AD配置
=====================

一、修改配置
--------------------------

打开OpsGrat和sso的settings.py文件，在最后面加入如下内容：
::
   import ldap
   AUTH_LDAP_CONNECTION_OPTIONS = {
       ldap.OPT_DEBUG_LEVEL: 1,
       ldap.OPT_REFERRALS: 0,
   }

二、ldap配置
-------------------------

打开sso，进入“系统设置”菜单下的“基本设置”

.. image:: ../_static/img/using/settings_ldap.png
