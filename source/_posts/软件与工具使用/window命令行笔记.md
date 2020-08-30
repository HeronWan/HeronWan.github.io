# windows下面有用的cmd指令

### 1. 临时禁用键盘

说明： 之前键盘坏了，敲键盘的的时候会一直输入字符k，于是使用卸载驱动的形式，将键盘禁用了，现在我只是想临时的想要禁用自己笔记本的键盘，便于在自己的键盘上放书或者本子什么的，方便阅读和外接键盘的输入。于是就搜到了如下的命令，解决自己的燃眉之急

禁用键盘：sc config i8042prt start= disabled，重启

恢复键盘：sc config i8042prt start= auto， 重启

###  2. 将cpp文件编译生成的exe文件放在指定的位置

需求说明：在编译单个cpp文件时，生成的exe文件总是放在当前文件夹下面，我花费了点心思，终于解决了将当前文件夹下面cpp编译生成的exe文件，放在当前文件下下面的build文件夹里面。

修改Setting.json文件里面的"code-runner.executorMap"."cpp"的值为：

```
"code-runner.executorMap": {
	...
    "cpp": "cd $dir &&  (IF NOT EXIST build (md build) )  && g++ $fileName -o build\\$fileNameWithoutExt && $dir\\build\\$fileNameWithoutExt",
    ...
}
```



上面其实就是将四句cmd命令合并成一句执行。

```
cd $dir     //进入到当前执行文件所在的文件夹

( IF NOT EXIST build (md build)  )  //  当前文件夹下面如果不存在build文件夹就创建build文件夹

g++ $fileName -o build\\$fileNameWithoutExt //编译当前文件并将编译结果放置在build文件夹下面

$dir\\build\\$fileNameWithoutExt //执行已经编译好的可执行文件
```







