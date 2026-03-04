本项目提供一些 MCP 服务。

## MCP 服务

### Feishu

基于 [Feishu-MCP](https://github.com/cso1z/Feishu-MCP) 的飞书文档 MCP 服务，支持文档、Wiki、云盘等操作。详细配置见 [feishu/README.md](feishu/README.md)。

## 快速开始

```bash
# 1. 配置飞书凭证（见 feishu/README.md）
cp feishu/.env.example feishu/.env
# 编辑 feishu/.env 填入 FEISHU_APP_ID、FEISHU_APP_SECRET

# 2. 启动 MCP 服务
docker compose up -d feishu
```

服务默认监听 `http://localhost:3201`。各 MCP 配置详见对应子目录。