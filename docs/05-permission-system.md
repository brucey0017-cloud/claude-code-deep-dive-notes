# 05 - Permission System

> Claude Code 权限系统

## 设计理念

Claude Code 实现了细粒度的权限控制，确保 AI Agent 在安全边界内操作。

## 权限模型

### Allow/Deny 规则

```yaml
permissions:
  allow:
    - read: ["src/**", "docs/**"]
    - write: ["src/**"]
    - exec: ["npm", "git"]
  
  deny:
    - read: [".env", "**/secrets/**"]
    - write: [".git/**"]
    - exec: ["rm -rf", "sudo"]
```

### 权限层级

1. **Global**: 全局配置
2. **Project**: 项目级配置
3. **Session**: 会话级临时授权

## 权限检查流程

```
Tool Request
    │
    ▼
┌─────────────┐
│ Rule Match  │ ← 匹配 allow/deny 规则
└─────────────┘
    │
    ├─ Allow → 执行
    │
    ├─ Deny  → 拒绝
    │
    └─ Unknown → 请求用户确认
```

## 沙箱机制

### 执行沙箱
- 隔离的进程环境
- 限制文件系统访问
- 网络访问控制

### 代码沙箱
- 受限的 Node.js 环境
- 禁用危险 API
- 超时保护

## 用户交互

### 权限请求提示

```
⚠️ Claude 想要执行：
   rm -rf node_modules

[y] 允许一次
[a] 总是允许
[d] 拒绝
[n] 永不允计
```

### 权限审计

所有权限决策都会记录到审计日志：

```json
{
  "timestamp": "2026-04-01T08:00:00Z",
  "tool": "exec",
  "action": "rm -rf node_modules",
  "decision": "denied",
  "reason": "user_rejected"
}
```

## 配置文件

权限配置存储在 `.claude/permissions.yml`

---

*Source: Sathwick's Claude Code Deep Dive*
