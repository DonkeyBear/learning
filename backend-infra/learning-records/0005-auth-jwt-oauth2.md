# 鑑權系統 — JWT / OAuth2 / Session 三種機制的 trade-off 已建立

完成 Lesson 0005，能區分 Authentication（你是誰）vs Authorization（你能做什麼），並理解三種鑑權機制的選擇邏輯：

- **Session**：傳統 SSR 方案，stateful，適合單體應用；需 Redis 才能在多實例間共享
- **JWT**：stateless，適合 SPA + API 架構；天生免疫 CSRF 但無法主動撤銷
- **OAuth2**：第三方登入的標準協定，是授權框架而非認證機制

**核心洞察**：JWT 的「無法撤銷」是特性而非 bug——你需要的是短效期 access token + 長效期 refresh token 的雙 token 模式。

**Implications:** 已能在 FastAPI 中實作完整的 JWT + OAuth2 流程。下一課自然過渡到資安——鑑權做完了，但攻擊者會從其他角度進來。

**相關課程**：[[0002-request-lifecycle-foundation]] [[0006-web-security-owasp]]
