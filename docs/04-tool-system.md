# 04 - Tool System

> Claude Code 工具系统

## 概述

Claude Code 内置 60+ 工具，覆盖开发全流程。

## 工具分类

### 1. 文件操作
- `read` - 读取文件内容
- `write` - 写入文件
- `edit` - 编辑文件（精确替换）
- `glob` - 文件模式匹配
- `tree` - 目录结构展示

### 2. 代码执行
- `exec` - 执行 shell 命令
- `process` - 后台进程管理
- `pty` - 伪终端支持

### 3. Git 操作
- `git_status` - 查看状态
- `git_commit` - 提交更改
- `git_push` - 推送到远程
- `git_log` - 查看历史

### 4. 搜索工具
- `grep` - 文本搜索
- `rg` - ripgrep 搜索
- `search_file` - 文件内容搜索

### 5. 网络工具
- `web_search` - 网页搜索
- `web_fetch` - 抓取网页内容
- `browser` - 浏览器自动化

### 6. AI 工具
- `image` - 图像分析
- `tts` - 文本转语音
- `image_generate` - 图像生成

## 工具接口规范

```typescript
interface Tool {
  name: string;
  description: string;
  parameters: JSONSchema;
  execute: (params: any) => Promise<Result>;
}
```

## 工具注册

```typescript
// 动态注册工具
ToolRegistry.register({
  name: 'custom_tool',
  description: '自定义工具',
  parameters: { ... },
  execute: async (params) => { ... }
});
```

## 工具选择策略

Claude 根据以下因素选择工具：
1. 用户意图匹配
2. 工具描述相关性
3. 参数可用性
4. 权限状态

---

*Source: Sathwick's Claude Code Deep Dive*
