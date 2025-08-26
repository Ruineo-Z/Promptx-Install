FROM node:20-alpine

# 设置工作目录
WORKDIR /app

# 设置环境变量
ENV PROMPTX_DIR=/root/.promptx

# 安装PromptX CLI
RUN npm install -g @promptx/cli@dev

# 暴露端口
EXPOSE 3000

# 启动命令
CMD ["promptx", "mcp-server", "--transport", "http", "--host", "0.0.0.0", "--port", "3000"]
