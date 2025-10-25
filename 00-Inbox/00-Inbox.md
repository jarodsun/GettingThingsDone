# 收件箱

**最后更新**: {{date:YYYY-MM-DD HH:mm}}

## 快速添加
- [ ] 

## 待处理项目
```dataview
LIST
FROM "00-Inbox"
WHERE contains(tags, "#inbox") AND !completed
SORT file.ctime DESC
```

## 处理流程
1. **收集** - 将所有想法、任务、承诺记录在这里
2. **澄清** - 对每个项目进行判断：这是什么？需要行动吗？
3. **组织** - 将澄清后的项目分配到相应清单
4. **执行** - 根据情境选择任务执行

## 标签说明
- `#inbox` - 收件箱项目
- `#action` - 需要行动
- `#project` - 项目
- `#waiting` - 等待
- `#someday` - 将来/也许
- `#reference` - 参考资料

## 情境标签
- `#@home` - 在家
- `#@office` - 办公室
- `#@phone` - 电话
- `#@computer` - 电脑
- `#@errands` - 外出
- `#@online` - 在线

## 优先级标签
- `#priority-high` - 高优先级
- `#priority-medium` - 中优先级
- `#priority-low` - 低优先级

## 时间标签
- `#time-2min` - 2分钟内
- `#time-15min` - 15分钟内
- `#time-1hour` - 1小时内
- `#time-long` - 长时间任务
