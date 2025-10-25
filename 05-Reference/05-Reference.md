# 参考资料

**最后更新**: {{date:YYYY-MM-DD HH:mm}}

## 参考资料总览
```dataview
TABLE file.ctime as "创建时间", reference_type as "类型"
FROM "05-Reference"
WHERE contains(tags, "#reference")
SORT file.ctime DESC
```

## 按类型分类

### 📚 文档资料
```dataview
LIST
FROM "05-Reference"
WHERE contains(tags, "#reference") AND contains(reference_type, "文档")
SORT file.ctime DESC
```

### 🔗 链接资料
```dataview
LIST
FROM "05-Reference"
WHERE contains(tags, "#reference") AND contains(reference_type, "链接")
SORT file.ctime DESC
```

### 📝 笔记资料
```dataview
LIST
FROM "05-Reference"
WHERE contains(tags, "#reference") AND contains(reference_type, "笔记")
SORT file.ctime DESC
```

### 🖼️ 图片资料
```dataview
LIST
FROM "05-Reference"
WHERE contains(tags, "#reference") AND contains(reference_type, "图片")
SORT file.ctime DESC
```

### 📊 数据资料
```dataview
LIST
FROM "05-Reference"
WHERE contains(tags, "#reference") AND contains(reference_type, "数据")
SORT file.ctime DESC
```

## 参考资料管理
- [ ] 定期整理参考资料
- [ ] 删除过时的资料
- [ ] 建立清晰的分类体系
- [ ] 确保资料的可访问性
