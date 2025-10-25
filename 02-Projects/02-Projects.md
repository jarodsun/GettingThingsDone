# 项目清单

**最后更新**: {{date:YYYY-MM-DD HH:mm}}

## 活跃项目
```dataview
TABLE status as "状态", file.ctime as "开始时间", choice(contains(tags, "#priority-high"), "🔴", choice(contains(tags, "#priority-medium"), "🟡", "🟢")) as "优先级"
FROM "02-Projects"
WHERE contains(tags, "#project") AND contains(tags, "#active")
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3)), file.ctime DESC
```

## 项目状态总览
```dataview
TABLE status as "状态", file.ctime as "开始时间"
FROM "02-Projects"
WHERE contains(tags, "#project")
SORT status, file.ctime DESC
```

## 项目分类

### 🔴 高优先级项目
```dataview
LIST
FROM "02-Projects"
WHERE contains(tags, "#project") AND contains(tags, "#priority-high")
SORT file.ctime DESC
```

### 🟡 中优先级项目
```dataview
LIST
FROM "02-Projects"
WHERE contains(tags, "#project") AND contains(tags, "#priority-medium")
SORT file.ctime DESC
```

### 🟢 低优先级项目
```dataview
LIST
FROM "02-Projects"
WHERE contains(tags, "#project") AND contains(tags, "#priority-low")
SORT file.ctime DESC
```

## 项目状态说明
- **进行中** - 正在执行的项目
- **暂停** - 暂时停止的项目
- **等待** - 等待外部条件的项目
- **完成** - 已完成的项目
- **取消** - 已取消的项目

## 项目回顾检查清单
- [ ] 每个项目都有明确的下一步行动
- [ ] 项目目标清晰明确
- [ ] 项目截止日期合理
- [ ] 项目资源充足
- [ ] 项目与长期目标一致
