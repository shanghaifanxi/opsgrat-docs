# playbook安装

## 一、服务器环境要求

*   CentOS 7或Red Hat 7
*   python2.7
*   pip可以正常使用
*   已安装ansible2.7+
*   已安装sshpass
*   已安装MySQL客户端

## 二、服务器配置要求

*   Cpu 4Core
*   内存 8G

## 三、依赖中间件

1.   MySQL5.5+：部署OpsGrat前需要先提供MySQL数据库，并准备好可以创建数据库的用户
2.   Redis3.0+：OpsGrat执行ansible-playbook产生的中间日志先记录在Redis中因此需要提供可以访问的Redis
3.   RabbitMQ：OpsGrat使用RabbitMQ作为消息队列异步执行作业，所以部署前需要先准备好可以访问的RabbitMQ

## 四、OpsGrat和SSO使用python版本

*   python3.6

## 五、OpsGrat程序的组成

1.   sso：单点登录，包括用户管理、部门管理、角色管理、菜单管理等基础内容
2.   sso-worker：celery异步任务进程，用于从ldap同步用户信息
3.   opsgrat：OpsGrat系统，提供OpsGrat的api和web操作界面，只能单节点部署
4.   opsgrat-worker：celery异步任务进程，主要用于异步执行自动化作业和工作流，opsgrat-worker可以部署多个节点
5.   notification-worker：通知进程，用于通过邮件或钉钉通知用户自动化作业的执行结果，notification-worker可以部署多个节点
6.   opsgrat-beat：定时任务进程，用于生成计划任务交给opsgrat-worker执行，只能单节点部署和opsgrat web程序部署在同一台主机上即可

## 六、OpsGrat安装

### playbook一键安装

1、   修改hosts文件，将其中主机的ip地址替换成用户实际安装的主机的ip地址：

```
# 将其中ip地址替换即可，如果要增加worker节点则，在opsgratserver组中增加主机即可
[opsgratserver]
opsgrat ansible_ssh_host=10.4.20.13 ansible_ssh_user=root role=portal # portal节点只能设置一台(不能没有portal节点)，为opsgrat web管理系统地址
opsgrat2 ansible_ssh_host=10.4.20.14 ansible_ssh_user=root role=worker # worker节点可以设置多台

# 将其中ip地址替换成sso的ip地址
[ssoserver]
sso ansible_ssh_host=10.4.20.12 ansible_ssh_user=root 

# 如果未配置免密登录则需要在，增加ansible_ssh_pass参数指定主机登录密码
```

2、   修改group_vars/all文件中的配置，group_vars/all文件内容及其参数含义如下：

```
opsgrat_user: opsgrat # opsgrat和sso程序运行的用户
opsgrat_group: opsgrat # opsgrat和sso程序运行的组

install_dir: /opt/opsgrat # opsgrat和sso程序安装目录
log_dir: /var/log/opsgrat # opsgrat和sso程序日志目录
pid_dir: /var/run/opsgrat # opsgrat和sso程序进程id文件目录


mysql_opsgrat_host: 127.0.0.1 # opsgrat MySQL主机名
mysql_opsgrat_db: opsgrat # opsgrat MySQL数据库名
mysql_opsgrat_port: 3306 # opsgrat MySQL端口
mysql_opsgrat_user: opsgrat # opsgrat MySQL用户名
mysql_opsgrat_user_password: opsgrat # opsgrat MySQL密码

mysql_sso_host: 127.0.0.1 # sso MySQL主机名
mysql_sso_db: opsgrat_sso # sso MySQL数据库名
mysql_sso_port: 3306 # sso MySQL端口
mysql_sso_user: opsgrat # sso MySQL用户名
mysql_sso_user_password: opsgrat # sso MySQL密码

redis_host: 127.0.0.1 # opsgrat和sso redis主机名
redis_port: 6379 # opsgrat和sso redis端口
redis_passwd:  # opsgrat和sso redis密码

rabbitmq_host: 127.0.0.1 # opsgrat和sso的RabbitMQ主机名
rabbitmq_port: 5672 # opsgrat和sso的RabbitMQ端口
rabbitmq_user: guest # opsgrat和sso的RabbitMQ用户名
rabbitmq_passwd: guest # opsgrat和sso的RabbitMQ密码

opsgrat_uwsgi_port: 7500 # opsgrat uwsgi进程端口
sso_uwsgi_port: 7501 # sso uwsgi进程端口

opsgrat_nginx_port: 8080 # opsgrat nginx进程端口
sso_nginx_port: 8081 # sso nginx进程端口
```

3、   进入opsgrat-install目录执行命令一键安装，命令如下：

```
export ANSIBLE_HOST_KEY_CHECKING=false
ansible-playbook -i hosts main.yml 
```

## 七、初始化配置

### sso配置

1、   opsgrat安装完成后在浏览器上访问sso，本文的地址为：http://10.4.20.12:8081/ (根据实际配置修改ip和端口)  
  - 管理用户为：admin
  - 初始密码为：admin
2、   修改sso和opsgrat的访问地址：
  - 点击菜单管理-》子系统管理
  - 修改OpsGrat和sso的访问路径

## 八、导入License

1.   申请试用或者购买的时候会将License发送到填写的邮箱，先将License文件下载到本地
2.   进入opsgrat系统，由于首次安装还未导入License，系统会跳转到License导入页面，本地opsgrat地址为：http://10.4.20.12:8080/
3.   点击“导入”按钮，选择License文件后点击上传即可


