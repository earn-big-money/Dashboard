# EDM 挣闲钱任务发布app gh-pages

> 本分支主要是提交中山大学数据科学与计算机学院系统分析与设计课程相关的文档作业

## 为什么需要用 gh-pages ?

1. 使用它我们可以把精力专注于书写，只需要提交 md 文件即可。



## 注意事项

### 1. 文件命名规范

eg.
`XX-XX-XX-demo.md` 使用`-`来进行连接，所有单词小写，前面先通过数字表明在`index.md`中的结构位置



### 2. 图片路径

插入 Github 上面的图片时其链接一定要注意，请在原 img 上右键复制该图片的实际存放的路径而不是在github 上的网页路径。否则 gitpages 会渲染不出来。



对于同一张图片，有下面示例。

错误示例 `https://github.com/rookies-sysu/Dashboard/blob/master/imgs/db/ER_model.png`

正确示例 `https://github.com/rookies-sysu/Dashboard/blob/master/imgs/db/ER_model.png?raw=true`

**每次提交后都上 git pages 确认一下图片的生成即可。**



### 3. 提交流程

1. 按照命名规范命名新文件
2. 修改`index.md`来索引新加入的文件
3. 提交

### 4. markdown 规范

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```


### 5.代码提交流程

因为是Dashboard，没有collaboration的权限。

只能通过fork到本地，进行需要的修改，修改并且update后可以通过自己的fork repo中的new pull request来与base repo中的master branch进行请求合并，此时会需要对于可能存在的冲突进行修改，没有冲突后即可以提交pull request，再被repo 的master review后就可以被merge到master branch中。

[offical help infomation](https://help.github.com/en/articles/creating-a-pull-request)