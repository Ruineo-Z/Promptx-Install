# Claude Code

本文档用于介绍如何在Claude Code中安装Promptx MCP

## 安装命令

### 本地模式(推荐)

```json
claude mcp add-json promptx '{
    "type": "stdio",
    "command": "npx",
    "args": [
        "-f",
        "-y",
        "--registry",
        "https://registry.npmjs.org",
        "dpml-prompt@beta",
        "mcp-server"
    ]
}'
```

### Http模式

```bash
claude mcp add --transport http promptx http://localhost:3000/mcp
```

## 流程图

### 1. 安装MCP

#### 1.1 Windows

##### 1.1.1 本地模式(推荐)

❗️暂不支持

##### 1.1.2 Http模式

![Http模式安装](./Imgs/img-1.png)

#### 1.2. Mac

##### 1.2.1 本地模式(推荐)

![本地模式安装](./Imgs/img-6.png)

##### 2.1.2 Http模式

![Http模式安装](./Imgs/img-7.png)

### 2 检查MCP是否可用

#### 2.2.1 本地模式

![本地模式检查1](./Imgs/img-8.png)

![本地模式检查2](./Imgs/img-9.png)

![本地模式检查3](./Imgs/img-10.png)

![本地模式检查4](./Imgs/img-11.png)

#### 2.2.2 Http模式

![Http模式检查1](./Imgs/img-2.png)

![Http模式检查2](./Imgs/img-3.png)

![Http模式检查3](./Imgs/img-4.png)

![Http模式检查4](./Imgs/img-5.png)



