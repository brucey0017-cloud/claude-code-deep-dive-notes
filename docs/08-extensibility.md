# 08 - Extensibility

> Claude Code 扩展性设计

## 扩展机制

### 1. MCP (Model Context Protocol)
- 标准化的工具协议
- 支持第三方集成
- 跨平台兼容

### 2. 自定义工具
```typescript
// 注册自定义工具
claude.tools.register({
  name: 'my_tool',
  description: '我的自定义工具',
  parameters: {
    type: 'object',
    properties: {
      input: { type: 'string' }
    }
  },
  handler: async (params) => {
    // 工具逻辑
    return { result: 'success' };
  }
});
```

### 3. 插件系统
- 安装社区插件
- 创建私有插件
- 热加载支持

## 扩展点

| 扩展点 | 用途 |
|--------|------|
| Tools | 添加新工具 |
| Commands | 自定义命令 |
| Renderers | 自定义输出渲染 |
| Parsers | 自定义输入解析 |

## 配置

```json
{
  "extensions": {
    "directory": "~/.claude/extensions",
    "autoLoad": true,
    "allowed": ["official", "community", "private"]
  }
}
```

---

*Source: Sathwick's Claude Code Deep Dive*
