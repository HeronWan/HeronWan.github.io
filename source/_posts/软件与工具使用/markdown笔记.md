# markdown疑难杂症


## 1. 单文件怎么生成目录，并实现点击即可定位

### 方法1:手动添加
    
原始格式如下所示，效果正如当前页面所生成的问题目录格式，原理其实是类似于插入链接的格式。插入链接格式

[点击跳转我的linux笔记](https://gitee.com/heronwang/linux_notes)

这里的链接的原始格式：
<!--more-->
```md
[点击跳转我的linux笔记](https://gitee.com/heronwang/linux_notes)
```


```md
[点击跳转](#id值)
```

整个目录模板格式如下：

```md
# <center> 标题 </center>
----
## 目录
1. [目录1](#jump1)
2. [目录2](#jump2)

---
### <a id="jump1">1. 目录1</a>
---
### <a id="jump2">2. 目录2</a>
```

### 方法2:使用vscode插件:Markdown-toc自动生成（简单易用）

- 在vscode扩展中搜索 Markdown-toc,点击安装。
- 进入vscode的系统设置settings,搜索eol,将换行设置为/n,这里我是linux系统设置为/n,windows系统设置为 /r/n 。
- 然后回到markdown文档中，右键选择 Markdown toc:insert/update，即可根据标题自动生成目录

### 方法3:使用markdown all in one 支持的toc创建toc
    
  打开相应的文件，ctrl +shift+ p 调出命令行，搜索toc，执行Markdown:create content of table


## 2. 原始格式输出

使用 ``` （ ` 位于esc的下面一个按键）将代码块包裹起来即可原始格式输出markdown，如下所示：

  ````md
  ```markdown
    # 一级标题
    ## 二级标题
    ### 三级标题
  ```
  ````

## 怎么使用flow流程图

示例：
````
```flow    
//这里定义结构以及节点等
st=>start: 开始
e=>end: 结束
op=>operation: 我的操作
cond=>condition: 确认？
op2=>operation: 操作2

//这里写流程
st->op->cond->op2
cond(yes)->e
cond(no)->op2

```
````

显示如下所示(vscode需要使用MPE插件预览)：


```flow    
//这里定义结构以及节点等
st=>start: 开始
e=>end: 结束
op=>operation: 我的操作
cond=>condition: 确认？
op2=>operation: 操作2

//这里写流程
st->op->cond->op2
cond(yes)->e
cond(no)->op2
```

## 怎么使用math公式

1. 矩阵使用：
  `$这里单行公式$`
  
  ```
  $$
  这里添加多行公式
  $$
  ```

$$
  平移矩阵：M=
  \left[\begin{matrix}
   1 & 0 & 100 \\
   0 & 1 & 100 \\
  \end{matrix} \right]\tag{A}
$$

## 怎么使用表格

实例如下，3列7行的表格：

```
| Column1 | Column2 | Column3 |
|---------|---------|---------|
| Row1    |         |         |
| Row2    | dfd     |         |
| Row3    |         |         |
| Row4    |         |         |
| Row5    |         |         |
| Row6    |         |         |
| Row7    |         |         |
```

显示如下：

| Column1 | Column2 | Column3 |
|---------|---------|---------|
| Row1    |         |         |
| Row2    | dfd     |         |
| Row3    |         |         |
| Row4    |         |         |
| Row5    |         |         |
| Row6    |         |         |
| Row7    |         |         |


相关的快捷键
`alt + m` 打开生成markdown结构的的菜单，选择table输入要生成的行列

`ctrl + d  t` 均与分布表格单元格（相当于美化表格）

