# 每天一个linux命令-cat.md

cat主要有三个功能

1. 显示文件：新手看文件会vim doc.md，有点弱。

```
➜  linux练习 cat end
text1.md
text1.md

➜  linux练习 cat text1.md
# 这是文档
```

2. 新文件(不是已有文件)写入内容。如果写入一个已有文件，不仅你编辑的内容写不进去，原来的内容也会被清空，只剩一个空文件。

```
➜  linux练习 rm cat.md
➜  linux练习 ls
base		end		text.md		text1.md
➜  linux练习 cat >cat.md
我正在编辑这cat.md文件 ，这 部分内容会被写进cat.md文件。^C
➜  linux练习 ls
base		cat.md		end		text.md		text1.md
➜  linux练习
```

3. 讲几个文件合并成一个文件。很奇怪，这个是可以写入一个已经存在的文件的，会覆盖原来的内容。但是使用>>代替>可以在文件后边追加另一个文件的内容，不清空原来的内容。

```
➜  linux练习 ls
base		cat.md		end		text.md		text1.md
➜  linux练习 cat text.md
这是第一个文件
➜  linux练习 cat text1.md
这是第二个文件
➜  linux练习 cat text.md text1.md >cat合并.md
➜  linux练习 ls
base		cat合并.md	text.md
cat.md		end		text1.md
➜  linux练习 cat cat合并.md
这是第一个文件
这是第二个文件
```
