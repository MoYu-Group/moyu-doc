# 简介
摸鱼开发小组文档库，用于储存小组开发规范，项目开发文档等

https://doc.ffis.me

- 使用 docsify 构建，部署于 Github Pages
- 评论系统使用 gitalk

### 编写文档

- 只有项目开发人员可编写文档
- 编写文档时要先确定归属文件夹，每个文件夹对应一个项目
- 文档命名规则
  - 文档名称统一使用英文 <s>（可用拼音）</s>
  - 多个单词之间只能使用短横杠 `-` 隔开
  - 文档名称不可超过50个字符
- 编写好 markdown 文档，储存到对应文件夹中
- 更新文档目录 `sidebar.md`，包括显示名称和文档相对访问地址
- 提交 commit 即可自动触发 Github Action 自动更新在线文档