# 使用 Node 20 官方镜像
FROM node:20.17.0

WORKDIR /app

# 初始化并安装 feishu-mcp 包
RUN npm init -y && npm install feishu-mcp --registry=https://registry.npmmirror.com

EXPOSE 3333

# 启动 HTTP 服务（与 Feishu-MCP 官方 Dockerfile 一致）
CMD ["node", "node_modules/feishu-mcp/dist/index.js"]
