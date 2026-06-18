# ZPD: 方塊雙重註冊與 Data-Driven 思維

在設計 Lesson 0005 時，確認了以下 ZPD 判斷：

**觀察到的挑戰點**：「方塊」在 Minecraft 中是雙重存在的概念——作為世界中的固體（`Block`）與作為物品欄中的道具（`BlockItem`）。這對有前端背景的學習者而言是一個新的抽象，因為前端世界中元件的狀態通常是單一的。

**ZPD 推論**：用「包裝紙（Wrapper）」的比喻最能讓這個學習者理解 `BlockItem` 的角色——`BlockItem` 是 `Block` 的物品欄代理人。因為這個學習者熟悉 Proxy/Wrapper/Adapter 這類設計模式的前端應用（例如 React 的 HOC），所以這個比喻會進入 ZPD 舒適區而非超出。

**Loot Table 的教學意義**：此處是一個重要的思維突破點——將原本在 Java 邏輯中硬寫 `if (broken) return item;` 的思維，轉移到「資料驅動 (Data-Driven)」的 JSON 設計模式。這是 Minecraft 26 的架構哲學，與 SpringBoot 的 YAML/Properties 設定驅動有異曲同工之妙，是未來學習的重要概念橋樑。

**未來的 ZPD 指引**：
- 方塊狀態（`BlockState`、`StateDefinition`）是下一個抽象層，可在學習者熟悉基本方塊後再引入
- 應在適當時機引入 `BlockEntity`（有記憶體的方塊），以對應到 SpringBoot 的 `@Service` 有狀態服務概念
