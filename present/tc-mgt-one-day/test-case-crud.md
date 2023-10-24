## Features: 测试用例增删改查功能

- 左侧是树状结构，代表模块层级
- 右侧是每个模块对应的测试用例

![](/images/tc-view-list.png)

---

## 测试用例：实现分析

- 实体: TestCase
- 关联: 产品模块配置: Product
- 数据字典: 配置优先级: 数字字典表

---

![](/images/testcase-er.png)

---

## 数据字典需要实现什么？

- 列表/搜索/新增/编辑/删除

---

![](/images/data-dict.png)

---

## 数据字典值页面实现

**一个JAVA文件完成一个增删改查页面**

- 启动系统自动建表
- 表和页面进行对应

---

## UI/JAVA 类说明

![](/images/UI-Simple.png)

---

## 文本类型UI定义

```java
    @EruptField(
            views = @View(
                    title = "代号"
            ),
            edit = @Edit(
                    title = "代号",
                    type = EditType.INPUT, search = @Search, notNull = true,
                    inputType = @InputType
            )
    )
    private String code;

```

---

## Tag类型文本定义

```java
    @EruptField(
            views = @View(title = "分类"),
            edit = @Edit(
                    search = @Search(vague = true),
                    title = "获取可选种类",
                    type = EditType.TAGS,
                    desc = "动态获取可选种类",
                    tagsType = @TagsType(
                            fetchHandler = SqlTagFetchHandler.class,
                            fetchHandlerParams = "select distinct category from master_data where valid=true"
                    ))
    )
    private String category;
```

---

## Boolean 类型

```java
   @EruptField(
            views = @View(
                    title = "是否有效"
            ),
            edit = @Edit(
                    title = "是否有效",
                    type = EditType.BOOLEAN, search = @Search, notNull = true,
                    boolType = @BoolType
            )
    )
    private Boolean valid = true;

```

---

## 配置数据字典菜单

- 类型值: 配置为JAVA类名
- 菜单配置完成

---

## 产品配置模块实现

**产品-模块树形结构UI**

![](/images/product.png)

---

## 产品模块增删改查实现

难点: 实现一个树形结构

---

## 产品模块树形结构: -也是一个文件实现

- 表/字段生成
- 页面自动生成

---

![](/images/product-module.png)

---

## UI: Tree树形结构

![](/images/tree-model.png)

---

## 菜单配置

同数据字典表

---

## 测试用例实现

![](/images/test-case-ui.png)

---


## 代码实例

这个功能本身只要一个JAVA类定义就可以完成:

- JPA: Entity/Table
- Erupt:@Erupt

```java
@Entity
@Erupt(name = "测试用例",
        power = @Power(export = true),
        orderBy = "TestCase.updateTime desc",
        linkTree = @LinkTree(field = "module"))
@Table(name = "test_cases")
public class TestCase extends ModuleValidFlagVo {

}
```

---



## 测试用例UI实现

![](/images/testcase-tree.png)

---

![](/images/ui-types.png)


---

## Choice

```java
    @EruptField(
            views = @View(
                    title = "用例优先级"
            ),
            edit = @Edit(
                    title = "用例优先级",
                    type = EditType.CHOICE,
                    choiceType = @ChoiceType(
                            fetchHandler = SqlChoiceFetchHandler.class,
                            fetchHandlerParams= {"select distinct code " +
                                    "from master_data where category ='priority' and valid =true"}
                    )
            )
    )
    private String priority = "P2";


```

---

## UEDITOR

```java
    @EruptField(
            views = @View(
                    title = "用例前提条件"
            ),
            edit = @Edit(
                    title = "用例前提条件",
                    type = EditType.HTML_EDITOR,
                    htmlEditorType = @HtmlEditorType(HtmlEditorType.Type.UEDITOR)
            )
    )
    private String precondition;

```

DONE!


---

## 菜单配置

1. 运行应用
2. 进行菜单配置,就可以基本完成以上功能

---

![](/images/menu-tc.png)

---

![](/images/menu-tc-table.png)

---

## 配置完成之后展示

测试用例清单:
![](/images/test-case-info.png)

---

![](/images/add-test-case.png)

---

![](/images/product-tree-tc.png)

---

## 小结

1. 这样子开发有什么好处和不好地方？
2. 这样子也太没技术含量了吧？。。。。。。
