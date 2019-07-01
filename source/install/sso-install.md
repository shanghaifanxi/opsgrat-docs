# SSO手工安装文档

## 一、环境要求

*   python3.6
*   CentOS7（2Core*4G）
*   MySQL5.5+
*   Redis3.0+
*   RabbitMQ

## 二、部署路径和虚拟环境

*   本文中sso部署在/var/lib/sso/sso目录，可以根据公司规范要求进行修改
*   本文中python3.6虚拟环境为/var/lib/sso/venv目录

## 三、依赖包安装

```
yum install openldap openldap-devel
```

## 四、安装python3.6

1、安装EPEL和IUS软件源
```
yum install epel-release -y
yum install https://centos7.iuscommunity.org/ius-release.rpm -y
```

2、安装Python3.6
```
yum install python36u -y
yum install python36u-devel -y
```

3、创建python3连接符
```
ln -s /bin/python3.6 /bin/python3
```

4、安装pip3
```
yum install python36u-pip -y
```

5、创建pip3链接符
```
ln -s /bin/pip3.6 /bin/pip3
```

## 五、安装python3.6虚拟环境

1、安装virtualenv
```
pip install virtualenv
```

2、创建sso部署目录
```
mkdir -p /var/lib/sso
```

3、创建虚拟环境
```
 # 虚拟环境目录可以自行修改，修改虚拟环境目录后需要
virtualenv /var/lib/sso/venv -p python3
```

## 六、SSO安装步骤

1、将sso.tar.gz上传到 /var/lib/sso 目录下并解压

2、安装python依赖包
```
/var/lib/sso/venv/bin/pip install -r /var/lib/sso/sso/docs/requirements.txt
```

3、创建数据库，连接MySQL执行：
```
create database opsgrat_sso default charset utf8mb4;
```

4、导入数据库，连接MySQL，在MySQL命令行中执行：
```
use opsgrat_sso
source /var/lib/sso/sso/docs/sso.sql
```

5、修改/var/lib/sso/sso/sso/configs.py文件中的数据库配置，替换下文中数据库主机名、端口、用户名、密码和数据库名称
```
    DB_NAME = "opsgrat_sso" # sso数据库名
    DB_USER = "root"  # 用户名
    DB_PASSWORD = "root" # 密码
    DB_HOST = "127.0.0.1" # 主机名
    DB_PORT = "3306" # 端口
```

6、修改/var/lib/sso/sso/sso/configs.py文件中REDIS配置，替换下文中redis的主机名、端口和密码
```
    REDIS = {
        "HOST": "127.0.0.1", # redis主机名
        "PORT": 6379, # redis密码
        "PASSWORD": '' # 默认为空密码
    }
```

7、修改/var/lib/sso/sso/sso/configs.py文件中RABBIT_MQ配置，替换下文中rabbitmq的主机名、端口、用户名和密码
```
    RABBIT_MQ = {
        "HOST": "", # rabbitmq主机名
        "PORT": 5672, # 端口
        "USER": "guest", # 用户名
        "PASSWORD": 'guest', # 密码
    }
```

8、创建日志目录，默认日志文件目录为：/var/log/sso，可以根据规范要求修改
```
    mkdir -p /var/log/sso
```

9、修改/var/lib/sso/sso/sso/configs.py文件中日志目录

10、关闭debug模式，/var/lib/sso/sso/sso/configs.py文件中DEBUG值改成False

11、创建进程文件目录
```
    mkdir -p /var/run/sso
```

12、创建sso运行用户
```
    useradd sso
```

13、修改sso目录所属的用户和组
```
    chown sso.sso -R /var/lib/sso
    chown sso.sso /var/log/sso
    chown sso.sso /var/run/sso
```

## 七、uwsgi安装与配置

1、进入/var/lib/sso/sso目录，新建一个uwsgi.ini文件

2、编辑uwsgi.ini文件

3、命令：vim uwsgi.ini

4、在里面添加以下内容：
```
    [uwsgi]
    #必须填写
    #socket的端口号(要与nginx中的 uwsgi_pass配置一样)
    socket=:7501

    #sso系统的部署路径
    chdir = /var/lib/sso/sso

    #sso系统中的wsgi文件路径
    module = sso.wsgi

    # 启用主进程
    master = true

    #设置进程个数
    processes = 4
    chmod-socket = 664

    #自动移除nginx Socket和pid文件当服务停止的时候
    vacuum = true

    #（当前使用的python版本路径）
    pythonpath = /var/lib/sso/venv/bin/python
```

5、退出保存(:x)

6、设置用户组
```
chown sso.sso -R /var/lib/sso/sso/uwsgi.ini
```


## 八、安装supervisor

1、通过pip安装supervisor：
```
    pip install supervisor
```

2、创建依赖目录：
```
mkdir -p /etc/supervisor/conf.d
mkdir -p /var/log/supervisor
mkdir -p /var/run/supervisor
```

3、创建启动配置文件：
```
vim /etc/supervisor/supervisord.conf
```
添加如下内容：
```
    [supervisord]
    nodaemon = False
    childlogdir = /var/log/supervisor
    user = root
    pidfile = /var/run/supervisord.pid

    [unix_http_server]
    file = /var/run/supervisor.sock
    ;chown = root
    ;username = root
    ;password = my_password

    [supervisorctl]
    serverurl = unix:///var/run/supervisor.sock
    ;username = root
    ;password = my_secret_password

    [include]
    files = /etc/supervisor/conf.d/*.ini

    [rpcinterface:supervisor]
    supervisor.rpcinterface_factory = supervisor.rpcinterface:make_main_rpcinterface
```

4、创建service启动
```
vim /etc/systemd/system/supervisord.service
```
添加如下内容：
```
    # supervisord service for systemd
    # Originally by ET-CS (https://github.com/ET-CS)
    [Unit]
    Description=Supervisor daemon

    [Service]
    Type=forking
    ExecStart=/usr/bin/supervisord -c /etc/supervisor/supervisord.conf
    ExecStop=/usr/bin/supervisorctl $OPTIONS shutdown
    ExecReload=/usr/bin/supervisorctl $OPTIONS reload
    KillMode=process
    Restart=on-failure
    RestartSec=42s

    [Install]
    WantedBy=multi-user.target
```

5、启动supervisord
```
    systemctl start supervisord
```


## 九、配置sso supervisor方式启动

1、添加supervisor启动sso uwsgi配置文件，在/etc/supervisor/conf.d目录中新建sso-web.ini文件，添加如下内容：
```
    [program:sso-uwsgi]
    #用户名
    user=sso
    group=sso

    #命令执行路径
    command=/var/lib/sso/venv/bin/uwsgi --ini /var/lib/sso/sso/uwsgi.ini
    stopsignal=QUIT

    #设置自动开启
    autostart=true

    #设置自动重启
    autorestart=true

    #uwsgi运行日志路径
    stdout_logfile=/var/log/sso/access.log
    stderr_logfile=/var/log/sso/access_err.log
```

2、添加supervisor启动sso worker配置文件，在/etc/supervisor/conf.d目录中新建ssod.ini文件，添加如下内容：
```
    [program:sso-worker]
    user=sso
    group=sso
    stopasgroup=true
    command=/var/lib/sso/venv/bin/celery -A sso worker --loglevel=INFO --time-limit=86400 -Ofair --concurrency=2 -Q sso_job --logfile=/var/log/sso/sso-worker.log --pidfile=/var/run/sso/sso-worker.pid
    directory=/var/lib/sso/sso
    autostart=true
    # --concurrency=2为celery的进程数量
```

3、重新加载配置文件：
```
   supervisorctl reload
```
4、启动所有进程：
```
   supervisorctl restart all
```

5、执行supervisorctl命令进入shell 可以看到当前守护的进程名以及状态 可以对其使用start stop等命令


##  十、nginx安装并配置

   说明：部署的环境中若有nginx 则直接在/etc/nginx/conf.d目录中添加配置文件。若没有nginx则用yum安装或者通过wget命令下载二进制
   文件编译安装 。本方法是在环境中存在nginx的情况下进行配置的 。具体配置步骤如下：

1、命令：vim  /etc/nginx/conf.d/sso.conf  进入编辑文件

2、添加如下内容（其中server_name后的xx.xx.xx.xx需要替换成主机实际的ip或域名）：
```
   server {
               autoindex on;

               #此为nginx服务器的端口号  服务通过nginx与uwsgi通信来启动
               listen      80;

               #nginx代理的ip或域名
               server_name xx.xx.xx;

               #nginx编码为utf-8
               charset     utf-8;

               #最大上传文件为500M
               client_max_body_size 500M;
               location /static {
                              #sso系统静态文件路径
                             alias /var/lib/sso/sso/static;
               }
               location / {
                            #导入一个Nginx模块(uwsgi_params)它是用来和uWSGI进行通讯的
                           include     /etc/nginx/uwsgi_params;

                           # 指定其处理动态文件 7501为uwsgi进程端口
                           uwsgi_pass 127.0.0.1:7501;
               }
    }
```

3、退出保存(:x)

4、重新加载nginx文件命令：
```
   nginx -s reload
```

5、启动nginx命令为:
```
   systemctl start nginx
```

## 十一、配置sso

1、sso安装完成后在浏览器上访问sso，本文的地址为：http://xx.xx.xx.xx/ (根据实际配置修改ip和端口)
  - 管理用户为：admin
  - 初始密码为：admin

2、修改sso和opsgrat的访问地址：
  - 点击菜单管理-》子系统管理
  - 修改OpsGrat和sso的访问路径

