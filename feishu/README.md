# Feishu MCP 配置

基于 [Feishu-MCP](https://github.com/cso1z/Feishu-MCP)（npm 包 `feishu-mcp`）提供飞书文档的 MCP 服务。

## 配置步骤

1. 复制环境变量模板：
   ```bash
   cp .env.example .env
   ```

2. 编辑 `.env` 文件，填入飞书应用凭证：
   - `FEISHU_APP_ID`：飞书应用 ID（如 `cli_xxxxx`）
   - `FEISHU_APP_SECRET`：飞书应用密钥
   - `FEISHU_AUTH_TYPE`：`tenant`（应用级）或 `user`（用户级）

3. 飞书应用创建与权限配置请参考 [官方教程](https://open.feishu.cn/document/home/develop-a-bot-in-5-minutes/create-an-app)。

## 启动方式

在项目根目录执行：

```bash
docker compose up -d feishu
```

服务默认监听 `http://localhost:3201`。

## Cursor 客户端配置

在 Cursor 的 MCP 配置中添加：

userKey：tenant 模式下不是必须，user 模式下用来区分不同用户，用户自己随机生成

```json
{
  "mcpServers": {
    "feishu-mcp": {
      "url": "http://localhost:3201/sse?userKey=你的随机userKey"
    }
  }
}
```

**注意**：`userKey` 为连接用户的唯一标识，建议使用随机字符串。
