# 归档

**最后更新**: {{date:YYYY-MM-DD HH:mm}}

## 归档项目总览
```dataview
TABLE archive_date as "归档日期", archive_reason as "归档原因"
FROM "06-Archive"
WHERE contains(tags, "#archive")
SORT archive_date DESC
```

## 按归档原因分类

### ✅ 已完成
```dataview
LIST
FROM "06-Archive"
WHERE contains(tags, "#archive") AND contains(archive_reason, "完成")
SORT archive_date DESC
```

### ❌ 已取消
```dataview
LIST
FROM "06-Archive"
WHERE contains(tags, "#archive") AND contains(archive_reason, "取消")
SORT archive_date DESC
```

### 📅 已过期
```dataview
LIST
FROM "06-Archive"
WHERE contains(tags, "#archive") AND contains(archive_reason, "过期")
SORT archive_date DESC
```

### 🔄 已转移
```dataview
LIST
FROM "06-Archive"
WHERE contains(tags, "#archive") AND contains(archive_reason, "转移")
SORT archive_date DESC
```

## 归档管理
- [ ] 定期清理归档文件
- [ ] 保持归档文件的完整性
- [ ] 建立归档索引
- [ ] 定期备份归档数据
