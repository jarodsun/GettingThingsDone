# 行动清单

**最后更新**: {{date:YYYY-MM-DD HH:mm}}

## 今日重点行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#priority-high")
SORT file.ctime DESC
```

## 按情境分类的行动

### 🏠 在家行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@home")
SORT file.ctime DESC
```

### 🏢 办公室行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@office")
SORT file.ctime DESC
```

### 📞 电话行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@phone")
SORT file.ctime DESC
```

### 💻 电脑行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@computer")
SORT file.ctime DESC
```

### 🚶 外出行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@errands")
SORT file.ctime DESC
```

### 🌐 在线行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@online")
SORT file.ctime DESC
```

## 按时间分类的行动

### ⚡ 2分钟内行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#time-2min")
SORT file.ctime DESC
```

### ⏰ 15分钟内行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#time-15min")
SORT file.ctime DESC
```

### ⏳ 1小时内行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#time-1hour")
SORT file.ctime DESC
```

## 所有行动总览
```dataview
TABLE WITHOUT ID
  choice(contains(tags, "#@home"), "🏠", choice(contains(tags, "#@office"), "🏢", choice(contains(tags, "#@phone"), "📞", choice(contains(tags, "#@computer"), "💻", choice(contains(tags, "#@errands"), "🚶", "🌐"))))) as "情境",
  file.link as "任务",
  choice(contains(tags, "#priority-high"), "🔴", choice(contains(tags, "#priority-medium"), "🟡", "🟢")) as "优先级",
  choice(contains(tags, "#time-2min"), "⚡", choice(contains(tags, "#time-15min"), "⏰", choice(contains(tags, "#time-1hour"), "⏳", "⏰"))) as "时间"
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3)), file.ctime DESC
```
