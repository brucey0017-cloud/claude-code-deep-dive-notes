# 16 - Coordinator Orchestrator

> Claude Code Coordinator 编排器

## 概述

Coordinator 是多 Agent 协作的核心组件。

## 职责

- 任务分解
- Agent 调度
- 结果整合
- 错误处理
- 进度报告

## 工作流程
- 分配给合适的 Agent
- 监控执行状态
- 收集并整合结果
- 失败时触发重试

```

┌─────────────────┐
│                 │
│  Coordinator    │
│                 │
└─────────────────┘
        │
    ┌───┴───┴───┐
    │       │       │
    ▼       ▼       ▼
 Agent1  Agent2  Agent3
```

## 配置

```json
{
  "coordinator": {
    maxParallelAgents: 5,
    timeout: 300000,
    retryPolicy: "exponential"
  }
}
```

---

*Source: Sathwick's Claude Code Deep Dive*
