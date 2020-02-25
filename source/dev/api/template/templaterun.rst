
执行模板管理
=======================

说明
-----------------------
- 管理执行模板

1、执行模板列表、新增执行模板、批量删除执行模板 API
----------------------------------------------------------

**请求方式：**    GET（查询） POST（新增） DELETE（批量删除）


**请求地址：**    /api/template/template/run/


**Content-Type：**
::
    新增数据的时候需要指定Content-Type，以下对Content-Type进行说明:

    application/x-www-form-urlencoded —— 表示通过表单方式提交
    application/json —— 表示传入数据为json格式字符串


**查询参数：**

+------------------------+------------+------------+------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**|**说明**                                        |
+------------------------+------------+------------+------------------------------------------------+
| offset                 | int        | 否         | 数据起始位置                                   |
+------------------------+------------+------------+------------------------------------------------+
| limit                  | int        | 否         | 查询条数                                       |
+------------------------+------------+------------+------------------------------------------------+
| name                   | string     | 否         | 主机清单分组名称                               |
+------------------------+------------+------------+------------------------------------------------+



**输入参数（新增）：**

+------------------------+------------+------------+------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**|**说明**                                        |
+------------------------+------------+------------+------------------------------------------------+
| id                     | int        | 否         | 模板id，与模板名称必须输入一个                 |
+------------------------+------------+------------+------------------------------------------------+
| name                   | string     | 否         |  模板名称，与模板id必须输入一个                |
+------------------------+------------+------------+------------------------------------------------+
| variables              | string     | 否         |  外部参数，会覆盖工作流中所有节的外部参数      |
+------------------------+------------+------------+------------------------------------------------+
| inventory_str          | string     | 否         |  主机清单内容，会覆盖工作流所有节点主机清单    |
+------------------------+------------+------------+------------------------------------------------+
| node                   | int        | 否         |  开始执行节点，默认从开始节点往下执行          |
+------------------------+------------+------------+------------------------------------------------+


**输出参数：**


    详细返回字段见job api：/api/job/job/

http method:

    get —— 模板列表
    post —— 执行模板



**批量删除参数：**

+------------------------+------------+-------------------+-------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**       |**说明**                                         |
+------------------------+------------+-------------------+-------------------------------------------------+
| pk                     | string     | 与pk[]不能都为空  | 主键，多个主键用半角逗号隔开。通过http body传入 |
+------------------------+------------+-------------------+-------------------------------------------------+
| pk[]                   | array      | 与pk不能都为空    | 主键数组。通过http body传入                     |
+------------------------+------------+-------------------+-------------------------------------------------+

**排序：**

+------------------------+------------+-------------------+---------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**       |**说明**                                           |
+------------------------+------------+-------------------+---------------------------------------------------+
|                        |            |                   |   一般默认按id倒叙                                |
| ordering               | string     | 否                | - ordering=id表示按id排序ordering=-id表示按id倒叙 |
|                        |            |                   | - 多个字段排序用半角逗号分隔                      |
+------------------------+------------+-------------------+---------------------------------------------------+

**GET返回数据例子：**
::
    {
        "count": 9,
        "next": null,
        "previous": null,
        "results": [
            {
                "id": 31,
                "description": "",
                "template_type": "job",
                "job_type": "run",
                "playbook": "site.yml",
                "credential": 29,
                "inventory": 18,
                "inventory_name": "阿里云主机",
                "project_name": "tomcat playbook",
                "project": 17,
                "forks": 0,
                "limit": "",
                "verbosity": 0,
                "become_enabled": 0,
                "variables": "tomcat_version: 8.5.42\r\n\r\n# Here are variables related to the Tomcat installation\r\n\r\nhttp_port: 8080\r\nhttps_port: 8443\r\n\r\n# This will configure a default manager-gui user:\r\n\r\nadmin_username: admin\r\nadmin_password: admin\r\n\r\ntomcat_downloadURL: http://mirror.bit.edu.cn/apache",
                "credential_name": "泛汐服务器（root用户名密码）",
                "name": "tomcat安装",
                "diff_mode": 0,
                "force_handlers": 0,
                "start_at_task": "",
                "tags": "",
                "skip_tags": "",
                "jobtype_name": "Run",
                "verbosity_name": "Normal",
                "cuser": 48,
                "bind_templates": [],
                "is_bind_templates": "否"
            },
            {
                "id": 30,
                "description": "",
                "template_type": "job",
                "job_type": "run",
                "playbook": "main.yml",
                "credential": 29,
                "inventory": 9,
                "inventory_name": "百度云和腾讯云主机",
                "project_name": "修改密码",
                "project": 8,
                "forks": 0,
                "limit": "",
                "verbosity": 0,
                "become_enabled": 0,
                "variables": "",
                "credential_name": "泛汐服务器（root用户名密码）",
                "name": "修改密码模板",
                "diff_mode": 0,
                "force_handlers": 0,
                "start_at_task": "",
                "tags": "",
                "skip_tags": "",
                "jobtype_name": "Run",
                "verbosity_name": "Normal",
                "cuser": 48,
                "bind_templates": [],
                "is_bind_templates": "否"
            }
        ]
    }

**新增执行模板返回数据例子：**
::
    {
        "id": 31,
        "description": "",
        "template_type": "job",
        "job_type": "run",
        "playbook": "site.yml",
        "credential": 29,
        "inventory": 18,
        "inventory_name": "阿里云主机",
        "project_name": "tomcat playbook",
        "project": 17,
        "forks": 0,
        "limit": "",
        "verbosity": 0,
        "become_enabled": 0,
        "variables": "tomcat_version: 8.5.42\r\n\r\n# Here are variables related to the Tomcat installation\r\n\r\nhttp_port: 8080\r\nhttps_port: 8443\r\n\r\n# This will configure a default manager-gui user:\r\n\r\nadmin_username: admin\r\nadmin_password: admin\r\n\r\ntomcat_downloadURL: http://mirror.bit.edu.cn/apache",
        "credential_name": "泛汐服务器（root用户名密码）",
        "name": "tomcat安装",
        "diff_mode": 0,
        "force_handlers": 0,
        "start_at_task": "",
        "tags": "",
        "skip_tags": "",
        "jobtype_name": "Run",
        "verbosity_name": "Normal",
        "cuser": 48,
        "bind_templates": [],
        "is_bind_templates": "否"
    }


2、获取单个执行模板，修改执行模板、删除执行模板 API
---------------------------------------------------------

**请求方式：**    GET（查询） PUT（修改） PATCH（修改） DELETE（删除）

**请求地址：**    /api/template/template/run/31/
::

    请求地址中31为执行模板的id


**输入/输出参数：**   见章节1中输入和输出参数说明，修改数据时输入参数均为非必须

**返回数据例子：**
::
{
        "id": 31,
        "description": "",
        "template_type": "job",
        "job_type": "run",
        "playbook": "site.yml",
        "credential": 29,
        "inventory": 18,
        "inventory_name": "阿里云主机",
        "project_name": "tomcat playbook",
        "project": 17,
        "forks": 0,
        "limit": "",
        "verbosity": 0,
        "become_enabled": 0,
        "variables": "tomcat_version: 8.5.42\r\n\r\n# Here are variables related to the Tomcat installation\r\n\r\nhttp_port: 8080\r\nhttps_port: 8443\r\n\r\n# This will configure a default manager-gui user:\r\n\r\nadmin_username: admin\r\nadmin_password: admin\r\n\r\ntomcat_downloadURL: http://mirror.bit.edu.cn/apache",
        "credential_name": "泛汐服务器（root用户名密码）",
        "name": "tomcat安装",
        "diff_mode": 0,
        "force_handlers": 0,
        "start_at_task": "",
        "tags": "",
        "skip_tags": "",
        "jobtype_name": "Run",
        "verbosity_name": "Normal",
        "cuser": 48,
        "bind_templates": [],
        "is_bind_templates": "否"
    }
