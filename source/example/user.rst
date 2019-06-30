
创建系统用户
==========================

一、创建user项目
--------------------------------

1、创建user文件夹

2、创建main.yml文件，并写入如下内容：
::

   ---
   # 创建用户

   - hosts: all
     tasks:  
      - name: Create group
        group:
          name: "{{ group_name }}"
          state: present

      - name: Create user
        user:
          name: "{{ user_name }}"
          groups: "{{ group_name }}"
          state: present

      - name: Create .ssh
        file:
          path: "/home/{{ user_name }}/.ssh"
          owner: "{{ user_name }}"
          group: "{{ group_name }}"
          mode: 0700
          state: directory
       
   
      - name: Deploy authorized_keys
        copy: 
          src: authorized_keys
          dest: "/home/{{ user_name }}/.ssh/authorized_keys"
          owner: "{{ user_name }}"
          group: "{{ group_name }}"
          mode: 0600


