# Upload/Import Test Cases

Test Cases in Excel is very common, so support import excel as Test Cases.

---

## 一个上传文件页面

- Model Class: Same As Test Case Model
- Fields: Same as Test Case Field iin Model

---

## 菜单配置/展示

![](/images/upload-tc.png)

---

## 如何导入呢？

文件上传了不代表直接导入, 那要如何导入呢？

***DataProxy*** in erupts

```java
@PreDataProxy(value = UploadFileDataProxy.class)
```

---

## 如何处理Excel呢？

```java
 excelReadWriter.readExcel(filePath, TestCaseDTO.class);
```

---

## 具体实现过程

- DataProxy: See Source code
- Excel: See Source code

---

