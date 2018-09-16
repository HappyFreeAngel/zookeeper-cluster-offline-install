
git submodule常用命令

#项目子模块批量从远程仓库更新到本地
git submodule foreach git pull origin master
或
git submodule update --recursive
或
git pull --recurse-submodules


=========
添加子模块 从远程仓库ssh://git@git.ascs.tech/caoi/dns-resolve.git 克隆代码到当面目录下的 tasks/roles/dns-resolve
git submodule add ssh://git@git.ascs.tech/caoi/dns-resolve.git tasks/roles/dns-resolve
#####添加子模块后运行git status, 可以看到目录有增加1个文件.gitmodules, 这个文件用来保存子模块的信息。

查看子模块
git submodule

 -e33f854d3f51f5ebd771a68da05ad0371a3c0570 assets
子模块前面有一个-，说明子模块文件还未检入（空文件夹）。

更新项目内子模块到最新版本
git submodule update

更新子模块为远程项目的最新版本
git submodule update --remote


####git 递归克隆仓库及其子模块  (在后面添加--recursive）
git clone ssh://git@git.ascs.tech/~linyingjie/hadoopcluster-offline-install.git --recursive



修改子模块
在子模块中修改文件后，直接提交到远程项目分支。

$ git add .
$ git ci -m "commit"
$ git push origin HEAD:master
删除子模块
删除子模块比较麻烦，需要手动删除相关的文件，否则在添加子模块时有可能出现错误
同样以删除assets文件夹为例
       删除子模块文件夹
       * $ git rm --cached assets
        $ rm -rf assets
        删除.gitmodules文件中相关子模块信息
        [submodule "assets"]
          path = assets
          url = https://github.com/maonx/vimwiki-assets.git
        删除.git/config中的相关子模块信息
        [submodule "assets"]
          url = https://github.com/maonx/vimwiki-assets.git
        删除.git文件夹中的相关子模块文件
        $ rm -rf .git/modules/assets
        
Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
