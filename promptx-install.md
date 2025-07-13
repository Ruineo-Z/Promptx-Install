# Promptx Install

本文档用于介绍Promptx MCP的安装方法

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

## 各平台详细教程

下方各文档为当前主流AI Coding工具安装的详细教程
❗默认都是用 beta 如果有特殊需要，只需更换版本即可

支持的平台：
- [Augment](./promptx-augment.md) - VSCode插件模式
- [Cursor](./promptx-cursor.md) - 支持Windows和Mac系统
- [Claude Code](./promptx-claude-code.md) - 终端命令行模式
- [Trae](./promptx-trae.md) - MCP服务器配置
- [Cline](./promptx-cline.md) - VSCode插件模式
- Roo Code - (链接与Trae相同，可能是重复项)

---

> 原始链接: https://kqntszks7k4.feishu.cn/wiki/QoJDwGSiSiMXzskwaArcax0JnMd
> 
> 获取时间: 2025-01-13
