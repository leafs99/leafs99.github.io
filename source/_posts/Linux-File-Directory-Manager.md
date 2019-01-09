---
title: 文件及目录管理
date: 2018-12-28 17:20:37
tags: Linux
---

### 常见处理目录的命令
- ls
- cd
- pwd
- mkdir
- rmdir
- cp
- rm
- mv

note: *man* 命令可用来查看各个命令的使用文档，如：
` man cp`

### ls (列出目录)
` ls [directory_name]`

- -a: 连同隐藏文件一起列出来
- -l: 列出目录内文件的详细信息
- -d: 只列出这个目录本身，而不是它的子文件们

` ls -al ~ `

*这个命令会列出父目录下的所有文件（含属性和隐藏项）*

### cd（切换目录）
cd: change directory

```
mkdir go
cd /root/go
cd ./go
cd ~
cd ..
```
### pwd（显示目前所在目录）

`pwd [-P]`

- -P：(大写)，显示出确实的路径，而不是连结路径(link)

### mkdir（创建新目录）

`mkdir [-mp] [directory name]`

- -m: 配置目录的权限，而不是默认权限（umask）的 755
- -p: 直接递归创建多层目录

```
mkdir test
mkdir -m 711 test2
mkdir -p test1/test2/test3
```

### rmdir（删除空目录）

`rmdir [-p] [directory name]`

- -p: 连同上一级目录也删除

```
rmdir test
rmdir -p test1/test2/test3
```

### cp（复制文件或目录）

```
cp [-adfilprsu] source destination
cp [-adfilprsu] source1 source2 source3 ... directory
```

- -a: 相当于 -pdr，如果是连结档就复制连结档的属性，如果是文件就连同文件一起复制，如果是目录就连同所有子目录一起复制
- -d: 若来源是连结档，就复制连结档属性而非文件本身
- -f: 若目标文件已经存在并且无法开启，则移除后再尝试一次
- -i: 若目标档已经存在时，在覆盖时会先询问是否进行下去(常用)
- -l: 进行硬式连结(hard link)的连结档创建，而非复制文件本身
- -p: 连同文件的属性一起复制过去
- -r: 递归持续复制，用于目录的复制行为(常用)
- -s: 复制成为符号连结档(symbolic link)，亦称捷径文件
- -u: destination 比 source 旧的时候才升级 destination

```
cp ~/.bashrc /tmp/bashrc
cp -i ~/.bashrc /tmp/bashrc
```
### rm（移除文件或目录）

`rm [-fir] [file/directory]`

- -f: 忽略不存在的文件，全部删除
- -i: 删除前会询问
- -r: 递归删除，常用于目录删除中

### mv（移动文件与目录或修改名称）

```
mv [-fiu] source destination
mv [-fiu] source1 source2 source3 ... directory
```
- -f: 忽略不存在的文件，全部移动
- -i: 移动前会询问
- -u: 递归移动，常用于目录这个移动

### touch（创建文件）

```
touch f1.js
```

### 文件内容查看命令

- cat
- tac
- nl
- more
- less
- head
- tail

### cat
由第一行开始显示文件内容

`cat [-benstuv]`

- -b: 列出行号，仅显示非空白行的行号
- -E: 将结尾的断行字节 $ 显示出来
- -n: 列印出行号，连同空白行也有行号
- -T: 将 [tab] 按键以 ^I 显示出来
- -v: 列出一些看不出来的特殊字符

### tac
与 cat 命令相反，从文件最后一行开始显示

### nl
显示行号

`nl [-bnw] [file name]`

- -b ：指定行号指定的方式，主要有两种
- -b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)
- -b t ：如果有空行，空的那一行不要列出行号(默认值)
- -n ：列出行号表示的方法，主要有三种
- -n ln ：行号在荧幕的最左方显示
- -n rn ：行号在自己栏位的最右方显示，且不加 0
- -n rz ：行号在自己栏位的最右方显示，且加 0
- -w ：行号栏位的占用的位数

### more
一页一页翻动

`more [file name]`

- 空白键 (space)：代表向下翻一页
- Enter         ：代表向下翻『一行』
- /字串         ：代表在这个显示的内容当中，向下搜寻『字串』这个关键字
- :f            ：立刻显示出档名以及目前显示的行数
- q             ：代表立刻离开 more ，不再显示该文件内容
- b 或 [ctrl]-b ：代表往回翻页，不过这动作只对文件有用，对管线无用

### less

`less [file name]`

- 空白键    ：向下翻动一页
- [pagedown]：向下翻动一页
- [pageup]  ：向上翻动一页
- /字串     ：向下搜寻『字串』的功能
- ?字串     ：向上搜寻『字串』的功能
- n         ：重复前一个搜寻 (与 / 或 ? 有关！)
- N         ：反向的重复前一个搜寻 (与 / 或 ? 有关！)
- q         ：离开 less 这个程序

### head
取出文件前几行

`head [-n number] [file name]`

- -n ：后面接数字，代表显示几行的意思

默认是前 10 行。

### tail
取出文件后几行

`tail [-n number] [file name]`

- -n ：后面接数字，代表显示几行的意思
- -f ：表示持续侦测后面所接的档名，要等到按下[ctrl]-c才会结束tail的侦测
