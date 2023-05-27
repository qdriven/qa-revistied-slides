---
title:  dynaconf - 开箱即用的配置管理
summary: Out-of-box Python Configuratio
authors: [FluentQA]
tags: ['QAPython-Revisited']
categories: ['QAPython-Revisited']
date: '2022-12-10'
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: white
  # Choose a code highlighting style (see Hugo docs on Chroma)
  #   Light style: github-light. Dark style: dracula (default).
  highlight_style: dracula
---

## python开箱即用配置管理-dynaconf


> dynaconf: Configuration Management for Python.
   
> https://www.dynaconf.com/

--- 

###  python配置文件

配置文件的用途: 
> 配置和代码分离，不同环境只修改配置即可

自己写获取配置文件方法: 有点小麻烦
1. 读取文件
2. 解析数据,可能还不同格式
3. .......

---


### dynaconf 优势

1. 开箱即用
2. 支持多格式```toml|yaml|json|ini|py```
3. 基本功能实用方便，同时又支持很多复杂配置

---

### dynaconf- 配置文件
配置文件settings.toml
```toml
[default]
DB_NAME = "mydb.db"
a_dict = { hello = "world" }
[development]
DB_PATH = "@format {env[HOME]}/{this.DB_NAME}"
name = "developer"
[test]
DB_PATH = "@format {env[HOME]}/{this.DB_NAME}"
name = "test"
[production]
name = "admin"
```

--- 

### dynaconf使用 - 开箱即用

初始化:自动读取settings.toml配置信息

```python

qSettings = Dynaconf(
    settings_files=["settings.toml", ".secrets.toml"],
    environments=True,
    load_dotenv=True,
)
qSettings.validators.validate()
print("settings is loaded")
```
--- 
### dynaconf优势 - 使用直接
如何从上面的settings文件中获取值:
```python
# 直接读取
def test_config_default_value(): 
    assert qSettings.DB_NAME == "mydb.db"
```
1. settings.<属性名> 可以直接获取
2. 支持嵌套属性: ```settings.a_dict.hello```
4. 支持多个环境不同配置,development/test/production
---

### dynaconf优势 - 嵌套值

从上面的settings文件中获取嵌套值: ```settings.a_dict.hello```
```python
def test_config_default_nested_value():
    print(qSettings.a_dict)
    assert qSettings.a_dict.hello == "world"
```

### dynaconf优势 - 不同环境的值

不同环境的值:name, 通过.env文件配置

```
def test_config_environment_setting():
    assert qSettings.name == "developer"
```

--- 

### dynaconf小结

- 开箱即用，基本功能实用
- 不需要二次开发或者适配

---
### dynaconf 可以学习的依赖库

- Box: https://box.readthedocs.io/
- 这个库解决了一个问题,不用```dict[key]```   这种方式取值，用 ```dict.key``` 也可以取值
- 原理可以自己看源码，如果像要听讲可以留言

### dynaconf 视频说明
- [[无废话python] PYTHON开箱即用配置管理-DYNACONF
](https://www.bilibili.com/video/BV1WV4y1F7pU/)

---