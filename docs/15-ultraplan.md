# 15 - ULTRAPLAN Remote Planning

> Claude Code ULTRAPLAN 远程规划

## 概述

ULTRAPLAN 允许 Claude 进行复杂的长期规划。

## 工作原理

- Claude 生成详细计划
- 用户确认计划
- 逐步执行
- 定期汇报

### 示例
```
任务： 重构整个支付系统

ULTRAPLAN:
├── Phase 1: 分析现有代码 (2天)
├── Phase 2: 设计新架构 (1天)
├── Phase 3: 实现核心模块 (3天)
├── Phase 4: 迁移数据 (1天)
├── Phase 5: 测试和部署 (2天)

```

## 优势
- 处理大型任务
- 用户可见进度
- 可调整计划
- 上下文管理优化

## 配置

```json
{
  "ultraplan": {
    "enabled": true,
    "maxPhases": 10,
    "checkInFrequency": "1h"
  }
}
```

---

*Source: Sathwick's Claude Code Deep Dive*
