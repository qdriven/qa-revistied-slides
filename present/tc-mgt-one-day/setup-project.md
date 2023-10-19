---
theme: eloc
---

## Do it Now!

How to Setup a MAVEN/Springboot/erupts project

---

## Setup Project

- 1. Choose Framework
- 2. Setup Maven Project
- 3. Run Application
- 4. Database Configuration
- 5. Packaging and Run

---

## 1. Choose Framework: erupts

**[erupts](https://www.yuque.com/erupts/erupt)**

*  Almost Zero Frontend coding
*  Backend code controll all the frontend layout and display
*  Very easy to build a just working internal tool system by a JAVA Bean
---


## 2.1 Setup MAVEN Project

MAVEN POM file dependecies/build setting

---

## 3. Run Application

- Application Class to Ready to Run

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

## 4. Database Configuration

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

## 5. Packing and Run

- **packing**:

```sh
mvn clean package -Dmaven.test.skip=true
cp -rf server/target/*.jar .
```

- **Running**:

```sh
java -jar server-1.0.SNAPSHOT.jar
```
---

## 5. Summary

- How to create a MAVEN Project?
- How to Run a erupt/springboot application
- How to Packaging and Run Springboot Application
- Bonus:
  - How to integrate API Docs
  - Erupt Basic Configuration
