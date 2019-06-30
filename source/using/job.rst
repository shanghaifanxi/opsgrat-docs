
自动化管理
=============================


一、作业管理
````````````````````````

::

    点击左侧菜单“自动化管理”下的“作业管理菜单”

.. image:: ../_static/img/using/job/zuoyeguanli.png

::

    点击上方的下拉框可以根据模板、主机清单、凭据等进行数据查询并返回数据结果

.. image:: ../_static/img/using/job/job_query_moban.png

.. image:: ../_static/img/using/job/job_query_qingdan.png

.. image:: ../_static/img/using/job/job_query_pingju.png

::

    点击操作框内的日志查看按钮

.. image:: ../_static/img/using/job/job_look_button.png

::

    跳转到该作业的日志页面、左边部分显示该作业的信息、右边部分显示日志信息

.. image:: ../_static/img/using/job/job_log.png

::

    点击操作框内的执行按钮

.. image:: ../_static/img/using/job/job_execute_button.png

::

    提示确认信息，确认后执行命令,跳转到该作业的日志页面

.. image:: ../_static/img/using/job/job_confirm_button.png

.. image:: ../_static/img/using/job/job_runing_log.png

::

    点击操作框内的删除按钮，可以删除当前行数据

.. image:: ../_static/img/using/job/job_delete_button.png

::

    提示确认信息，确认后进行数据删除

.. image:: ../_static/img/using/job/job_delete_confirm.png

.. image:: ../_static/img/using/job/job_delete_result.png

::

    点击右上角的列显示状态按钮下拉菜单，并点击要隐藏或者展示的列来获取相应列的信息

.. image:: ../_static/img/using/job/job_column_button.png

.. image:: ../_static/img/using/job/job_column_display.png


::

    选择一个模板的作业类型为工作流的作业，点击执行按钮，跳转到工作流图形页面
    展示该工作流模板的流程图下的各个节点运行状态，可以根据右侧的状态信息进行了解


.. image:: ../_static/img/using/job/job_chart.png


::

    在展示的流程图形页面可以点击节点上的查看按钮，会跳转到该节点下的模板任务执行情况


.. image:: ../_static/img/using/job/job_chart_button.png

.. image:: ../_static/img/using/job/job_chart_node.png

::

    模板类型为工作流的模板可以点击前面的加号，会展示出该ID下的子作业数据

.. image:: ../_static/img/using/job/job_workflow_plus.png

.. image:: ../_static/img/using/job/job_workflow_information.png

::

    同时可以对子作业进行执行、查看、删除等操作，功能与前面所介绍的类似

::

    说明：1、当作业类型为自动化作业或者命令，点击执行按钮跳转到作业日志页面
          2、当作业类型为工作流，点击执行按钮跳转到工作流程图形页面
          对应页面如下如：

.. image:: ../_static/img/using/job/job_job_execute.png

.. image:: ../_static/img/using/job/job_log.png

.. image:: ../_static/img/using/job/job_workflow_execute.png

.. image:: ../_static/img/using/job/job_chart.png



二、批量命令
````````````````````````

::

    点击左侧菜单“自动化管理”下的“批量命令菜单”

.. image:: ../_static/img/using/job/piliang.png

::

    添加相应的数据(像模块、登录凭据(ssh)、主机清单等下拉框值均要在相应的页面进行新增数据才可显示)具体情况如下图：

::

    点击左侧菜单“系统管理”下的“模块管理”、在此页面进行新增需要的模块

.. image:: ../_static/img/using/job/job_system_model.png

.. image:: ../_static/img/using/job/job_batch_model.png

::

    点击左侧菜单“资源管理”下的“凭据管理”、在此页面进行新增需要的凭据

.. image:: ../_static/img/using/job/job_project_ssh.png

.. image:: ../_static/img/using/job/job_batch_ssh.png

::

    点击左侧菜单“资源管理”下的“主机清单”、在此页面进行新增需要的主机清单

.. image:: ../_static/img/using/job/job_project_inventory.png

.. image:: ../_static/img/using/job/job_batch_inventory.png

::

    最后添加数据，并点击左上角的执行命令按钮

.. image:: ../_static/img/using/job/job_batch_button.png

.. image:: ../_static/img/using/job/job_batch_add.png

::

    该批量命令会跳转到该任务的日志页面，展示该批量命令运行的信息

.. image:: ../_static/img/using/job/job_batch_log.png


三、作业执行
````````````````````````

::

   点击左侧菜单“自动化管理”下的“作业执行菜单”

.. image:: ../_static/img/using/job/job_execute.png

::

   填写或选择相应的数据（像主机清单、登录凭据(ssh)上面以作叙述，这里不再介绍）
   这里介绍如何获取tags和skip_tags、点击左侧菜单“系统管理”下的“Tag管理菜单”

.. image:: ../_static/img/using/job/job_system_tag.png

.. image:: ../_static/img/using/job/job_tags.png

::

   最后填写具体数据，并点击左上角的执行按钮

.. image:: ../_static/img/using/job/job_job_execute_button.png

::

   该作业会跳转到相应的日志页面，并展示该作业运行的具体信息以及日志信息

.. image:: ../_static/img/using/job/job_job_execute_log.png


四、计划任务
````````````````````````

::

   点击左侧菜单“自动化管理”下的“计划任务菜单”

.. image:: ../_static/img/using/job/job_schedule.png

::

   点击页面上的新增按钮,执行方式为计划任务

.. image:: ../_static/img/using/job/job_schedule_add.png

::

   点击新增按钮,执行方式为固定间隔

.. image:: ../_static/img/using/job/job_schedule_add2.png

::

   点击新增按钮,执行方式为特定时间

.. image:: ../_static/img/using/job/job_schedule_add3.png

.. image:: ../_static/img/using/job/job_schedules.png

::

   点击上方的搜索框可以根据模板以及任务名称进行数据查询和返回查询结果

.. image:: ../_static/img/using/job/job_query_model.png

.. image:: ../_static/img/using/job/job_query_name.png

::

   点击操作框内的修改按钮，可以修改当行数据

.. image:: ../_static/img/using/job/job_schedule_update.png

.. image:: ../_static/img/using/job/job_schedule_update_button.png

::

   点击操作框内的权限管理按钮，可以增加相应的权限

.. image:: ../_static/img/using/job/job_schedule_authority.png

::

  点击权限管理按钮后进入用户权限设置以及团队权限设置两个页卡、在两个页面均可以新增、修改、查询、删除等操作，这些功能与前面一样不再赘述

.. image:: ../_static/img/using/job/job_schedule_user.png

.. image:: ../_static/img/using/job/job_schedule_team.png








