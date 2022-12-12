---
title:  Poetry - Python依赖管理工具
summary: An introduction For QA to understand Poetry.
authors: [FluentQA]
tags: ['QA-Python-Revisited']
categories: ['QA-Revisited','Python']
date: '2022-11-30'
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: black
  # Choose a code highlighting style (see Hugo docs on Chroma)
  #   Light style: github-light. Dark style: dracula (default).
  highlight_style: github-light
---

# Poetry- Python 打包和依赖管理工具

--- 

## Poetry是什么

![](poetry.png)

---

## Python项目管理

- 创建虚拟环境
- 使用requirements.txt
  ```sh
    pip install <name> 
    pip freeze -r \
      > requirements.txt
  ```
- setup.py打包

---

## Poetry的好处

- 集成了上面所有功能
- 统一管理依赖和打包
- 方便使用的命令行工具
- 可以集成shell 命令自动完成功能

---

## Poetry创建项目

```python
poetry new pydaily
tree pydaily
```
![](2022-12-05-01-36-51.png)

---

## Poetry 虚拟环境
```sh
poetry shell
```
![](2022-12-05-01-37-31.png)

--- 

## Poetry 添加依赖

  ```
  poetry add requests
  poetry add pytest -D
  ```
![](2022-12-05-01-38-08.png)

--- 

## Poetry 项目文件

- pyproject.toml: 项目依赖，打包发布生声明
- poetry.lock: 确定项目安装内容
- 类似于Javascript的:
  - package.json
  - package.lock

---

## Poetry: pyporject.toml

![](2022-12-05-01-39-09.png)

--- 

## Poetry 常用命令

- poetry add : 添加依赖
- poetry install: 安装所有poetry.toml 文件声明的依赖
- poetry update: 更新所有依赖
- poetry run: 运行命令
- poetry build: 打包
- poetry publish: 发布包
  
---

## Poetry使用的好处

- 集成python从虚拟环境，第三方依赖，打包和发布功能
- 一个工具搞定所有项目配置
- 使用和其他语言理念一致
  * npm package.json
  * maven/gradle: pom.xml/build.gradle
  * go: go.mod
---

## Poetry使用Cheatsheet

---

## Poetry 使用教程视频

## Q&A

- Demos
- Have a try and have fun

--- 
