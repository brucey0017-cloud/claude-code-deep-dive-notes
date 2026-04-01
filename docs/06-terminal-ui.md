# 06 - Terminal UI

> Claude Code 终端 UI 实现

## 核心技术

Claude Code 使用 **自定义 React Reconciler** 将组件渲染到终端。

### React to Terminal

```
┌─────────────────────────────────────┐
│   Standard React                    │
│   React DOM → Browser DOM           │
└─────────────────────────────────────┘
                │
                ▼
┌─────────────────────────────────────┐
│   Claude Code React                 │
│   Custom Reconciler → Terminal      │
└─────────────────────────────────────┘
```

## UI 组件

### 主要组件
- `ChatWindow` - 主对话窗口
- `ToolOutput` - 工具输出展示
- `PermissionPrompt` - 权限请求弹窗
- `ProgressBar` - 进度条
- `StatusIndicator` - 状态指示器

## 渲染特性

### 响应式更新
- 工具输出实时渲染
- 流式 API 响应展示
- 状态变化即时反映

### 终端适配
- ANSI 颜色支持
- 光标控制
- 多种布局模式

## 示例代码

```typescript
const TerminalApp = () => {
  return (
    <Box flexDirection="column">
      <Header />
      <ChatWindow messages={messages} />
      <InputBox onSubmit={handleSubmit} />
    </Box>
  );
};
```

## 性能优化

1. **虚拟滚动**: 长对话历史按需渲染
2. **增量更新**: 仅重绘变化部分
3. **缓冲管理**: 控制渲染频率

---

*Source: Sathwick's Claude Code Deep Dive*
