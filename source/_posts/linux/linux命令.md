# linux常见问题总结

    这个是在使用linux/ubuntu 系统过程中，对遇到的问题进行记录总结，以备后用。好记性不如烂键盘！

## 1. 怎么使用管理员权限打开文件夹?

    > sudo natilus
<!--more-->
## 2. 浏览器看不了视频?

    安装flash,执行一下命令前先需要设置允许安装未知版权的软件：  system settings -> software&updates -> ubuntu software -> 取消software restricted copyright or legal issues(第四个选项)

    >  sudo apt-get install flashplugin-installer

    安装html5音视频所支持的依赖
  
    > sudo apt-get update
    >
    > sudo apt-get install ubuntu-restricted-extras

## 3. 多条命令执行区别

    （1） 每个命令之间用;隔开

    说明：各命令的执行给果，不会影响其它命令的执行。换句话说，各个命令都会执行，但不保证每个命令都执行成功。

    （2） 每个命令之间用&&隔开

    说明：若前面的命令执行成功，才会去执行后面的命令。这样可以保证所有的命令执行完毕后，执行过程都是成功的。

    （3）每个命令之间用||隔开

    说明：||是或的意思，只有前面的命令执行失败后才去执行下一条命令，直到成功执行一条命令为止。

    （4）每个命令之间用&隔开
    说明：&表示and，按顺序执行每条命令，但是前后不影响，也就是无论第一条是否执行失败，后一条总是要执行

    （5）每个命令之间用|隔开
    说明：管道符|，前一条执行的结果作为后一条执行语句的输入，依次执行。

## 4.Ubuntu安装各种格式软件

    安装.deb格式的软件
    dpkg -i <package.deb>

## 5. 快速回到桌面快捷键

`ctrl + win + d` 快速回到桌面快捷键