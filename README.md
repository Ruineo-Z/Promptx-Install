# Promptx MCP Install

本文档用于介绍Promptx MCP的安装方法



## 各平台详细教程

下方各文档为当前主流AI Coding工具安装的详细教程
❗默认都是用 beta 如果有特殊需要，只需更换版本即可

- [Augment](./Augment/promptx-augment.md)
- [Cursor](./Cursor/promptx-cursor.md)
- [Claude Code](./Claude%20Code/promptx-claude-code.md)
- [Trae](./Trae/promptx-trae.md)
- [Cline](./Cline/promptx-cline.md)
- [Roo Code](./Roo%20Code/promptx-roo-code.md)



## 🚀 一键启动 快速使用

### ⚙️ 快速配置

**📋 前置要求：** 确保已安装 Node.js（建议 v18 及以上版本）

打开配置文件，将下面的 promptx 配置代码复制进去。这是最简单的 **零配置模式**，PromptX 会自动为您处理一切。

**本地模式，强烈推荐**

```json
{
  "mcpServers": {
    "promptx": {
      "command": "npx",
      "args": [
        "-y",
        "-f",
        "--registry",
        "https://registry.npmjs.org",
        "dpml-prompt@beta",
        "mcp-server"
      ]
    }
  }
}
```

**💡 提示：** 配置中特意指定了官方镜像源 registry.npmjs.org，这可以避免因使用非官方镜像导致的安装问题。如果您发现安装很慢，建议使用代理工具加速，而不是切换到其他镜像源。

**配置参数说明：**
- `command`: 指定使用 npx 运行 promptx 服务（npx 随 Node.js 自动安装）
- `args`: 启动参数配置列表
  - `-y`: 自动确认
  - `-f`: 强制刷新缓存
  - `--registry`: 指定镜像源
  - `https://registry.npmjs.org`: 使用官方镜像
  - `dpml-prompt@beta`: 使用稳定测试版
  - `mcp-server`: 启动服务

### Http模式

使用Http模式，需要在本地启动对应服务，后续文档中将省略这一步教程

**启动服务命令**

```bash
# 启动服务
npx -f -y dpml-prompt@beta mcp-server --transport http --port 3000

# 检查服务状态
curl http://localhost:3000/health
```

`/health`响应200，表示服务成功启动

**MCP安装命令**

```json
{
  "servers": {
    "promptx": {
      "type": "http",
      "url": "http://localhost:3000/mcp"
    }
  }
}
```

## 📦 版本说明

| 🏷️ **渠道** | 📊 **稳定性** | 🎯 **适用场景** | 📦 **配置** |
|---------|---------|------------|---------|
| **alpha** | 内测版 ⚡ | 尝鲜最新功能，参与测试反馈 | `dpml-prompt@alpha` |
| **beta** | 公测版 🧪 | 功能相对稳定，适合日常使用 | `dpml-prompt@beta` |
| **latest** | 正式版 ✅ | 生产环境，追求最高稳定性 | `dpml-prompt@latest` |
