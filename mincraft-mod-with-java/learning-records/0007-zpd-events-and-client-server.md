# ZPD: 事件系統與伺服器/客戶端邊界

在設計 Lesson 0006 時，確認了以下 ZPD 判斷：

**關鍵知識橋樑**：Fabric 事件系統（`EventType.EVENT.register(lambda)`）和前端的 `addEventListener(event, callback)` 幾乎完全同構。這是目前課程中「知識遷移最順暢」的章節，因為學習者已經對觀察者模式有深刻直覺。因此，此課程的工作記憶（working memory）成本極低。

**真正的 ZPD 挑戰在這裡**：`isClientSide()` 的概念。這個學習者熟悉前後端分離架構（FastAPI + React），但 Minecraft 的雙端架構更像「同一個 JVM 可以同時運行兩套邏輯（單人）或遠端呼叫（多人）」，這個 mental model 轉換需要額外的認知負荷。

**Fluency vs. Storage Strength 提醒**：由於事件 API 的語法對這個學習者非常直覺，可能產生「我已經懂了」的流暢錯覺。未來應在後續課程中安排**交錯 (Interleaving)**——在新課程中要求學習者不看程式碼自行重寫一個新的事件監聽器，以測試 Storage Strength。

**未來的 ZPD 指引**：
- `InteractionResultHolder` 的不同 result 類型（`.success`, `.consume`, `.pass`）值得在事件更複雜後深化
- 未來可引入 Minecraft 的 `Packet` 機制，作為 SpringBoot 的 REST Request/Response 的類比，強化前後端概念的融合
- 「繼承覆寫 vs. 全域事件監聽」這個取捨在 SpringBoot 中對應「Override 方法 vs. @EventListener」，可以在適當時機建立連結
