# 1. 确保服务器已安装docker和docker compose
# 2.构建启动脚本
**`docker-compose.yml` `nginx.conf` `Dockerfile` 必须在同一目录下**
![img-1.png](/assets/uploads/files/1756174743380-img-1.png) 
## 2.1 复制下方代码，保存为docker-compose.yml

```docker
services:
  nginx:
    image: nginx:alpine
    container_name: promptx-nginx
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
    depends_on:
      - promptx
    restart: unless-stopped
    networks:
      - promptx-network

  promptx:
    container_name: promptx
    image: node:20-alpine
    volumes:
      - ~/.promptx:/root/.promptx
      - promptx_npm_cache:/usr/local/lib/node_modules  # 缓存npm全局包
    environment:
      - PROMPTX_DIR=/root/.promptx
    command: >
      sh -c "npm install -g @promptx/cli@dev && promptx mcp-server --transport http --host 0.0.0.0 --port 3000"
    restart: unless-stopped
    networks:
      - promptx-network

networks:
  promptx-network:
    driver: bridge

volumes:
  promptx_npm_cache:
``` 
## 2.2 复制下方代码，保存为nginx.conf
```nginx.conf
events {
    worker_connections 1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;
    
    # 日志格式
    log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                    '$status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';
    
    access_log /var/log/nginx/access.log main;
    error_log /var/log/nginx/error.log;
    
    # 基本设置
    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;
    
    # 上游服务器定义
    upstream promptx_backend {
        server promptx:3000;
    }
    
    server {
        listen 80;
        server_name localhost;
        
        # 根路径可以返回一个简单的页面或重定向
        location / {
            return 200 'Nginx Proxy Server - Available services: /promptx/';
            add_header Content-Type text/plain;
        }
        
        # PromptX服务代理
        location /promptx/ {
            # 移除 /promptx 前缀，转发到后端
            rewrite ^/promptx/(.*) /$1 break;
            
            proxy_pass http://promptx_backend;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
            
            # 超时设置
            proxy_connect_timeout 30s;
            proxy_send_timeout 30s;
            proxy_read_timeout 30s;
            
            # 缓冲设置
            proxy_buffering off;
            proxy_request_buffering off;
        }
        
        # 健康检查端点
        location /nginx-health {
            access_log off;
            return 200 "nginx healthy\n";
            add_header Content-Type text/plain;
        }
    }
}

```

# 3.启动服务
**启动命令**
```sh
# docker版本大于Docker 20.10+ 
docker compose up -d

# docker版本小于Docker 20.10
docker-compose up -d
```
**检查启动状态**
```sh
curl http://localhost:80/promptx/health
```
![img-2.png](/assets/uploads/files/1756176540806-img-2.png) 

**连接服务**
```json
# 使用http形式连接
{
  "servers": {
    "promptx": {
      "type": "http",
      "url": "http://your_domain:80/promptx/mcp"
    }
  }
}
```
**Augment示例**
![72ab1868-ecc1-4cef-ad3b-0b3bc2a23ccf-image.png](/assets/uploads/files/1756176394245-72ab1868-ecc1-4cef-ad3b-0b3bc2a23ccf-image.png) 
