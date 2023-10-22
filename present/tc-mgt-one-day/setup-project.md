---
theme: eloc
---

## 一个文件启动一个系统

***一个JAVA文件运行启动一个后台管理系统***
---

## ***一个JAVA文件运行启动一个后台管理系统***

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import xyz.erupt.core.annotation.EruptScan;

@SpringBootApplication
@EruptScan
public class QAWorkspaceApp {
    public static void main(String[] args) {
        SpringApplication.run(QAWorkspaceApp.class);
    }
}
```

---

## 当然还有一些其他

- 一个命令启动数据库
- 一个命令打包/运行JAVA包
- 权限管理内部已经集成

---

## 技术栈基本介绍

- Low-Code Solution:
  - JAVA/SpringBoot
  - **[erupts](https://www.yuque.com/erupts/erupt)**
- 优势：
  - 低成本/快速开发
  - 几乎不用前端代码开发,又后端JAVA基础就可以
- JAVA/MAVEN/Springboot

---


## 验证JAVA/MAVEN安装完成

```sh
java -version
mvn -v
```

---

## Setup MAVEN Project

1. 创建MAVEN项目
2. 添加erupt/springboot相关依赖
3. 添加数据库配置

---

##  数据库搭建

- docker/docker-compose
- [orbstack](https://orbstack.dev/download) 轻量级docker 客户端
- 创建一个数据库 ```qa_workspace```
- 运行: ```docker-compose up```

---

## Database Configuration

```yaml
spring:
  datasource:
    url: jdbc:postgresql://127.0.0.1:7432/qa_workspace
    username: postgres
    password: changeit
  jpa:
    show-sql: true
    generate-ddl: true
    database-platform: org.hibernate.dialect.PostgreSQLDialect
    database: postgresql
```

---


## 5. 打包

- **packing**:

```sh
mvn clean package -Dmaven.test.skip=true
cp -rf server/target/*.jar .
```

---

## 运行 **Running**:

```sh
java -jar server-1.0.SNAPSHOT.jar
```
---

## 查看接口文档

***http://localhost:9090/doc.html#/home***

---

## 5. 回顾

- 如何创建MAVEN项目？
- 如何设置数据库？
- 如何运行erupt项目
- 如何打包和运行springboot项目
- Bonus:
  - 如何获取API文档
  - 如何进行添加新用户配置
