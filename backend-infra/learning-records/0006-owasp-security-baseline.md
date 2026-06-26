# 資安基礎 — OWASP Top 5 攻擊與防禦策略內化

完成 Lesson 0006，建立 Web 安全的核心知識體系：

1. **Injection**（SQL/NoSQL/Command）— 參數化查詢是唯一解，過濾字元不可靠
2. **XSS** — 輸出編碼，後端責任是確保儲存資料被正確 sanitize
3. **CSRF** — JWT + Authorization header 天生免疫；cookie 場景用 SameSite=Strict
4. **Broken Access Control**（OWASP #1）— 每個端點檢查所有權，不只是檢查登入
5. **SSRF** — URL hostname 白名單 + 禁止內網 IP + 只允許 HTTPS

**核心洞察**：Broken Access Control 是 2021 年 OWASP 冠軍，因為它是「開發流程問題」而非「技術問題」——只要忘記在任何一個端點加權限檢查就是漏洞。

**Implications:** 已能在面試中給出有深度的資安回答。資安是鑑權的延續和補完。

**相關課程**：[[0005-auth-jwt-oauth2]] [[0011-production-deploy-security]]
