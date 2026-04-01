# 10 - State Management

> Claude Code 状态管理

## 状态类型

### 1. 会话状态
- 当前对话 ID
- 消息历史
- 用户偏好
- 任务队列

### 2. 项目状态
- 工作目录
- Git 分支
- 未提交更改
- 构建状态

### 3. 工具状态
- 已加载工具
- 工具缓存
- 权限状态

## 状态持久化

### 存储位置
```
.claude/
├── sessions/
│   └── <session-id>.json
├── cache/
│   └── <cache-key>.json
└── config/
    └── preferences.json
```

### 状态恢复
- 会话重启后恢复状态
- 跨设备同步（可选）

## 状态同步

```typescript
interface StateSync {
  local: LocalState;
  remote?: RemoteState;
  
  merge(): MergedState;
  push(): void;
  pull(): void;
}
```

## 状态隔离

不同项目/会话的状态相互隔离：
- 独立的会话历史
- 独立的工具缓存
- 独立的权限配置

---

*Source: Sathwick's Claude Code Deep Dive*
