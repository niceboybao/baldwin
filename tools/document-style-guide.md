# 中文技术文档的写作规范

## Learn more here

[document-style-guide](https://github.com/ruanyf/document-style-guide)

[参考链接](https://github.com/ruanyf/document-style-guide/blob/master/docs/reference.md)

## Some useful points

### 1.文档体系

软件手册是一部完整的书，建议采用下面的结构。

- **简介**（Introduction）： [必备] [文件] 提供对产品和文档本身的总体的、扼要的说明
- **快速上手**（Getting Started）：[可选] [文件] 如何最快速地使用产品
- **入门篇**（Basics）： [必备] [目录] 又称"使用篇"，提供初级的使用教程

  - **环境准备**（Prerequisite）：[必备] [文件] 软件使用需要满足的前置条件
  - **安装**（Installation）：[可选] [文件] 软件的安装方法
  - **设置**（Configuration）：[必备] [文件] 软件的设置

- **进阶篇**（Advanced)：[可选] [目录] 又称"开发篇"，提供中高级的开发教程

- **API**（Reference）：[可选] [目录|文件] 软件 API 的逐一介绍

- **FAQ**：[可选] [文件] 常见问题解答

- **附录**（Appendix）：[可选] [目录] 不属于教程本身、但对阅读教程有帮助的内容

  - **Glossary**：[可选] [文件] 名词解释
  - **Recipes**：[可选] [文件] 最佳实践
  - **Troubleshooting**：[可选] [文件] 故障处理
  - **ChangeLog**：[可选] [文件] 版本说明
  - **Feedback**：[可选] [文件] 反馈方式

下面是两个真实范例，可参考。

- [Redux 手册](http://redux.js.org/index.html)
- [Atom 手册](http://flight-manual.atom.io/)

### 2.文件名

文档的文件名不得含有空格。

文件名必须使用半角字符，不得使用全角字符。这也意味着，中文不能用于文件名。

```
错误： 名词解释.md

正确： glossary.md
```

文件名建议只使用小写字母，不使用大写字母。

```
错误：TroubleShooting.md

正确：troubleshooting.md
```

为了醒目，某些说明文件的文件名，可以使用大写字母，比如`README`、`LICENSE`。

文件名包含多个单词时，单词之间建议使用半角的连词线（`-`）分隔。

```
不佳：advanced_usage.md

正确：advanced-usage.md
```

### 3.参考链接

- [产品手册中文写作规范](http://wenku.baidu.com/view/23cc1a6527d3240c8447efbf.html), by 华为
- [写作规范和格式规范](http://docs.daocloud.io/write-docs/format), by DaoCloud
- [技术写作技巧在日汉翻译中的应用](http://www.hitachi-tc.co.jp/company/thesis/thesis.pdf), by 刘方
- [简体中文规范指南](https://www.lengoo.de/documents/styleguides/lengoo_styleguide_ZH.pdf), by lengoo
- [文档风格指南](https://open.leancloud.cn/copywriting-style-guide.html), by LeanCloud
- [豌豆荚文案风格指南](https://docs.google.com/document/d/1R8lMCPf6zCD5KEA8ekZ5knK77iw9J-vJ6vEopPemqZM/edit), by 豌豆荚
- [中文文案排版指北](https://github.com/sparanoid/chinese-copywriting-guidelines), by sparanoid
- [中文排版需求](http://w3c.github.io/clreq/), by W3C
- [为什么文件名要小写？](http://www.ruanyifeng.com/blog/2017/02/filename-should-be-lowercase.html), by 阮一峰
- [Google Developer Documentation Style Guide](https://developers.google.com/style/), by Google
