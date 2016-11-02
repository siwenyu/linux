# mac/windows批量修改文件名后缀

无需软件批量修改文件后缀名？怎么通过命令行批量修改文件后缀名?有时候由于文件后缀名格式不同，有的时候我们需要对文件扩展名进行修改，或者文件扩展名丢失，需要添加。如果数量少的文件那还简单直接修改就好了。

### mac
在当前文件目录下创建rename.sh，讲后缀名为.text的文件改为.md(markdown)文件：

rename.sh:

```
for i in *.text;do mv "$i" "${i%.text}.md" ;done
```
然后执行这个文件，具体终端命令如下：

```
$ vim rename.sh
	for i in *.text;do mv "$i" "${i%.text}.md" ;done
$ sh rename.sh

```

### windows
通过批处理文件来实现批量修改文件后缀名,也就是.bat文件。
在当前目录下新建rename.text：
rename.text

```
ren *.text *.md
```
保存，修改此文件后缀为.bat，然后双击运行这个文件就行了。


