# OopMineGame
### 2D 程序化生成沙盒遊戲開發實務

報告人：高憲成、張育溥、程昱銘

課程：物件導向程式設計



## 專案動機
* **核心願景**：打造一個類似 Minecraft 的 2D 沙盒世界
* **技術目標**：
- 實踐 **C++23** 現代語法
- 構建高度解耦的 **GUI 系統**
- 應用 **OOP 三大特性** 解決管理難題



## 系統架構圖 (UML)

<!-- * 以 `World` 為核心容器
<!--     - 組合 `Entity` (動態實體)
<!--     - 組合 `Block` (靜態方塊)
<!-- * 分離 `Logic` 與 `Render` 層



![](/uml.png) <!-- element height="30%" width="30%" -->
<!-- ![](/uml.png =256x256) -->
<!-- <img src="/uml.png" style="max-height: 90%; max-width: 90%; object-fit: contain;" /> -->



## OOP 三大特性之應用 (1/2)

### 1. 封裝 (Encapsulation)
* **資料保護**：將 `pos`, `vel`, `health` 等關鍵狀態設為 `protected`
* **統一介面**：透過虛擬函式 `update()` 與 `draw()` 封裝複雜的物理邏輯

### 2. 繼承 (Inheritance)
* **實體層次**：`Entity` → `Mob` → `Sheep`
* **GUI 層次**：`Container` → `FlowContainer` → `Hotbar`



## OOP 三大特性之應用 (2/2)

### 3. 多型 (Polymorphism)

* **動態綁定**：

```cpp
// 使用 std::unique_ptr 實作異質容器
std::vector<std::unique_ptr<Entity>> entities;
for (auto& e : entities) e->update(dt); // 執行各自的自定義行為
```

* **虛擬解構子**：確保透過基底指標刪除物件時能正確釋放資源



## 技術亮點：設計模式

### 1. 觀察者模式 (Observer)
* 應用於 `Bindable<T>`：當數值變更時，自動通知 UI 重新渲染

### 2. 建造者模式 (Builder)
* 應用於 `BlockBuilder`：透過鏈式呼叫 (chaining) 優化方塊初始化流程

### 3. 組合模式 (Composite)
* 應用於 **GUI 樹狀架構**：Container 可以包含 Button、Slider 或其他 Container



## 程序化生成演算法

* **柏林噪音 (Perlin Noise)**：
    - 使用 `FastNoiseLite` 實作平滑地形
    - 支援種子碼系統，保證世界生成的可重現性



## 開發技術細節

* **現代 C++ 實踐**：
    - 使用 `std::unique_ptr` 進行自動記憶體管理
    - 使用模板實作萬用類型的 `Bindable<T>` 屬性系統



## 團隊分工與管理

* **版本控制**：使用 GitHub 進行版本控制與一鍵發布

* **分工明細**：
    - **張育溥**：UML/報告撰寫、核心架構 (World/Entity) 構建
    - **高憲成**：GUI 框架開發、程式設計、邏輯整合
    - **程昱銘**：吃、睡



## 未來展望

1. **持久化儲存**：實作 JSON 或二進位存檔系統
2. **AI 進化**：提升生物 AI 與路徑偵測的複雜度
3. **擴展內容**：加入更多合成表與工具系統



# Q & A
### 感謝聆聽，歡迎指教
