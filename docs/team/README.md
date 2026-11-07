# 媒体模块参考

当前模块边界以 [架构文档](../ARCHITECTURE.md)、[HTTP 接口](../API.md) 和 [类型合同](../../contracts/api.ts) 为准。公开副本不包含旧开发人员分工和内部交接记录。

- `backend/media_store.py`、`backend/media_service.py`：媒体保存、状态与生命周期。
- `backend/recognition.py`：外部识别服务适配。
- `frontend/media.js`、`frontend/local-store.js`：浏览器原件、识别初稿与人工核对。
- [复杂医学图像边界](P1-COMPLEX-IMAGE-RECOGNITION.md)：当前不支持自动医学解读。
- [开发与检查](INTEGRATION.md)：公开仓库的配置与回归入口。
