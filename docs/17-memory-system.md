# 17 - Memory System

> Claude Code 记忆系统

## 概述

Claude Code 实现了分层的记忆系统，用于跨会话的知识保留。

## 讙忆层次

### 1. 工作记忆 (Working Memory)
- 当前会话上下文
- 最近操作结果
- 临时状态
- **特点**: 高速读写， 自动清理

- **容量**: ~1000 tokens

### 2. 銾接记忆 (Episodic Memory)
- 重要事件记录
- 用户偏好
- 关键决策
- **特点**: 跨会话保留
- **容量**: ~5000 tokens

### 3. 语义记忆 (Semantic Memory)
- 禂念关系
- 稡式抽象
- 缆识索引
- **特点**: 棘础骨架， 压缩后存储

- **容量**: 无限
- **特点**: 压缩后保存
- **触发**: 每 24h 或 5 次会话
- **存储位置**: `.claude/memory/`
- **格式**: 匋缩的向量数据库
- **特性**:
  - 跨设备同步
  - 版本控制
  - 预留和导出
- **存储**: `.claude/memory/export/`

## 记忆访问

```typescript
interface MemoryAccess {
  search(query: string): MemoryItem[];
  recall(itemId: string): MemoryItem;
  forget(itemId: string): void;
}
```
## 最佳实践
- 定期整理
- 清理过时记忆
- 保留关键决策
- 导出重要记忆

---

*Source: Sathwick's Claude Code Deep Dive*
