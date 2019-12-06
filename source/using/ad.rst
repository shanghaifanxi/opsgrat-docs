AD配置
=====================

打开sso，进入“系统设置”菜单下的“基本设置”

.. image:: ../_static/img/using/settings_ldap.png

::
   
   LDAP类型：可选值有Windows AD域和OpenLDAP
   LDAP 地址：LDAP的访问地址，例如：ldap://10.0.1.1:389
   绑定DN：为提供给SSO系统使用的LDAP管理账号DN
   密码：为上述管理账号的密码
   用户OU：为允许登录SSO的用户部门OU，可以换行填入多个OU
   用户过滤器：为查询用户的查询语句
   状态：如果状态设置为禁用则系统将不会使用LDAP认证
