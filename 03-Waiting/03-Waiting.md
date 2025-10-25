# 等待清单

**最后更新**: {{date:YYYY-MM-DD HH:mm}}

## 等待项目总览
```dataview
TABLE waiting_for as "等待对象", waiting_until as "等待截止", file.ctime as "创建时间"
FROM "03-Waiting"
WHERE contains(tags, "#waiting")
SORT waiting_until ASC, file.ctime DESC
```

## 按等待对象分类

### 👥 等待他人
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting") AND contains(waiting_for, "人")
SORT waiting_until ASC
```

### 📧 等待邮件
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting") AND contains(waiting_for, "邮件")
SORT waiting_until ASC
```

### 📞 等待电话
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting") AND contains(waiting_for, "电话")
SORT waiting_until ASC
```

### 📦 等待包裹
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting") AND contains(waiting_for, "包裹")
SORT waiting_until ASC
```

### 🏢 等待机构
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting") AND contains(waiting_for, "机构")
SORT waiting_until ASC
```

## 即将到期
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting") AND waiting_until <= date(today) + dur(7 days)
SORT waiting_until ASC
```

## 等待清单管理
- [ ] 定期检查等待项目状态
- [ ] 及时跟进即将到期的项目
- [ ] 更新等待状态
- [ ] 将完成的等待项目归档
