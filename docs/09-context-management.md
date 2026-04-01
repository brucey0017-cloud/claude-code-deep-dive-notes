# 09 - Context Management

> Claude Code 上下文管理

## 挑战

Claude 的上下文窗口有限，Claude Code 需要智能管理上下文。

## 上下文层次

### 1. 系统上下文
- 环境信息
- 可用工具列表
- 权限配置

### 2. 项目上下文
- 目录结构
- Git 状态
- 依赖关系
- 配置文件

### 3. 会话上下文
- 对话历史
- 当前任务
- 中间结果

### 4. 文件上下文
- 文件内容
- 符号定义
- 导入关系

## 压缩策略

### 自动压缩
- 当上下文接近限制时自动触发
- 保留关键信息
- 生成摘要

### 手动压缩
- `/compact` 命令
- 选择性保留

### 滑动窗口
- 保留最近 N 条消息
- 重要消息标记为永久

## Token 优化

```typescript
interface TokenUsage {
  system: number;    // 系统提示
  context: number;   // 项目上下文
  history: number;   // 对话历史
  response: number;  // Claude 响应
}
```

## 最佳实践

1. **定期压缩**: 使用 `/compact` 保持上下文精简
2. **明确任务**: 一次只做一件事
3. **提供上下文**: 明确指出相关文件

---

*Source: Sathwick's Claude Code Deep Dive*
