# mcp-context-forge
- Github: https://github.com/ibm/mcp-context-forge
- Docs: https://ibm.github.io/mcp-context-forge/

# 使用 Docker 啟動
```shell
docker run -d --name mcpgateway \
  -p 4444:4444 \
  -e MCPGATEWAY_UI_ENABLED=true \
  -e MCPGATEWAY_ADMIN_API_ENABLED=true \
  -e HOST=0.0.0.0 \
  -e JWT_SECRET_KEY=my-test-key \
  -e BASIC_AUTH_USER=admin \
  -e BASIC_AUTH_PASSWORD=changeme \
  -e AUTH_REQUIRED=true \
  -e PLATFORM_ADMIN_EMAIL=admin@example.com \
  -e PLATFORM_ADMIN_PASSWORD=changeme \
  -e PLATFORM_ADMIN_FULL_NAME="Platform Administrator" \
  -e DATABASE_URL=sqlite:///./mcp.db \
  ghcr.io/ibm/mcp-context-forge:0.9.0
```

# API Endpoints
> https://github.com/ibm/mcp-context-forge?tab=readme-ov-file#api-endpoints

取得 gateways 清單
```shell
curl --location 'http://localhost:4444/gateways' \
  --header 'Authorization: Bearer ${MCPGATEWAY_BEARER_TOKEN}'
```

取得 Tools 清單
```shell
curl --location 'http://localhost:4444/tools' \
  --header 'Authorization: Bearer ${MCPGATEWAY_BEARER_TOKEN}'
```

透過 Gateway 連線
```shell
# Transport Type: SSE, URL: http://localhost:4444/servers/UUID_OF_SERVER_1/sse,  Header Name: "Authorization", Bearer Token
http://localhost:4444/servers/${UUID_OF_SERVER}/sse
http://localhost:4444/servers/${UUID_OF_SERVER}/mcp
```
