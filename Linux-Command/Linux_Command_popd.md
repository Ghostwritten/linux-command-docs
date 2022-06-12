#  Linux Command popd

## 1. 简介
popd命令用于从目录堆栈中删除目录。popd 中的“d”代表目录，因为它将目录路径删除到堆栈中。执行此命令后，当前目录堆栈显示为以空格分隔的目录列表。在每个 popd命令之后，目录堆栈的大小都会减小。此目录堆栈基于后进先出 (LIFO) 原则。
## 2. 语法

```bash
popd [OPTIONS] [DIRECTORY]
```

## 3. 参数

```bash
+N：将第N个目录删除（从左边数起，数字从0开始）；
-N：将第N个目录删除（从右边数起，数字从0开始）；
-n：将目录出栈时，不切换目录。
```

## 4. 实例

```bash
root@Mylinux:/tmp/dir4# popd（相当于popd +0）
/tmp/dir3 /tmp/dir2 /tmp/dir1 ~

root@Mylinux:/tmp/dir3# pushd /tmp/dir4
/tmp/dir4 /tmp/dir3 /tmp/dir2 /tmp/dir1 ~

root@Mylinux:/tmp/dir4# popd +1
/tmp/dir4 /tmp/dir2 /tmp/dir1 ~

root@Mylinux:/tmp/dir4# popd -2
/tmp/dir4 /tmp/dir1 ~
```
