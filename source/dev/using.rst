
API使用
================================

一、API认证
---------------------------

**认证方式：**
::
    OpsGrat系统API认证通过Token实现，使用方式为，在http的header里面增加Authorization，如下：
   
    Authorization: Token 0a529467ef243ee25cf2f7dea238eab7b6c82085
  
    0a529467ef243ee25cf2f7dea238eab7b6c82085 为用户的Token，替换成用户实际Token即可

**获取API Token：**
::

    1、登录OpsGrat系统，点击左侧上方用户头像下用户名，如下图所示：

.. image:: ../_static/img/dev/token_username.jpg

::

    2、然后点击弹出窗中的“API Token”按钮，如下图所示：

.. image:: ../_static/img/dev/token_list.jpg

::

    3、最后在弹出的“我的Token”模态框中可以看到登录用户的API Token，如下图：

.. image:: ../_static/img/dev/token.jpg

**使用例子：**
::

    以下例子为查询用户主机清单列表：

    curl -X GET http://127.0.0.1/api/project/inventory/ -H 'Authorization: Token 0a529467ef243ee25cf2f7dea238eab7b6c82085'

二、http请求方式说明
-------------------------------

- GET： 查询数据
- POST： 新增数据
- PUT： 修改数据
- PATCH： 修改数据（部分修改）
- DELETE： 删除数据

三、http返回状态码说明
---------------------------------

- 200：查询或修改成功
- 201：新增成功
- 400：数据验证错误
- 401：未认证
- 403：没有权限
- 405：http method不允许
- 5xx：服务端错误

四、Content-Type
------------------------

- application/x-www-form-urlencoded：类似表单方式提交数据
- application/json：使用json格式字符串提交数据

五、返回数据格式
--------------------------

**数据格式说明：**

- 返回的数据格式为json字符串
- 列表api中count表示总数，next为下一页请求地址，previous为上一页请求地址，results为查询到的数据列表
- 列表api通过offset和limit参数进行分页，offset表示数据开始位置，limit表示查询数量
- 列表api url地址后面跟上某条数据的id为获取该数据的信息

**列表api范例如下：**
::

   {
    "count": 16,
    "next": "http://127.0.0.1/api/project/host/?limit=2&offset=2",
    "previous": null,
    "results": [
        {
            "id": 29,
            "hostname": "host1",
            "inventory_name": "我的主机清单",
            "description": "",
            "status": 1,
            "variables": "",
            "inventory": 11
        },
        {
            "id": 28,
            "hostname": "host2",
            "inventory_name": "我的主机清单",
            "description": "",
            "status": 1,
            "variables": "",
            "inventory": 11
        }
    ]
   }

**单条数据api范例如下：**
::

   {
    "id": 29,
    "hostname": "host1",
    "inventory_name": "我的主机清单",
    "description": "",
    "status": 1,
    "variables": "",
    "inventory": 11
   }

六、数据新增成功说明
--------------------------------

数据新增成功返回的http状态码为201，返回的数据为新增数据的内容，类似如下内容：
::
   
   {
    "id": 29,
    "hostname": "host1",
    "inventory_name": "我的主机清单",
    "description": "",
    "status": 1,
    "variables": "",
    "inventory": 11
   }

七、数据验证错误说明
---------------------------------

数据验证错误返回的http状态码为400，返回的数据内容类似如下信息：
::

   {
    "detail": "xxxx错误"
   }
