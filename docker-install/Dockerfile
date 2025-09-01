FROM node:20-slim

ENV TZ=Asia/Shanghai NODE_ENV=production
RUN corepack enable

EXPOSE 3000

CMD ["npx","-f","-y","@promptx/mcp-server","--transport","http","--port","3000","--host","0.0.0.0"]
