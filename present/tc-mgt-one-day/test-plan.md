## Test Run/Test Plan

Define Test Plan Scope
- Time Period
- Testing Scope: Test Cases/Test Sceanrios
- Owner

How to Combine Test Case/Test Scenario?

---

![](/images/test-plans.png)

---

## key takeaway

**RowOperation**

```java
@Entity
@Table(name = "test_runs")
@Erupt(name = "测试执行计划",
        power = @Power(importable = true, export = true),
        tree = @Tree(id = "id", label = "name", pid = "parent.id")
        ,rowOperation = {@RowOperation(
                title = "生成执行测试用例",
                operationHandler = GenerateTestRecordHandler.class)}
)

public class TestRun extends MetaModel {
}
```
