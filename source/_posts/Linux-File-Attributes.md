---
title: 文件基本属性
date: 2018-12-29 16:36:59
tags: Linux
---
### 文件属性

每个文件的属性由左边第一部分的10个字符来确定（如下图）：
![file-attributes](file_attributes.png)

第一个字符表示这个文件是目录，文件或链接文件等等
- d: 目录
- -: 文件
- l: 链接文档
- b: 装置文件里面的可供储存的接口设备（可随机存取装置）
- c: 装置文件里面的串行端口设备，例如键盘，鼠标（一次性读取装置）

后面九位表示：user,group,other 三者的 rwx 权限

### chgrp 更改文件属组

`chgrp [-R] [group name] [file name]`

- -R: 递归更改文件属组，就是在更改某个目录文件的属组时，会将该目录下的所有文件的属组都更改

### chown 更改文件属主

也可以同时更改文件属性：

```
chown [-R] [owner name] [file name]
chown [-R] [owner name]:[group name] [file name]
```

### chmod 更改文件九个属性

Linux文件属性有两种设置方法，一种是数字，一种是符号。
Linux文件的基本权限就有九个，分别是 user/group/others 三种身份各有自己的 read/write/execute 权限。

#### 数字表示法

数字就是三位二进制表示的十进制数。

`chmod [-R] xyz [file or directory name]`

- xyz : 就是刚刚提到的数字类型的权限属性，为 rwx 属性数值的相加
- -R : 进行递归(recursive)的持续变更，亦即连同次目录下的所有文件都会变更

#### 符号表示法

可以使用 u, g, o 来代表三种身份的权限。

此外， a 则代表 all，即全部的身份。读写的权限可以写成 r, w, x，也就是可以使用下表的方式来看：

![chmod by character](chmod_by_character.png)

`chmod u=rwx,g=rx,o=r [file name]`
`chmod a-x [file name]`
