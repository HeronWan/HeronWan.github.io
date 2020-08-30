# [MyNotes](https://heronwan.github.io/)



## 相关命令



- `hexo c` //清除public中生成的编译文件

- `hexo g` //生成public编译文件

- `hexo s` //启动本地服务，浏览器中可查看项目

- `hexo d` //项目部署远程，将生成的public中的文件推送到远程master分支中

- `hexo c` && hexo g &&hexo d && hexo s

- `git pull` //同步远程的修改

- `git add .` //将本地修改添加到暂存区

- `git commit -m "提交信息"` // 将修改提交到本地仓库

- `git push origin hexo` //推送到远程的hexo分支中

 <!--more-->

1. 一键部署：

 hexo c && hexo g && hexo g && hexo s



2. 博客迁移

> git clone https://github.com/HeronWan/HeronWan.github.io.git hexo # 克隆远程仓库

> npm install -g hexo-cli #安装全局hexo环境，可提供hexo c/g/s/d命令使用

> npm install # 本地安装依赖（会将package.json中的依赖全部安装）



3. 同步博客源码：

 git add . && git commit -m "some changes" && git push origin hexo



## 博客源码维护

该仓库中有两个分支：

1. master负责保存编译好了的部署文件，在本地执行“hexo d”就会自动更新部署

2. hexo保存的是该仓库的源码，包括配置文件和md文件以及其他页面的源码。在本地修改可通过git命令提交维护。



## todos



1. leetcode刷题
2. 2. opencv实战

3. 动手学深度学习pytorch实战





## 搭建流程

1. 需要本地预先安装好安装好git和node环境

2. 在node全局环境中安装hexo-cli手脚架`npm install -g hexo-cli`

3. 在本地新建一个空白文件夹，注意文件夹一定要是空白的，在该文件夹路径打开终端，运行：

- `hexo init`   # 初始化 

- `npm install`  # 安装组件

4. 启动本地进行预览

- `hexo g` 生成编译文件

- `hexo s` 启动服务器，访问 http://localhost:4000，出现 Hexo 默认页面，本地博客安装成功！



5. 在码云上创建gitee pages

6. 配置文件

7. 部署 命令`hexo d`

  `hexo clean && hexo g && hexo d && hexo g` 

 