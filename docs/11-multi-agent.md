# 11 - Multi-Agent Architecture

> Claude Code 多 Agent 架构

## 设计理念

Claude Code 支持多 Agent 并行协作，处理复杂任务。

## Agent 类型

### 1. 主 Agent
- 用户直接交互
- 任务分解
- 结果整合

### 2. 子 Agent
- 独立任务执行
- 并行处理
- 结果汇报

### 3. 专用 Agent
- 特定领域专家
- 代码审查
- 测试生成

## 协作模式

### 并行执行
```
Main Agent
    │
    ├─→ Agent 1: 文件分析
    ├─→ Agent 2: 测试生成
    └─→ Agent 3: 文档更新
    │
    ▼
Result Aggregation
```

### 流水线执行
```
Agent 1 → Agent 2 → Agent 3 → Final
(解析)   (转换)   (验证)   (输出)
```

## 通信机制

### 任务分发
```typescript
interface TaskDispatch {
  taskId: string;
  agentType: string;
  input: any;
  priority: number;
}
```

### 结果收集
```typescript
interface ResultCollection {
  taskId: string;
  status: 'pending' | 'completed' | 'failed';
  result?: any;
  error?: string;
}
```

## 协调器

协调器负责：
1. 任务分解
2. Agent 调度
3. 结果整合
4. 错误处理

---

*Source: Sathwick's Claude Code Deep Dive*
