我来详细介绍如何使用Obsidian来实践GTD系统。

## Obsidian作为GTD工具的优势

1. **链接功能**：强大的双向链接，便于任务关联
2. **标签系统**：灵活的分类和筛选
3. **模板功能**：快速创建标准化结构
4. **搜索功能**：快速找到相关信息
5. **插件生态**：丰富的扩展功能
6. **本地存储**：数据安全，离线可用

## Obsidian GTD系统架构

### 1. 核心文件夹结构

```
📁 00-Inbox (收件箱)
📁 01-Actions (行动清单)
📁 02-Projects (项目)
📁 03-Waiting (等待清单)
📁 04-Someday (将来/也许)
📁 05-Reference (参考资料)
📁 06-Archive (归档)
📁 07-Templates (模板)
```

### 2. 核心笔记模板

#### 收件箱模板
```markdown
# {{title}}

**收集时间**: {{date}}
**状态**: 待处理
**类型**: 

## 内容
- 

## 下一步行动
- [ ] 

## 标签
#inbox
```

#### 项目模板
```markdown
# {{title}}

**项目状态**: 进行中
**开始日期**: {{date}}
**预计完成**: 
**负责人**: 

## 项目描述
- 

## 下一步行动
- [ ] 

## 相关资源
- 

## 项目笔记
- 

## 标签
#project #active
```

#### 行动清单模板
```markdown
# {{title}}

**行动类型**: 
**情境**: 
**优先级**: 
**预计时间**: 

## 行动描述
- 

## 相关项目
- 

## 完成标准
- [ ] 

## 标签
#action
```

## 实施步骤

### 第一步：设置基础结构

1. **创建文件夹结构**
   - 在Obsidian中创建上述文件夹
   - 设置文件夹图标便于识别

2. **创建核心笔记**
   - `00-Inbox.md` - 收件箱主页面
   - `01-Actions.md` - 行动清单主页面
   - `02-Projects.md` - 项目清单主页面
   - `03-Waiting.md` - 等待清单主页面
   - `04-Someday.md` - 将来/也许清单主页面

### 第二步：建立标签系统

#### 核心标签
```
#inbox - 收件箱
#action - 行动
#project - 项目
#waiting - 等待
#someday - 将来/也许
#reference - 参考资料
#archive - 归档
```

#### 情境标签
```
#@home - 在家
#@office - 办公室
#@phone - 电话
#@computer - 电脑
#@errands - 外出
#@online - 在线
```

#### 优先级标签
```
#priority-high - 高优先级
#priority-medium - 中优先级
#priority-low - 低优先级
```

#### 时间标签
```
#time-2min - 2分钟内
#time-15min - 15分钟内
#time-1hour - 1小时内
#time-long - 长时间任务
```

### 第三步：创建自动化模板

#### 使用Templater插件
```javascript
// 收件箱项目模板
<%*
const title = await tp.system.prompt("项目标题");
const date = tp.date.now("YYYY-MM-DD");
%>
# <% title %>

**收集时间**: <% date %>
**状态**: 待处理
**类型**: 

## 内容
- 

## 下一步行动
- [ ] 

## 标签
#inbox
```

### 第四步：建立工作流程

#### 每日工作流程
1. **晨间回顾**（5分钟）
   - 检查收件箱
   - 查看今日日程
   - 选择3个重要任务

2. **收件箱处理**（10分钟）
   - 清空收件箱
   - 对每个项目进行澄清
   - 分配到相应清单

3. **情境执行**
   - 根据当前情境选择任务
   - 使用标签筛选相关任务

#### 每周回顾流程
1. **项目回顾**
   - 检查所有活跃项目
   - 更新项目状态
   - 确定下一步行动

2. **系统维护**
   - 清理完成的任务
   - 更新标签系统
   - 归档旧文件

### 第五步：使用插件增强功能

#### 推荐插件
1. **Templater** - 模板自动化
2. **Dataview** - 数据查询和展示
3. **Kanban** - 看板视图
4. **Calendar** - 日历集成
5. **Daily Notes** - 每日笔记
6. **Tag Wrangler** - 标签管理
7. **QuickAdd** - 快速添加功能

#### Dataview查询示例
```dataview
TABLE file.ctime as "创建时间", status as "状态"
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed
SORT file.ctime DESC
```

### 第六步：建立自动化查询

#### 今日行动清单
```dataview
LIST
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed
SORT priority DESC
```

#### 按情境分类的行动
```dataview
TABLE WITHOUT ID
  choice(contains(tags, "#@home"), "🏠", choice(contains(tags, "#@office"), "🏢", choice(contains(tags, "#@phone"), "📞", "💻"))) as "情境",
  file.link as "任务",
  choice(contains(tags, "#priority-high"), "🔴", choice(contains(tags, "#priority-medium"), "🟡", "🟢")) as "优先级"
FROM "01-Actions"
WHERE contains(tags, "#action") AND !completed
SORT priority DESC
```

#### 项目状态总览
```dataview
TABLE status as "状态", file.ctime as "开始时间"
FROM "02-Projects"
WHERE contains(tags, "#project")
SORT status, file.ctime DESC
```

### 第七步：建立定期回顾系统

#### 每周回顾模板
```markdown
# 周回顾 - {{date:YYYY-MM-DD}}

## 本周完成
- [ ] 

## 本周未完成
- [ ] 

## 下周重点
- [ ] 

## 项目更新
- [ ] 

## 系统改进
- [ ] 
```

#### 每月回顾模板
```markdown
# 月回顾 - {{date:YYYY-MM}}

## 本月成就
- [ ] 

## 本月挑战
- [ ] 

## 下月目标
- [ ] 

## 系统优化
- [ ] 
```

## 高级技巧

### 1. 使用MOCs（Maps of Content）
创建主题地图，连接相关项目：
```markdown
# 工作主题地图

## 活跃项目
- [[项目A]]
- [[项目B]]

## 相关资源
- [[参考资料1]]
- [[参考资料2]]
```

### 2. 建立工作流程自动化
使用QuickAdd插件创建快速添加功能：
- 快速添加收件箱项目
- 快速创建项目
- 快速添加行动

### 3. 使用看板视图
安装Kanban插件，创建项目看板：
- 待办
- 进行中
- 完成

### 4. 集成日历
使用Calendar插件，将时间敏感任务与日历集成。

## 最佳实践建议

1. **保持简单**：不要过度复杂化系统
2. **定期清理**：每周清理完成的任务
3. **标签一致**：建立标签使用规范
4. **备份重要**：定期备份Obsidian库
5. **持续改进**：根据使用情况调整系统

通过这种方式，Obsidian可以成为一个强大的GTD系统，帮助你更好地管理任务、项目和目标，提高个人生产力。