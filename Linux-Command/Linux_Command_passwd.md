# Linux Command passwd、gpasswd
tags: 用户管理

@[toc]

---

## 1. passwd
Linux passwd命令用来更改使用者的密码

```bash
-d 删除密码
-f 强制执行
-k 更新只能发送在过期之后
-l 停止账号使用
-S 显示密码信息
-u 启用已被停止的账户
-x 设置密码的有效期
-g 修改群组密码
-i 过期后停止用户账号
选择参数：

--help 显示帮助信息
--version 显示版本信息
```
passwd 命令后面不接任何参数或用户名，则表示修改当前用户的密码；请看下面的例子；

```bash
$ passwd   注：没有加任何用户，我是用root用户来执行的passwd 表示修改root用户的密码；下面也有提示；
Changing password for user root.
New UNIX password: 注：请输入新密码；
Retype new UNIX password: 注：验证新密码；
passwd: all authentication tokens updated successfully. 注：修改root密码成功；
```

如果是普通用户执行passwd 只能修改自己的密码；

如果新建用户后，要为新用户创建密码，则用 passwd 用户名 ，注意要以root用户的权限来创建；

```bash
$ passwd beinan 注：更改或创建beinan用户的密码；
Changing password for user beinan.
New UNIX password: 注：请输入新密码；
Retype new UNIX password: 注：再输入一次；
passwd: all authentication tokens updated successfully. 注：成功；
```
## 2. gpasswd
gpasswd命令 是Linux下工作组文件/etc/group和/etc/gshadow管理工具。

```bash
-a：添加用户到组；
-d：从组删除用户；
-A：指定管理员；
-M：指定组成员和-A的用途差不多；
-r：删除密码；
-R：限制用户登入组，只有组中的成员才可以用newgrp加入该组。
```
1.将userA添加到groupB用户组里面：  
```bash
gpasswd -a userA groupB
```
**注意**：添加用户到某一个组可以使用  usermod -G groupB userA 这个命令可以添加一个用户到指定的组，但是以前添加的组就会清空掉， 所以想要添加一个用户到一个组，同时保留以前添加的组时，请使用gpasswd这个命令来添加操作用户。
2.将userA设置为groupA的群组管理员：

```bash
gpasswd -A userA groupA
```
