# Dataview查询集合

## 基础查询

### 今日行动清单
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3)), file.ctime DESC
```

### 高优先级行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#priority-high")
SORT file.ctime DESC
```

### 活跃项目列表
```dataview
LIST
FROM "02-Projects"
WHERE contains(tags, "#project") AND contains(tags, "#active")
SORT file.ctime DESC
```

## 情境查询

### 在家可执行的任务
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@home")
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3))
```

### 办公室任务
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@office")
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3))
```

### 电话任务
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@phone")
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3))
```

### 电脑任务
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#@computer")
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3))
```

## 时间查询

### 2分钟内任务
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#time-2min")
SORT file.ctime DESC
```

### 15分钟内任务
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#time-15min")
SORT file.ctime DESC
```

### 1小时内任务
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#time-1hour")
SORT file.ctime DESC
```

## 项目查询

### 项目状态总览
```dataview
TABLE status as "状态", file.ctime as "开始时间", choice(contains(tags, "#priority-high"), "🔴", choice(contains(tags, "#priority-medium"), "🟡", "🟢")) as "优先级"
FROM "02-Projects"
WHERE contains(tags, "#project")
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3)), file.ctime DESC
```

### 高优先级项目
```dataview
LIST
FROM "02-Projects"
WHERE contains(tags, "#project") AND contains(tags, "#priority-high")
SORT file.ctime DESC
```

## 等待查询

### 等待项目总览
```dataview
TABLE waiting_for as "等待对象", waiting_until as "等待截止", file.ctime as "创建时间"
FROM "03-Waiting"
WHERE contains(tags, "#waiting")
SORT waiting_until ASC, file.ctime DESC
```

### 即将到期的等待
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting") AND waiting_until <= date(today) + dur(7 days)
SORT waiting_until ASC
```

## 将来/也许查询

### 高兴趣想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(interest_level, "高")
SORT file.ctime DESC
```

### 学习类想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(idea_type, "学习")
SORT interest_level DESC
```

## 归档查询

### 已完成项目
```dataview
LIST
FROM "06-Archive"
WHERE contains(tags, "#archive") AND contains(archive_reason, "完成")
SORT archive_date DESC
```

### 本月归档
```dataview
LIST
FROM "06-Archive"
WHERE contains(tags, "#archive") AND archive_date >= date(today) - dur(30 days)
SORT archive_date DESC
```

## 综合查询

### 任务总览表
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

### 本周新增项目
```dataview
LIST
FROM "02-Projects"
WHERE contains(tags, "#project") AND file.ctime >= date(today) - dur(7 days)
SORT file.ctime DESC
```

### 待处理收件箱
```dataview
LIST
FROM "00-Inbox"
WHERE contains(tags, "#inbox") AND !completed
SORT file.ctime DESC
```
