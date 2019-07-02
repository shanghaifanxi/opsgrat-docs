
作业日志
=======================

说明
---------------------------------------------------------------------------------------------
- 管理作业管理中的作业信息，用户可以查看曾经执行过计划的执行内容

1、作业日志列表、新增作业日志、批量删除作业日志 API
-----------------------------------------------------------------------------------

**请求方式：**    GET（查询） POST（新增） DELETE（批量删除）


**请求地址：**    /api/job/log/


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
| job                    | int        | 否         | job id                                         |
+------------------------+------------+------------+------------------------------------------------+


**输入参数（新增）：**

+------------------------+------------+------------+------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**|**说明**                                        |
+------------------------+------------+------------+------------------------------------------------+
| job                    | int        | 是         | job id                                         |
+------------------------+------------+------------+------------------------------------------------+
| ctime                  | long       | 是         | 创建时间                                       |
+------------------------+------------+------------+------------------------------------------------+
| log                    | string     | 是         | 日志内容                                       |
+------------------------+------------+------------+------------------------------------------------+

**输出参数：**

+------------------------+------------+------------+------------------------------------------------+
|**参数**                |**数据类型**|**是否必须**|**说明**                                        |
+------------------------+------------+------------+------------------------------------------------+
| id                     | int        | 是         | 作业日志 id                                    |
+------------------------+------------+------------+------------------------------------------------+
| job                    | int        | 是         | job id                                         |
+------------------------+------------+------------+------------------------------------------------+
| ctime                  | long       | 是         | 创建时间                                       |
+------------------------+------------+------------+------------------------------------------------+
| log                    | string     | 是         | 日志内容                                       |
+------------------------+------------+------------+------------------------------------------------+

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
                "id": 1688,
                "ctime": 1561705740,
                "log": "\n\n/usr/bin/ansible-playbook -i /tmp/auto_job_1718/tmpos_mosmk -u root --ask-pass main.yml\n\nSSH password: \r\nERROR! Syntax Error while loading YAML.\r\n  mapping values are not allowed in this context\r\n\r\nThe error appears to have been in '/tmp/auto_job_1718/project/roles/tomcat/tasks/main.yml': line 8, column 10, but may\r\nbe elsewhere in the file depending on the exact syntax problem.\r\n\r\nThe offending line appears to be:\r\n\r\n- name:Extract archive jdk\r\n  command: /bin/tar xf /tmp/jdk-8u211-linux-x64.gz -C /application\r\n         ^ here\r\n",
                "job": 1718
            },
            {
                "id": 1687,
                "ctime": 1561698849,
                "log": "\n\n/usr/bin/ansible-playbook -i /tmp/auto_job_1717/tmp7xwu64mp -u root --ask-pass main.yml\n\nSSH password: \r\nERROR! Syntax Error while loading YAML.\r\n  mapping values are not allowed in this context\r\n\r\nThe error appears to have been in '/tmp/auto_job_1717/project/roles/tomcat/tasks/main.yml': line 8, column 10, but may\r\nbe elsewhere in the file depending on the exact syntax problem.\r\n\r\nThe offending line appears to be:\r\n\r\n- name:Extract archive jdk\r\n  command: /bin/tar xf /tmp/jdk-8u211-linux-x64.gz -C /application\r\n         ^ here\r\n",
                "job": 1717
            },
            {
                "id": 1686,
                "ctime": 1561689957,
                "log": "\n\n/usr/bin/ansible-playbook -i /tmp/auto_job_1716/tmp4fxky1_f -u root --ask-pass main.yml\n\nSSH password: \r\nERROR! Syntax Error while loading YAML.\r\n  mapping values are not allowed in this context\r\n\r\nThe error appears to have been in '/tmp/auto_job_1716/project/roles/tomcat/tasks/main.yml': line 8, column 10, but may\r\nbe elsewhere in the file depending on the exact syntax problem.\r\n\r\nThe offending line appears to be:\r\n\r\n- name:Extract archive jdk\r\n  command: /bin/tar xf /tmp/jdk-8u211-linux-x64.gz -C /application\r\n         ^ here\r\n",
                "job": 1716
            },
            {
                "id": 1685,
                "ctime": 1561688924,
                "log": "\n\n/usr/bin/ansible-playbook -i /tmp/auto_job_1715/tmp76x4cjpx -u root --ask-pass main.yml\n\nSSH password: \r\nERROR! Syntax Error while loading YAML.\r\n  mapping values are not allowed in this context\r\n\r\nThe error appears to have been in '/tmp/auto_job_1715/project/roles/tomcat/tasks/main.yml': line 8, column 10, but may\r\nbe elsewhere in the file depending on the exact syntax problem.\r\n\r\nThe offending line appears to be:\r\n\r\n- name:Extract archive jdk\r\n  command: /bin/tar xf /tmp/jdk-8u211-linux-x64.gz -C /application\r\n         ^ here\r\n",
                "job": 1715
            }
        ]
    }

**新增作业日志返回数据例子：**
::

    {
        "id": 1685,
        "ctime": 1561688924,
        "log": "\n\n/usr/bin/ansible-playbook -i /tmp/auto_job_1715/tmp76x4cjpx -u root --ask-pass main.yml\n\nSSH password: \r\nERROR! Syntax Error while loading YAML.\r\n  mapping values are not allowed in this context\r\n\r\nThe error appears to have been in '/tmp/auto_job_1715/project/roles/tomcat/tasks/main.yml': line 8, column 10, but may\r\nbe elsewhere in the file depending on the exact syntax problem.\r\n\r\nThe offending line appears to be:\r\n\r\n- name:Extract archive jdk\r\n  command: /bin/tar xf /tmp/jdk-8u211-linux-x64.gz -C /application\r\n         ^ here\r\n",
        "job": 1715
    }


2、获取单个作业日志，修改作业日志、删除作业日志 API
-----------------------------------------------------------------------------------------------------------------

**请求方式：**    GET（查询） PUT（修改） PATCH（修改） DELETE（删除）

**请求地址：**    /api/job/log/1685/
::

    请求地址中1685为作业日志的id


**输入/输出参数：**   见章节1中输入和输出参数说明，修改数据时输入参数均为非必须

**返回数据例子：**
::

    {
        "id": 1685,
        "ctime": 1561688924,
        "log": "\n\n/usr/bin/ansible-playbook -i /tmp/auto_job_1715/tmp76x4cjpx -u root --ask-pass main.yml\n\nSSH password: \r\nERROR! Syntax Error while loading YAML.\r\n  mapping values are not allowed in this context\r\n\r\nThe error appears to have been in '/tmp/auto_job_1715/project/roles/tomcat/tasks/main.yml': line 8, column 10, but may\r\nbe elsewhere in the file depending on the exact syntax problem.\r\n\r\nThe offending line appears to be:\r\n\r\n- name:Extract archive jdk\r\n  command: /bin/tar xf /tmp/jdk-8u211-linux-x64.gz -C /application\r\n         ^ here\r\n",
        "job": 1715
    }
