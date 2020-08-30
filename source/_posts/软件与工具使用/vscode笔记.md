# vscode常见问题

## 1.怎么修改 vscode 主题颜色？

:smile:

新下载的 vscode 默认的都是黑色的主题，颜色太暗看不清怎么办？ 直接修改 vscoe 颜色颜色即可，步骤如下：

file -> preference -> color theme -> 选择 light 即可
也可以快捷键 ctrl + K + ctrl + T 直接打开颜色主题进行设置
<!--more-->
## 2.设置文件过程中自动保存

对文件的修改每次有需要手动保存 ，有没有觉得好麻烦呀？只需按照下面步骤设置轻松实现 vscode 自动编辑保存功能

    点击 vscode 界面右下角 -> settings -> 搜索框中搜索 auto save ->选择 afterDelay,同时设置延迟保存时间为 1000，大功告成

## 3.设置滚轮可调节编辑区字体大小

    在settings.json 文件中添加配置`"editor.mouseWheelZoom": true` 即可

## 4.灵活好用的快捷建

    灵活好用的系统或自定义的常用快捷键，如果系统没有该快捷建可自行配置：
    
    vscode界面及编辑区快捷键
    
    `ctrl + b` 显示/隐藏左侧状态栏
    
    `ctrl + =/-/鼠标滚轮`  调整编辑区的字体大小 ，鼠标滚轮需要进行[问题3](#3设置滚轮可调节编辑区字体大小)所示的设置
    
    `crrl + shift + -/=` 调整整个界面大小
    
    `crrl + tab` 切换到最近打开文本中


    分屏快捷键
    
    `ctrl + \` 拆分窗口组，（默认新建窗口位置在右侧）
    
    `ctrl + \  ctrl + 方向键` 选择新拆分出的窗口位置（自定义）
    
    `ctrl + j  a` 将所有其他窗口的分屏关闭，并合并当当前窗口中，可实现当前代码窗口的最大化显示（(自定义)）
    
    `ctrl + k  w` 关闭当前分屏及所有打开的文件
    
    `ctrl + k o` 关闭其他分组的窗口，保留当前分组的窗口
    
    markdown快捷键
    
    `alt + m` 激活docs-markdown菜单,实现快捷制表等操作 
       
    `ctrl + shift + v` 切换 markdown 的编辑和预览模式

## 5. 实用的扩展插件

    `Markdown All in One` 在vscode中必备的markdown插件，支持预览，基本语法等
    
    `markdownlint` markdown 语法智能提示，改善自己的md书写规范
    
    `Markdown toc` 自动生成markdown目录树，简单实用
    
    `markdown preview Enhancced` 预览增强，可支持显示复杂的公式，流程图，表格等
    
    `vscode-icons` 美化文件浏览器中的文件/文件夹图标
    
    `terminal` 下面状态栏添加终端快捷按钮
    
    `python` python环境必备的插件，识别 .py文件关联到解释器，运行等功能

## 6. 怎么拆分和合并分屏

    见 [4.灵活好用的快捷建](#4灵活好用的快捷建) 中的分屏快捷键
