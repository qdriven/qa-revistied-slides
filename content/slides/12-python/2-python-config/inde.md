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

## Python Configuration 

开箱即用

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

### dynaconf 优势 - 开箱即用

初始化，自动读取settings.toml配置信息

```python

```qSettings = Dynaconf(
    settings_files=["settings.toml", ".secrets.toml"],
    environments=True,
    load_dotenv=True,
)
qSettings.validators.validate()
print("settings is loaded")
```
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

### dynaconf优势 - 使用直接
常用方法：
1. settings.<属性名> 可以直接获取
2. 支持嵌套属性: ```settings.a_dict.hello```
4. 支持多个环境不同配置,development/test/production
---

### dynaconf优势 - 使用直接
```python
# 直接读取
def test_config_default_value(): 
    assert qSettings.DB_NAME == "mydb.db"

# 内嵌
def test_config_default_nested_value():
    print(qSettings.a_dict)
    assert qSettings.a_dict.hello == "world"


def test_config_environment_setting():
    assert qSettings.name == "developer"
```

--- 

### dynaconf小结

- 开箱即用，基本功能实用
- 不需要二次开发或者适配

