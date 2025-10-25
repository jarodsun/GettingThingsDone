# 将来/也许清单

**最后更新**: {{date:YYYY-MM-DD HH:mm}}

## 所有想法总览
```dataview
TABLE interest_level as "兴趣程度", file.ctime as "创建时间"
FROM "04-Someday"
WHERE contains(tags, "#someday")
SORT interest_level DESC, file.ctime DESC
```

## 按兴趣程度分类

### 🔥 高兴趣
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(interest_level, "高")
SORT file.ctime DESC
```

### 🟡 中兴趣
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(interest_level, "中")
SORT file.ctime DESC
```

### 🟢 低兴趣
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(interest_level, "低")
SORT file.ctime DESC
```

## 按类型分类

### 🎯 学习想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(idea_type, "学习")
SORT interest_level DESC
```

### 🏠 生活想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(idea_type, "生活")
SORT interest_level DESC
```

### 💼 工作想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(idea_type, "工作")
SORT interest_level DESC
```

### 🎨 创意想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(idea_type, "创意")
SORT interest_level DESC
```

### 🏃 健康想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(idea_type, "健康")
SORT interest_level DESC
```

## 将来/也许清单管理
- [ ] 定期回顾想法列表
- [ ] 评估想法的可行性
- [ ] 将成熟的想法转为项目
- [ ] 删除不再感兴趣的想法
