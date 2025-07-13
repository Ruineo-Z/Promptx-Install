# Cursor

本文档用于介绍如何在Cursor中安装Promptx MCP

## 安装命令

### 本地模式(推荐)

```json
"promptx": {
    "command": "npx",
    "args": [
        "-f",
        "-y",
        "--registry",
        "https://registry.npmjs.org",
        "dpml-prompt@beta",
        "mcp-server"
    ]
}
```

### Http模式

```json
"promptx": {
  "type": "http",
  "url": "http://localhost:3000/mcp"
}
```

## 流程图

### 1. 打开Cursor的MCP页面

#### 1.1 Windows系统
![Windows MCP页面](./Imgs/img-1.png)
![Mac MCP页面](./Imgs/img-2.png)

#### 1.2 Mac系统

### 2. 复制安装命令，进行粘贴

#### 2.1 本地模式(推荐)
![本地模式安装](./Imgs/img-3.png)

#### 2.2 Http模式
![Http模式安装](./Imgs/img-4.png)

### 3. 完成安装

![安装完成](./Imgs/img-5.png)

