#  Linux Command vim 文本编辑器
tags: 编辑器
## 1. 编辑多文件

### 1.1 在同一窗口中打开多个文件

```bash
vi file1 file2 file3
:n  切换到下一个文件 (n=next)
:N  切换到上一个文件
```

### 1.2 在不同窗口中打开多个文件：

如果已经打开一个了一个文件，
则在vi的命令输入状态下输入 :sp 另外一个文件的路径及文件名，
如此就可以在一个窗口打开多个文件了。

或者用 vi -o file1 file2 file3....用分割屏幕窗口方式同时打开多个文件。
可以使用 ctrl + 两次按 w 或者ctrl + w 然后按上下键在上下窗口间切换。
### 1.3 窗口分割实现编辑多文件
   先使用vi打开一个文件，例如vi actinia_proenrule.sh 
   分割窗口打开另外的文件
    命令行模式下输入  sp 另外一个文件 就可以水平分割继续打开第二个文件，如果想纵向分割，可以使用vsp 文件名
     注：sp=split，vsp=vsplit. 上面的写法是vi支持的简略写法，v实际就是vertical，从中我们可以看出改命令的含义，另外vi不仅仅支持两个文件，还支持更多个文件同时在一个 大的窗口中显示编辑，同时还支持同时打开的两个文件是同一个文件。
    *窗口切换
可以使用 ctrl +两次按 w，这样就可以在各个文件中切换
   之前觉得vi的多文档编辑用着很不方便，现在接触了几个，用过了MiniBufExplorer，发现看着不是很舒服。还是使用ｌｓ比较好看一些。
　

　

```bash
:ls  展示全部的打开文档
:xn  切换到向下的第x个文档
n ctrl+6 ： 切换到第n个buffer
ctrl+6  或 :e#   回到前一个编辑文件
```

　　
         分屏
 

```bash
   :new xxx
　　ctrl+w s   对当前文档内容分屏显示
　　ctrl+w q   关闭所处分屏
　　ctrl+w o   仅显示当前分屏内容
　　ctrl+w j k  上下选择分屏
```
   个人觉得最值得用的命令就是ctrl+w  w 快速在分屏的两个屏幕中切换
 
   下面写的还没用过~看了大家的分享觉得这几个还不错
 

```bash
   :n1,n2 co n3: 将n1行到n2行之间的内容拷贝到第n3行下
   :n1,n2 m n3:将n1行到n2行之间的内容移至到第n3行下
   :n1,n2 d: 将 n1行到n2行之间的内容删除
   :n1,n2 w!command: 将文件中n1行至n2行的内容作为command的输入并执行之，
```
   若不指定n1，n2，则表示将整个文件内容作为command的输入
   方式2的优点在可以直接使用nyy和pp命令在各个窗口的文件之间进行拷贝和粘贴，操作比较方便

## 2. 编辑命令
### 2.1 vim模式：

```bash
编辑模式(命令模式)
输入模式
末行模式
模式转换：
```

编辑-->输入：
  

```bash
  i: 在当前光标所在字符的前面，转为输入模式；
  a: 在当前光标所在字符的后面，转为输入模式；
  o: 在当前光标所在行的下方，新建一行，并转为输入模式；
  I：在当前光标所在行的行首，转换为输入模式
  A：在当前光标所在行的行尾，转换为输入模式
  O：在当前光标所在行的上方，新建一行，并转为输入模式；
```

输入-->编辑：
   

```bash
 ESC
```

编辑-->末行：

```bash
:
```

末行-->编辑：

```bash
 ESC, ESC
注
```

：输入模式和末行模式之间不能直接切换
### 2.2 打开文件
 

```bash
   vim +\# :打开文件，并定位于第#行
   vim +：打开文件，定位至最后一行
   vim +/PATTERN : 打开文件，定位至第一次被PATTERN匹配到的行的行首
```

注：默认处于编辑模式
### 2.3 关闭文件
2.3.1 末行模式关闭文件
 

```bash
   :q  退出

   :wq 保存并退出

   :q! 不保存并退出

   :w 保存

   :w! 强行保存

   :wq --> :x
```

2.3.2 编辑模式下退出

```bash
ZZ: 保存并退出
```

### 2.4 移动光标(编辑模式)
#### 2.4.1 逐字符移动：

```bash
h: 左

l: 右

j: 下

k: 上

#h: 移动#个字符
```

#### 2.4.2 以单词为单位移动

```bash
w: 移至下一个单词的词首

e: 跳至当前或下一个单词的词尾

b: 跳至当前或前一个单词的词首

#w: 移动#个单词
```

#### 2.4.3 行内跳转：
  

```bash
  0: 绝对行首

  ^: 行首的第一个非空白字符

  $: 绝对行尾
```

#### 2.4.4 行间跳转
 

```bash
   #G：跳转至第#行

   gg: 第一行

   G：最后一行
```

#### 2.4.5 末行模式

```bash
.: 表示当前行

$: 最后一行

#：第#行

+#: 向下的#行
```

###  2.5 翻屏
 

```bash
   Ctrl+f: 向下翻一屏
	
   Ctrl+b: 向上翻一屏

   Ctrl+d: 向下翻半屏

   Ctrl+u: 向上翻半屏
```
### 2.6 删除
#### 2.6.1 删除单个字符

```bash
x: 删除光标所在处的单个字符

#x: 删除光标所在处及向后的共#个字符
```

#### 2.6.2 删除命令: d

```bash
d命令跟跳转命令组合使用
#dw, #de, #db
dd: 删除当前光标所在行
#dd: 删除包括当前光标所在行在内的#行；
```

### 2.7 粘贴命令 p
   

```bash
p: 如果删除或复制为整行内容，则粘贴至光标所在行的下方，如果复制或删除的内容为非整行，则粘贴至光标所在字符的后面
P: 如果删除或复制为整行内容，则粘贴至光标所在行的上方，如果复制或删除的内容为非整行，则粘贴至光标所在字符的前面
```

### 2.8 复制命令 y
   

```bash
 用法同d命令
```

### 2.9 修改：先删除内容，再转换为输入模式

```bash
c: 用法同d命令
```

### 2.10 替换：

```bash
r：单字符替换
#r: 光标后#个字符全部替换
R: 替换模式
```

### 2.11 撤消编辑操作 u
 

```bash
u：撤消前一次的编辑操作
#u: 直接撤消最近#次编辑操作
连续u命令可撤消此前的n次编辑操作
撤消最近一次撤消操作：Ctrl+r
```

### 2.12 重复前一次编辑操作
  

```bash
  .：编辑模式重复前一次编辑操作
```

### 2.13 可视化模式
 

```bash
   v: 按字符选取

   V：按矩形选取
```

### 2.14 查找
 

```bash
   /PATTERN

    ?PATTERN

    n 下一个

    N 上一个
```

### 2.15 查找并替换
在末行模式下使用s命令
 

```bash
   headline,footlines#PATTERN#string#g

   1,$:表示全文

   %：表示全文
```

### 2.16 使用vim编辑多个文件
  

```bash
  vim FILE1 FILE2 FILE3

  :next 切换至下一个文件

  :prev 切换至前一个文件

  :last 切换至最后一个文件

  :first 切换至第一个文件

  :q退出当前文件

  :qa 全部退出
```

### 2.17 分屏显示一个文件

```bash
Ctrl+w, s: 水平拆分窗口

Ctrl+w, v: 垂直拆分窗口
```

在窗口间切换光标：

```bash
Ctrl+w, ARROW(h,j,k,l或方向键) 

:qa 关闭所有窗口
```

### 2.18 分窗口编辑多个文件

```bash
vim -o : 水平分割显示

vim -O : 垂直分割显示
```

### 2.19 将当前文件中部分内容另存为另外一个文件
末行模式下使用w命令

```bash
:ADDR1,ADDR2w /path/to/somewhere
```

### 2.20 将另外一个文件的内容填充在当前文件中
```bash
:r /path/to/somefile
```
  附加到当前文件光标后
### 2.21 跟shell交互

```bash
:! COMMAND
```

###  2.22 快速翻页

整页翻页：
 `ctrl-f `  - f就是forword
 `ctrl-b`  - b就是backward




翻半页

 - `ctrl-d` d=down
 - `ctlr-u`  u=up

滚一行

 - ctrl-e
 - ctrl-y

`zz` 让光标所在的行居屏幕中央
`zt` 让光标所在的行居屏幕最上一行 t=top
`zb` 让光标所在的行居屏幕最下一行 b=bottom


## 3 显示格式设置
### 3.1 显示或取消显示行号

```bash
:set nu

:set nonu

mu = number
```

### 3.2 显示忽略或区分字符大小写
 

```bash
   :set ic

   :set noic

    ic = ignorecase
```

### 3.3 设定自动缩进
 

```bash
   :set ai

   :set noai

   ai = autoindent
```

### 3.4 查找到的文本高亮显示或取消

```bash
:set hlsearch

:set nohlsearch
```

### 3.5 语法高亮

```bash
:syntax on

:syntax off
```

注:特性当前有效，如果想要永久有效需修改配置文件
## 4 配置文件
 

```bash
   /etc/vimrc    针对所有用户

    ~/.vimrc    针对当前用户
```
### 实例1
```bash
vi ~/.vimrc
---
:set number
:set et
:set sw=2 ts=2 sts=2
---
^: Start of word in line
0: Start of line
$: End of line
w: End of word
GG: End of file
```

## 5 多行处理
### 5.1 多行添加


```bash
ctrl -v
选中多行
shift+i
添加#
ESC
```


### 5.2 多行删除

```bash
Ctrl+v 
左右移动 确定列数
上下移动确定行数
按下d 删除
```
### 5.3 移动多行

```bash
$ vim ~/.vimrc
set shiftwidth=2 ##左右移动2行
```

在打开文件中

```bash
ctrl + v  可视化
上下移动确定移动行数
shift + > 向右移动2行
shift + < 向左移动2行
```

## 6. 复制乱序

```bash
set nopaste
```
参考：

 - [vim 教程](https://learnvimscriptthehardway.stevelosh.com/)
 - [Getting started with Vim: The basics](https://opensource.com/article/19/3/getting-started-vim)
 - [Getting Started with Vim Editor in Linux](https://www.geeksforgeeks.org/getting-started-with-vim-editor-in-linux/)
 - [https://www.vim.org/](https://www.vim.org/)


