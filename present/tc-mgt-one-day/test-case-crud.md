## Features: 测试用例增删改查功能

- 左侧是树状结构，代表模块层级
- 右侧是每个模块对应的测试用例

![](/images/tc-view-list.png)

---

![](/images/tc-fields.png)

---

## 实现细节

这个功能本身只要一个JAVA类定义就可以完成:

- JPA: Entity/Table
- Erupt:@Erupt

```java
@Entity
@Erupt(name = "测试用例",
        power = @Power(export = true),
        orderBy = "TestCase.updateTime desc",
        linkTree = @LinkTree(field = "product"))
@Table(name = "test_cases")
public class TestCase extends ProductModuleValidFlagVo {

}
```

---

## Define your fields:  text

```java

    @EruptField(
            views = @View(
                    title = "用例ID"
            )
    )
    private String uuid;
```

---

## Define your fields:  dropdown or choice

```java
    @EruptField(
            views = @View(
                    title = "用例优先级"
            ),
            edit = @Edit(
                    title = "用例优先级",
                    type = EditType.TAGS,
                    tagsType = @TagsType(
                            fetchHandler = SqlTagFetchHandler.class,
                            fetchHandlerParams = "select distinct priority from  test_cases"
                    )
            )
    )
    private String priority = "P2";

```

---

## Define your fields:  UEDITOR

```java
    @EruptField(
            views = @View(
                    title = "测试步骤"
            ),
            edit = @Edit(
                    title = "测试步骤",
                    type = EditType.HTML_EDITOR,
                    htmlEditorType = @HtmlEditorType(HtmlEditorType.Type.UEDITOR)
            )
    )
    private String steps;

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

1. Model 
2. Field
3. 菜单配置
