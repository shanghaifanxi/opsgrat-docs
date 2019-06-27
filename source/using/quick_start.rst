
快速入门
=======================

说明
````````````
- 通过例子引导OpsGrat的配置和使用

一、SSO设置
````````````````````

**1.1 子系统设置**
--------------------

.. code-block:: vim

    先设置SSO，实现基础配置，再管理设备
    首先，进入SSO

.. image:: ../_static/img/using/sso.png

.. code-block:: vim

    点击页面左侧菜单栏中“菜单管理”下的“子系统管理”进入子系统管理页面
    修改OpsGrat和SSO的路径，改成实际的访问路径

.. image:: ../_static/img/using/navigation.png

**1.2 ldap设置**
--------------------

.. code-block:: vim

    如果不使用ldap认证可以跳过该步骤
    
.. image:: ../_static/img/using/settings_ldap.png

**1.3 添加用户**
--------------------

.. code-block:: vim

    点击“用户管理”下的“用户管理”菜单，进入用户管理页面。
    如果配置了ldap则在“新增”按钮后面会有一个“AD”按钮，如下图。点击“AD”按钮会从ldap获取用户
    如果没有配置ldap则需要手工为自己添加用户，是否管理员设置为“是”
    然后使用新的用户重新登录SSO

.. image:: ../_static/img/using/sso_user.png

::

    点击“新增”按钮，新增一个deploy用户

.. image:: ../_static/img/using/add.png

::

    退出登录，使用deploy用户进行操作

.. image:: ../_static/img/using/in.png

二、资源管理
````````````````````

**2.1 添加ssh登录凭据**
-----------------------------

::

    点击右上方“OpsGrat”导航栏，跳转到OpsGrat系统
    点击左侧菜单“资源管理”下的“凭据管理”菜单

.. image:: ../_static/img/using/pingju.png

::

    点击“新增”按钮，新增凭据类型为ssh的凭据

.. image:: ../_static/img/using/ssh_pj.png

**2.2 添加git的凭据**
---------------------------

::

    点击“新增”按钮，新增凭据类型为“用户名和密码”的git凭据

.. image:: ../_static/img/using/git_yhm.png

**2.3 添加项目**
--------------------------

::

    点击左侧菜单“资源管理”下的“项目管理”菜单

.. image:: ../_static/img/using/management.png

::

    点击“新增”按钮，新增凭据类型为git项目的凭据

.. image:: ../_static/img/using/git_xm.png

**2.4 添加主机清单**
---------------------------

::

    点击左侧菜单“资源管理”下的“主机清单”菜单

.. image:: ../_static/img/using/inventory.png

::

    点击“新增”按钮，添加主机清单
    主机清单内容可直接填写ip地址

.. image:: ../_static/img/using/inventory_add.png

三、通知管理
````````````````````

**3.1 添加邮件设置**
---------------------------

::

    点击左侧菜单“通知管理”下的“渠道设置”菜单，点击邮件设置

.. image:: ../_static/img/using/channel_email.png

::

    点击“新增”按钮，新增邮件

.. image:: ../_static/img/using/channel_email_add.png

**3.2 添加通知设置**
---------------------------

::

    点击左侧菜单“通知管理”下的“通知设置”菜单

.. image:: ../_static/img/using/notification.png

::

    点击“新增”按钮，选择类型为邮件的渠道

.. image:: ../_static/img/using/notification_add.jpg

四、模板管理
``````````````````````````

**4.1 添加作业模板**
-------------------------

::

    点击左侧菜单“模板管理”下的“作业模板”菜单

.. image:: ../_static/img/using/template.png

::

    点击“新增”按钮，添加作业模板

.. image:: ../_static/img/using/template_addupdate.png


**4.2 执行作业模板**
---------------------------

::

    点击通知设置图标，进入通知设置

.. image:: ../_static/img/using/template_sz.png

.. image:: ../_static/img/using/templatetzsz.png

::

    点击新增，选择通知方式

.. image:: ../_static/img/using/method_to.png

::

    点击执行图标，执行作业模板

.. image:: ../_static/img/using/template_hj2.png


五、自动化管理
````````````````````

**5.1 批量命令执行**
--------------------------

::

    点击左侧菜单“自动化管理”下的“批量命令”菜单，填写数据后，点击“执行命令”按钮

.. image:: ../_static/img/using/process.png

::

    批量执行

.. image:: ../_static/img/using/process_zx.png

**5.2 查看作业日志**
-------------------------

::

    点击左侧菜单“自动化管理”下的“作业管理”菜单，点击“查看日志”图标，查看作业日志

.. image:: ../_static/img/using/job.png

::

    作业日志：

.. image:: ../_static/img/using/job_zy.png


**5.3 设置计划任务**
--------------------------

::

    点击左侧菜单“自动化管理”下的“计划任务”菜单

.. image:: ../_static/img/using/schedule.png

::

    点击“新增”按钮，设置计划任务

.. image:: ../_static/img/using/schedule_add.png

    
