
模板管理
=============================

一、作业模板
````````````````````````

::

    点击左侧菜单“模板管理”下的“作业模板菜单”

.. image:: ../_static/img/using/template/1.png

::

    点击新增按钮，跳转到新增页面，并添加相应的数据(像此页面的主机清单、自动化管理、登录凭据(ssh)、tags等下拉框的值均来自于相应页面的新增数据后才可显示选择，前面章节以作相应的介绍，这里不再赘述)，点击保存

.. image:: ../_static/img/using/template/2.png

::

    点击保存后，跳转到作业模板页面、同时可以点击上方下拉框进行主机清单、凭据、自动化项目等数据查询并返回查询结果、返回结果分别如下图：

.. image:: ../_static/img/using/template/3.png

.. image:: ../_static/img/using/template/5.png

.. image:: ../_static/img/using/template/6.png

::

    点击操作框内的执行按钮，跳转到该作业模板的日志页面，显示作业信息和作业日志

.. image:: ../_static/img/using/template/7.png

::

    点击操作框内的通知按钮，跳转到该作业模板的通知设置页面

.. image:: ../_static/img/using/template/8.png

::

    点击新增按钮按钮，添加相应数据并提交保存(新增时的通知字段下拉框值来自于通知管理--通知设置，要提前新增数据才可显示)，具体步骤如下图：

.. image:: ../_static/img/using/template/template_notification_settings.png

.. image:: ../_static/img/using/template/template_notification_add.png

::

    点击修改按钮，修改相应的数据，点击删除按钮，可以删除当前行数据、具体如下图：


.. image:: ../_static/img/using/template/template_notification_update.png

.. image:: ../_static/img/using/template/template_notification_delete.png

.. image:: ../_static/img/using/template/template_notification_result.png


::

    返回作业模板页面，点击修改按钮

.. image:: ../_static/img/using/template/template_update_button.png

::

    进入修改页面，修改相应的数据，点击修改即可保存

.. image:: ../_static/img/using/template/template_update.png

::

    返回作业模板页面，点击权限按钮,进行权限设置，跳转到授权用户和授权团队的两个页卡页面

.. image:: ../_static/img/using/template/template_authority_button.png

.. image:: ../_static/img/using/template/template_user_team.png

::

    在授权用户页面若当前用户没有被超级管理员授权，则不可以在此页面进行新增，修改，删除等操作、具体情况如下图：

.. image:: ../_static/img/using/template/template_user_test.png

::

    点击新增按钮填入相应数据，点击提交按钮，此时弹出没有权限执行操作

.. image:: ../_static/img/using/template/template_none_authority.png

::

    点击新修改按钮修改相应数据，点击提交按钮，此时弹出没有权限执行操作

.. image:: ../_static/img/using/template/template_update_none.png

::

    点击删除按钮删除当前行数据，点击确认后，此时弹出没有权限执行操作

.. image:: ../_static/img/using/template/template_delete_none.png

::

    若当前用户被超级管理员授予管理权限，则可以执行新增、修改、删除等操作

.. image:: ../_static/img/using/template/template_user_empower.png

::

    执行新增操作（新增时的用户下拉框的值来自于sso系统配置的用户）

.. image:: ../_static/img/using/template/template_user_empower_add.png

.. image:: ../_static/img/using/template/template_user_empower_result.png

::

    执行修改、删除等操作与新增一样，这里不再介绍、从以上可以看出每个用户有着不同的权限，其中超级管理员的权限最大，然而每种权限也有着不同的执行能力，其中包括：只读、执行、执行与读写、管理这四种权限类型


::

    点击授权团队页卡按钮，进入到团队权限页面

.. image:: ../_static/img/using/template/template_team_button.png

::

    点击新增按钮，填入相应的数据（其中的团队名称下拉框值来自于系统管理--团队管理所新增的团队名称）

.. image:: ../_static/img/using/template/template_team_add.png

.. image:: ../_static/img/using/template/template_team_add_result.png

::

    同时可以修改和删除相应的数据

.. image:: ../_static/img/using/template/template_team_update.png

.. image:: ../_static/img/using/template/template_team_update_result.png

.. image:: ../_static/img/using/template/template_team_delete.png

.. image:: ../_static/img/using/template/template_team_delete_result.png

二、工作流模板
````````````````````````

::

    点击左侧菜单“模板管理”下的“工作流模板菜单”

.. image:: ../_static/img/using/template/template_workflow.png

::

    点击新增按钮，填入相应数据

.. image:: ../_static/img/using/template/template_workflow_add.png

::

    点击操作框内的流程设计按钮，进入流程设计页面、在此页面移动鼠标至右上角将开始节点和处理节点拖拽到左侧的放置区域内，同时可以将节点之间进行连接

.. image:: ../_static/img/using/template/template_editflow.png

::

    对于连线有以下几点说明：
    1、从开始节点开始进行连线，可以同时连接几个处理节点
    2，节点之间只能进行一次连线（即每个处理节点只能执行一次）
    3，最后的处理节点不可连接开始节点，否则会出现死循环

::

    点击连线之间的修改按钮，可以对节点之间的状态进行设置

.. image:: ../_static/img/using/template/template_workflow_line_settings.png

::

    对于连线状态之间设置说明：1、当设置为成功或失败时，此时无论前一个节点的状态如何都会去执行下一个节点 2、当设置为成功时，此时前一个节点状态若为成功则执行下一个节点，若前一个节点为失败则不会执行下一个节点 3、当设置成失败时，此时前一个节点状态若为失败则会执行下一个节点，同理若前一个节点状态为成功则不会执行下一个节点

::

    点击节点上的修改按钮，可以编辑该节点以及点击节点上的删除按钮可以删除相关节点

.. image:: ../_static/img/using/template/template_workflow_node.png

.. image:: ../_static/img/using/template/template_workflow_node_update.png

::

    返回工作流模板页面，点击通知设置按钮

.. image:: ../_static/img/using/template/template_workflow_notification_button.png

::

    进入到该工作流的通知设置页面，可以对其进行通知设置，在此页面可以进行新增、修改、删除等操作，此步骤在前面的（模板管理--作业模板中的通知设置一样，这里不再赘述）

::

   对于通知设置的作用这里简单介绍一下：目前支持钉钉，邮件，企业微信这三种通知类型，设置不同的类型，当模板执行成功或者失败的时候会根据设定的通知对你进行消息通知

::

   点击操作框内的执行按钮，可以执行该工作流，并跳转到流程图页面，展示相关信息

.. image:: ../_static/img/using/template/template_workflow_execute.png

.. image:: ../_static/img/using/template/template_workflow_result.png


::

   同时可以点击节点上的查看按钮，跳转到该节点模板的执行状态页面

.. image:: ../_static/img/using/template/template_workflow_look.png

.. image:: ../_static/img/using/template/template_workflow_look_log.png

::

   同时可以修改以及删除相关的数据，与前面的修改和删除一样，这里不做赘述

::

   返回工作流模板页面，点击右上角的列状态下拉菜单，可以对相应的列进行显示或者隐藏

.. image:: ../_static/img/using/template/template_workflow_column.png

.. image:: ../_static/img/using/template/template_workflow_column_result.png


