# 07 - Commands System

> Claude Code 命令系统

## 命令类型

### 1. 斜杠命令
- `/help` - 帮助信息
- `/clear` - 清除对话
- `/compact` - 压缩上下文
- `/cost` - 显示成本
- `/model` - 切换模型
- `/permissions` - 管理权限
- `/review` - 代码审查
- `/status` - 显示状态

### 2. 快捷命令
- `!!` - 重复上一条命令
- `!` - 执行 shell 命令

### 3. 自然语言命令
直接用自然语言描述任务，Claude 会自动识别并执行。

## 命令执行流程

```
User Input → Parser → Command Matcher → Handler → Executor
```

## 自定义命令

用户可以定义自定义命令：

```json
{
  "customCommands": {
    "/test": {
      "description": "运行测试",
      "action": "npm test"
    }
  }
}
```

## 命令历史

- 使用上下箭头浏览历史命令
- 支持模糊搜索历史记录

---

*Source: Sathwick's Claude Code Deep Dive*
