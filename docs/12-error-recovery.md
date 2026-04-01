# 12 - Error Recovery

> Claude Code 错误恢复机制

## 错误类型

### 1. 工具执行错误
- 命令失败
- 文件操作失败
- 权限拒绝

### 2. API 错误
- 网络超时
- Rate limit
- 认证失败

### 3. 上下文错误
- Token 超限
- 上下文损坏
- 状态不一致

## 恢复策略

### 自动重试
```typescript
interface RetryPolicy {
  maxAttempts: number;
  backoff: 'exponential' | 'linear' | 'fixed';
  retryableErrors: string[];
}
```

### 降级处理
- 工具失败 → 回退到替代方案
- API 失败 → 缓存响应
- 上下文超限 → 自动压缩

### 用户干预
- 权限请求 → 等待用户确认
- 模糊任务 → 请求澄清
- 不可恢复 → 报告错误

## 错误日志

```
.claude/logs/
├── error-2026-04-01.log
├── warning-2026-04-01.log
└── debug-2026-04-01.log
```

## 最佳实践

1. **明确错误**: 提供具体错误信息
2. **建议方案**: 给出可能的解决方案
3. **保留上下文**: 恢复后保留之前的工作状态

---

*Source: Sathwick's Claude Code Deep Dive*
