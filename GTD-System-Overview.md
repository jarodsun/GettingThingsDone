# GTD系统总览

**最后更新**: 2025-10-25 12:20

## 系统状态

### 📥 收件箱状态
```dataview
LIST
FROM "00-Inbox"
WHERE file.name != "00-Inbox"
SORT file.ctime DESC
```

### ✅ 今日行动
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed AND contains(tags, "#priority-high")
SORT file.ctime DESC
```

### 📋 活跃项目
```dataview
LIST
FROM "02-Projects"
WHERE contains(tags, "#project") AND contains(tags, "#active")
SORT choice(contains(tags, "#priority-high"), 1, choice(contains(tags, "#priority-medium"), 2, 3)), file.ctime DESC
```

### ⏳ 等待项目
```dataview
LIST
FROM "03-Waiting"
WHERE contains(tags, "#waiting")
SORT waiting_until ASC
```

### 💡 将来想法
```dataview
LIST
FROM "04-Someday"
WHERE contains(tags, "#someday") AND contains(interest_level, "高")
SORT file.ctime DESC
```

## 快速导航

- [[00-Inbox/00-Inbox|📥 收件箱]]
- [[01-Actions/01-Actions|✅ 行动清单]]
- [[02-Projects/02-Projects|📋 项目清单]]
- [[03-Waiting/03-Waiting|⏳ 等待清单]]
- [[04-Someday/04-Someday|💡 将来/也许]]
- [[05-Reference/05-Reference|📚 参考资料]]
- [[06-Archive/06-Archive|🗄️ 归档]]

## 工作流程

### 每日流程
1. **晨间回顾**（5分钟）
   - 检查收件箱
   - 查看今日重点任务
   - 选择3个重要任务

2. **收件箱处理**（10分钟）
   - 清空收件箱
   - 对每个项目进行澄清
   - 分配到相应清单

3. **情境执行**
   - 根据当前情境选择任务
   - 使用标签筛选相关任务

### 每周流程
1. **项目回顾**
   - 检查所有活跃项目
   - 更新项目状态
   - 确定下一步行动

2. **系统维护**
   - 清理完成的任务
   - 更新标签系统
   - 归档旧文件

## 标签系统

### 核心标签
- `#inbox` - 收件箱
- `#action` - 行动
- `#project` - 项目
- `#waiting` - 等待
- `#someday` - 将来/也许
- `#reference` - 参考资料
- `#archive` - 归档

### 情境标签
- `#at_home` - 在家
- `#at_office` - 办公室
- `#at_phone` - 电话
- `#at_computer` - 电脑
- `#at_errands` - 外出
- `#at_online` - 在线

### 优先级标签
- `#priority-high` - 高优先级
- `#priority-medium` - 中优先级
- `#priority-low` - 低优先级

### 时间标签
- `#time-2min` - 2分钟内
- `#time-15min` - 15分钟内
- `#time-1hour` - 1小时内
- `#time-long` - 长时间任务

## 使用说明

1. **收集** - 将所有想法、任务、承诺记录在收件箱
2. **澄清** - 对每个项目进行判断：这是什么？需要行动吗？
3. **组织** - 将澄清后的项目分配到相应清单
4. **回顾** - 定期检查系统，确保完整性
5. **执行** - 根据情境选择任务执行

## 最佳实践

1. **保持简单** - 不要过度复杂化系统
2. **定期清理** - 每周清理完成的任务
3. **标签一致** - 建立标签使用规范
4. **备份重要** - 定期备份Obsidian库
5. **持续改进** - 根据使用情况调整系统
