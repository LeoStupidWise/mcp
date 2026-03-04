# Feishu MCP 配置

基于 [Feishu-MCP](https://github.com/cso1z/Feishu-MCP)（npm 包 `feishu-mcp`）提供飞书文档的 MCP 服务。

## 认证模式

| 模式 | 说明 |
|------|------|
| `tenant` | 应用级，创建的文档需单独添加应用为协作者才能编辑 |
| `user` | 用户级，需 OAuth 授权，授权后用户可编辑所有文档 |

## 配置步骤

1. 复制环境变量模板：
   ```bash
   cp .env.example .env
   ```

2. 编辑 `.env` 文件，填入飞书应用凭证：
   - `FEISHU_APP_ID`：飞书应用 ID（如 `cli_xxxxx`）
   - `FEISHU_APP_SECRET`：飞书应用密钥
   - `FEISHU_AUTH_TYPE`：`tenant` 或 `user`

3. 飞书应用创建与权限配置请参考 [官方教程](https://open.feishu.cn/document/home/develop-a-bot-in-5-minutes/create-an-app)。

4. **user 模式额外配置**：在 [飞书应用管理](https://open.feishu.cn/app/) → 安全设置 → 重定向 URL 中，添加回调地址：
   - 本地：`http://localhost:3201/callback`
   - 服务器部署：`https://你的域名/callback`（端口 80/443 可省略）

## 启动方式

在项目根目录执行：

```bash
docker compose up -d feishu
```

服务默认监听 `http://localhost:3201`。

## Cursor 客户端配置

在 Cursor 的 MCP 配置中添加：

```json
{
  "mcpServers": {
    "feishu-mcp": {
      "url": "http://localhost:3201/sse?userKey=你的随机userKey"
    }
  }
}
```

**userKey 说明**：
- `tenant` 模式：可选，用于区分不同连接
- `user` 模式：**必填**，每个用户使用唯一标识（建议随机字符串），首次连接时会跳转飞书完成 OAuth 授权
