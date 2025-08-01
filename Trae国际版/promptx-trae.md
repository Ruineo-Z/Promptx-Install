# Trae国际版

本文档用于介绍如何在Trae 国际版中安装Promptx MCP

## 安装命令

### 本地模式(推荐)

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

### Http模式

```json
{
  "mcpServers": {
    "promptx": {
      "type": "http",
      "url": "http://localhost:3000/mcp"
    }
  }
}
```

## 视频教程
### 本地模式
<video src="https://github.com/user-attachments/assets/b6cd9dc3-ca82-4e72-bd07-e645db9ec629"
       width="640" height="360" controls>
</video>

### Http模式
<video src="https://github.com/user-attachments/assets/479bb843-059e-4cc6-9cea-cc080dd2837b"
       width="640" height="360" controls>
</video>

## 图文教程

### 1. 打开MCP页面

![MCP页面1](./Imgs/img-1.png)

![MCP页面2](./Imgs/img-2.png)

### 2. 复制安装命令，进行粘贴

#### 2.1 本地模式(推荐)
![本地模式安装](./Imgs/img-3.png)

#### 2.2 Http模式
![Http模式安装](./Imgs/img-4.png)

### 3. 完成安装

![安装完成](./Imgs/img-5.png)

## 使用
![使用指南1](./Imgs/img-6.png)
![使用指南2](./Imgs/img-7.png)