---
title:  Poetry - 现代Python依赖管理工具
summary: An introduction For QA to understand Poetry.
authors: [FluentQA]
tags: ['QA-Revisited']
categories: [QA-Revisited]
date: '2022-10-09'
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: black
  # Choose a code highlighting style (see Hugo docs on Chroma)
  #   Light style: github-light. Dark style: dracula (default).
  highlight_style: dracula
---

# Poetry 

Poetry - python的虚拟环境,依赖管理和打包工具

---

## Poetry 介绍 -1

- 什么是python开发中的虚拟环境,依赖管理和打包工具
- Poetry的优势是什么
- 如何使用Poetry进行python项目的依赖管理
  - 第三方依赖安装，卸载，版本管理
  - 使用本地/github/gitlab仓库代码作为第三方依赖
- Poetry 常用命令
  - init
  - install
  - run
  - update
---

## Poetry 介绍 -2

- Poetry CI
  - 不同CI流程工具
- Poetry 打包(package)
  - 打包发布
  - 命令行工具的打包

---

## 什么是依赖管理和打包工具

- python 虚拟环境的用途
- 第三方依赖怎么在项目里面管理
- 如何把写好的代码打包发布

---

## 如何使用Poetry进行python项目的依赖管理

- poetry 添加依赖

```sh
poetry add requests
```
- poetry 依赖可以管理分类
  - 生产运行使用
  - 本地开发使用
- poetry gitlab/github 依赖管理
- poetry 的优势什么？
---

## Poetry 常用命令

- poetry shell
- poetry add 
- poetry update pacakge
- poetry run
- poetry.lock文件

---

## Poetry CI 流程

- code 格式
- 单元测试和代码覆盖率
- precommit设置

---

##  Poetry 打包(package)

- poetry build
- poetry install
- 命令行工具如何打包

---

## Q&A

- Demos
- Have a try and have fun

--- 
