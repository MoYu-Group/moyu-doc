# 简介
摸鱼开发小组文档库，用于储存摸鱼小组开发文档

https://doc.ffis.me

- 使用 docsify 构建，部署于 CloudFlare Pages
- 评论系统使用 Gitalk

## 编写文档

- 只有摸鱼开发组人员可编写文档
- 编写文档时要先确定归属文件夹，根目录每个文件夹对应一个项目
- 文档命名规则
  - 文档名称统一使用英文 <s>（可用拼音）</s>
  - 多个单词之间只能使用短横杠 `-` 隔开
  - 文档名称不可超过50个字符
- 编写 markdown 格式文档，储存到对应项目文件夹中
- 更新文档目录 `sidebar.md`，包括文档目录名称和文档相对访问地址
- 提交 commit 即可自动触发 CloudFlare Action 自动更新在线文档

## 本地运行
```bash
git clone https://github.com/MoYu-Group/moyu-doc.git
cd moyu-doc
docsify serve .
```

## 摸鱼开发小组

- 摸鱼开发小组，只有摸鱼的时候才会开发
- 我们的宗旨：让每一位同学切实的参与到开源项目的每一个环节中，共同学习和成长，一起摸鱼~
- 欢迎志同道合的同学们加入我们~
