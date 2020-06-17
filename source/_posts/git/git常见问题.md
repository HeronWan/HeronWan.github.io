---
toc:
  depth_from: 2
  depth_to: 6
  ordered: false
---
# git常见问题汇 

## 1. git怎么快捷提交到远程

有时候只是修改了一个简单的地方，但是提交却要好几行才能完成

```bash
git add .
git commit -am "change some text"
git push
```

能不能把这几句合并成一句，以后再也不用桥一些繁琐的命令，以提高工作效率
当然可以，如下：
<!--more-->
> git add . &&  git commit -am "change some text" && git push

一句搞定！
但是问题来了，这句命令也太长了吧，做人能不能简单一点，不要搞得那么复杂吗！或者能直接设置快捷键呢？

好的，满足你，跟着我来一起做，步骤如下：

1. 用vscode打开当前仓库，配置task.json:

    点击vscode界面左下角，打开 command palette.. ---> 输入task 进行搜索  --->  选择task：configure task -> 选择task 模板 ，新建task.json文件 ---> 在task.json文件中修改成以下内容：

    ```md
    {
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "push code",
            "type": "shell",
            "command": "git add . &  git commit -am 'change something' & git push"
        }
    ]
    }
    ```

2. 验证 task是否能运行：

    点击vscode界面左下角，打开 command palette.. ---> 输入run task 回车 ---> 点击 push code看task是否能成功执行

3. 配置快捷键：

    file ---> preference ---> keyboard shortcut ---> 打开了快捷键配置文件，点击右上角的 {}，进入文本编辑模式，添加如下内容：

    ```markdown
    [
        {
            // 为git提交代码到远程仓库设置快捷键 
            "key": "ctrl+p ctrl+p",
            "command": "workbench.action.tasks.runTask",
            "args": "push code",
            "when": "isLinux"    
        }
    ]
    ```

4. 使用 快捷键"ctrl+p ctrl+p" 验证是否能成功push代码到远程仓库。

原本按照这个想法，我想到了两个思路：

1. 通过vscode的设置task和快捷键完成操作，步骤如上。

2. 将三条命令alias一条简短的快捷命令,在终端上执行。
   
    2.1 但是这个并没有想象中那么简单，至少在gitvonfig中是难以实现的。因为 alias 中的快捷命令是需要运行时需要在前面添加 git 才能运行的，比如：<code>alias p=push </code>，那么在命令行运行 <code>git p</code> 就相当于 <code>git push </code>。这就限制了无法用 将这三条命令 缩写成一条命令来运行。

    2.2 但是世上无难事，只要有心人，曲线也是能救国的！不要局限在git的配置中怎么去实现，思维要开阔些！我们可以在当前文件夹下面新建一个bash脚本，把上面三条命令直接写进去，直接运行脚本不就可以了嘛!

    当前文件夹下面创建push.sh,写入文本：
        
    ```md
    git add .
    echo 成功添加暂存区
    git commit -am "change some text"
    echo 成功提交到本地仓库
    git push
    echo 成功push到远程仓库
    ```

    在当前文件夹下面的终端运行：
    > chmod a+x push.sh 
    > 
    > ./push.sh

## 2. git提交码云上没有显示贡献度

  结果竟然是因为我设置的全局邮箱有问题:
    
  ```
  user.email="1002860620@qq.com"
  user.name=heronwang
  ```
  
  上面所示，邮箱多了一双引号，去掉引号就可以啦
  `git config --global user.email 1002860620@qq.com`
  
  然后再输入`git config -l` 查看配置：

  ```
  user.email=1002860620@qq.com
  user.name=heronwang
  ```

  引号去掉了，然后`git push`提交，在后台查看终于显示我的贡献度了，

  好气哦，ubuntu用了这么长时间，在码云上提交了那么多贡献全是空的！！


## 3.怎么给仓库打tag，记录历史中重要的节点

首先`git tag -l` 查看仓库中所有tag 

Git 支持两种标签：轻量标签（lightweight）与附注标签（annotated）

- 轻量标签：很像一个不会改变的分支——它只是某个特定提交的引用。
  
  `git tag <tagname>` 创建轻量标签
  `git show <tagname>` 显示出提交信息

- 附注标签：是存储在 Git 数据库中的一个完整对象， 它们是可以被校验的，其中包含打标签者的名字、电子邮件地址、日期时间， 此外还有一个标签信息，并且可以使用 GNU Privacy Guard （GPG）签名并验证。
  `git tag -a <tagname> -m "标签信息"` 创建附注标签

- 后期打标签：你也可以对过去的提交打标签
  `git log --pretty=oneline` 显示历史提交信息
  `git tag -a <tagname> <某个提交的哈希码>` 为历史提交打标签

- 共享标签：将标签上传到远程共享
  `git push origin --tags` 上传所有tags
  `git push origin <tagname>` 上传某个tag

- 删除标签tag
  `git tag -d <tagname>` 删除本地tag
  `git push origin --delete <tagname>`   删除远程tag

- 检出标签：如果你想查看某个标签所指向的文件版本，可以使用 git checkout 命令， 虽然这会使你的仓库处于“分离头指针（detached HEAD）”的状态——这个状态有些不好的副作用，在“分离头指针”状态下，如果你做了某些更改然后提交它们，标签不会发生变化， 但你的新提交将不属于任何分支，并且将无法访问，除非通过确切的提交哈希才能访问。 因此，如果你需要进行更改，比如你要修复旧版本中的错误，那么通常需要创建一个新分支。
   `git checkout <tagname>` 查看标签具体内容

   `git checkout -b <branchName> <tagname>` 为某个标签创建分支

