## Test Scenarios

Test Case Collection for different purposes

---

## Model Class with JPA

```java
    @JoinTable(name = "test_scenario_cases",
            joinColumns = @JoinColumn(name = "test_scenario_id", referencedColumnName = "id"),
            inverseJoinColumns = @JoinColumn(name = "test_case_id", referencedColumnName = "id"))
    @ManyToMany(fetch = FetchType.EAGER)
    @EruptField(
            views = @View(title = "包含用例"),
            edit = @Edit(
                    title = "包含用例",
                    type = EditType.TAB_TABLE_REFER
            )
    )
    private Set<TestCase> testCases;
```

---

## Done! Really?

Not Really, but configure the Menu.

---

![](/images/test-scenarios.png)


