---

---
# MyNotes

## 相关命令


- `hexo c`  //清除public中生成的编译文件
- `hexo g`  //生成public编译文件
- `hexo s`  //启动本地服务，浏览器中可查看项目
- `hexo d`  //项目部署远程，将生成的public中的文件推送到远程master分支中
- `hexo c` && hexo g &&hexo d && hexo s
- `git pull` //同步远程的修改
- `git add .` //将本地修改添加到暂存区
- `git commit -m "提交信息"` // 将修改提交到本地仓库
- `git push origin hexo` //推送到远程的hexo分支中
  
一键部署：
  hexo c && hexo g && hexo g && hexo s

意见推送源码：
  git add . && git commit -m "some changes" && git push origin hexo

## 博客源码维护

该仓库中有两个分支：
1. master负责保存编译好了的部署文件，在本地执行“hexo d”就会自动更新部署
2. hexo保存的是该仓库的源码，包括配置文件和md文件以及其他页面的源码。在本地修改可通过git命令提交维护。

## todos

1. leetcode刷题
2. opencv实战
3. 动手学深度学习pytorch实战