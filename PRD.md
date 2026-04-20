# 銀遊通 SilverTravel — 產品需求文件 (PRD)
> 最後更新：2026-04-14

---

## 一、產品概覽

| 項目 | 內容 |
|------|------|
| **產品名稱** | 銀遊通 SilverTravel |
| **副標語** | 銀髮族安心出遊平台 / Senior-Friendly Travel Platform |
| **目標用戶** | 台灣 55 歲以上銀髮旅人（及海外華人） |
| **產品類型** | 單頁 HTML 應用程式（無框架） |
| **檔案位置** | `c:\Users\Lovell_Chang\OneDrive\Desktop\AI_Training\銀遊通\銀遊通.html` |
| **技術堆疊** | HTML5 + CSS3 + Vanilla JS（無任何外部框架） |
| **設計風格** | 溫暖橘色系、無障礙優先、銀髮友善 |

---

## 二、目標用戶 (Target Users)

### 主要用戶
- **台灣銀髮旅人**：55–80 歲，中文為主，習慣大字體、簡單操作
- **需求特點**：行動能力有限、慢性病管理、需要家人安心追蹤、重視安全與費用透明

### 次要用戶
- **海外華人**：英文或中英雙語使用者，需要英文介面
- **家人/子女**：代訂行程、追蹤長輩動態

### 無障礙要求
- 最小字體 20px（正文）
- 高對比色彩
- 大型點擊目標（最小 60px 高）
- 清晰中文標示
- 鍵盤可操作

---

## 三、已完成功能 (Implemented Features)

### 3.1 核心頁面/區塊（6 個主要區塊）

| 區塊 | ID | 說明 |
|------|-----|------|
| 首頁英雄區 | `#home` | Logo、導覽列、語言切換、快速導覽列、Hero 橫幅、統計數字 |
| 找旅遊 | `#tours` | 6 個旅遊行程卡片、篩選標籤、行程詳情 Modal |
| 旅遊內容 | `#steps` | 三步驟流程說明 |
| 健康評估 | `#health` | 5 題旅遊健康問卷 + 智能配對結果 |
| 找旅伴 | `#group` | 揪團卡片、發起揪團功能 |
| 家人專區 | `#family` | 即時位置追蹤（展示）、緊急聯絡人、行程通知 |

### 3.2 銀髮餐功能 (Silver Meals Overlay)

- **進入方式**：點擊導覽列「銀髮餐」、快速導覽「銀髮餐」、底部導覽「銀髮餐」均直接開啟全螢幕 Overlay
- **UI 模式**：從底部滑出的全螢幕 Overlay（`transform: translateY(100%)` → `.open { translateY(0) }`）
- **餐點篩選**：6 個篩選標籤（全部/軟質易嚼/低鈉/糖友/素食/高蛋白）
- **6 種餐點**：
  1. 軟燉豬肉蓋飯（軟質、高蛋白）
  2. 清蒸鱈魚佐蔬菜（低鈉、軟嫩）
  3. 控糖養生便當（糖友、低GI）
  4. 素食養生什錦炒（全素、高纖）
  5. 廣東皮蛋瘦肉粥（極軟質、低鈉）
  6. 豆腐布丁＋牛奶（高鈣、甜點）
- **選餐流程**：點卡片選取 → 購物車面板即時更新 → 確認送出預約
- **無障礙**：aria-checked, aria-live, tabindex, keyboard 操作支援
- **營養師說明區**：連結至健康問卷填寫特殊需求

### 3.3 健康問卷 + 智能配對

- **5 道題目**（單選+複選）：
  1. Q1：行動能力（輪椅/慢走/2–4km/5km+）
  2. Q2：健康狀況複選（高血壓/糖尿病/膝蓋/肺/健康）
  3. Q3：旅遊偏好（文化/自然/溫泉/海景）
  4. Q4：同行方式（獨行/夫妻/家人/揪團）
  5. Q5：預算（3萬以下/3–5萬/5萬以上/彈性）
- **配對算法**：
  - 每個行程有 `keywords` 陣列
  - 用戶答案 key 與 keywords 比對計分
  - 預算懲罰邏輯（超預算扣分）
  - 輪椅無障礙強制篩選
  - 最多顯示前 4 個最高分行程
  - 配對百分比進度條、🥇 最推薦標章
- **結果展示**：配對標籤、配對理由、行程卡片（可點擊開啟 Modal）

### 3.4 行程 Modal 詳情

- 6 個完整行程資料：
  - 日本京都賞櫻溫泉 5D4N
  - 台灣環島文化遊 8D7N
  - 北海道養生溫泉療癒 6D5N
  - 歐洲三國慢遊 12D11N
  - 峇里島悠閒海景療癒 5D4N
  - 九州溫泉文化探索 6D5N
- 每個行程包含：標籤、亮點、每日行程、價格、出發日期、報名按鈕

### 3.5 中英雙語系統 (Bilingual System)

#### 架構設計
- **`T` 物件**：存放所有 `data-i18n` / `data-i18n-html` key 的 zh/en 文字
- **`S` 物件**：存放 7 個主要區塊的完整 HTML（用於區塊級替換）
  - `tours-grid`：6 個旅遊行程卡片
  - `group-cta`：揪團 CTA 橫幅
  - `group-grid`：3 個揪團卡片
  - `family-body`：家人追蹤 + 緊急聯絡人 + 功能區塊
  - `reviews-grid`：3 個評價卡片
  - `footer-grid`：頁尾 4 欄
  - `footer-bottom`：版權行
- **`setLang(lang)`** 函式：同時處理 data-i18n、data-i18n-html、sectionMap 三種替換
- **語言切換 UI**：頂部導覽列的 中文 / EN 切換按鈕

#### 已翻譯範圍
- ✅ 導覽列所有項目
- ✅ 快速導覽列
- ✅ Hero 橫幅（標語、標題、描述、按鈕、統計）
- ✅ 為什麼選擇銀遊通（3 個卡片）
- ✅ 旅遊行程區（標題、篩選標籤、6 個行程卡片）
- ✅ 三步驟區塊
- ✅ 健康問卷（所有 5 題、20 個選項、按鈕）
- ✅ 揪朋友區塊（CTA + 3 個揪團卡片）
- ✅ 家人關心專區
- ✅ 評價區塊（3 個評價）
- ✅ CTA 區塊
- ✅ 頁尾（4 欄 + 版權）
- ✅ 底部導覽列
- ✅ 銀髮餐 Overlay（標題、返回按鈕）

#### 尚待完成的翻譯（截至 2026-04-14）
- ⏳ 銀髮餐 Overlay 步驟說明文字
- ⏳ 銀髮餐篩選標籤
- ⏳ 6 個餐點卡片內容（名稱、描述、標籤）
- ⏳ 購物車面板文字
- ⏳ 營養師說明區塊
- ⏳ 健康問卷配對結果動態內容（tagMap、配對理由、行程名稱）
- ⏳ 行程 Modal 所有內容（標題、每日行程、日期、說明文字）
- ⏳ JS 動態生成文字（toggleMeal、renderMealCart、confirmMeals 等）

---

## 四、設計系統 (Design System)

### 色彩
```css
--orange:    #E8601C   /* 主色：橘色 CTA */
--orange-d:  #C2410C   /* 深橘：Hover */
--orange-l:  #FFF7ED   /* 淺橘：背景 */
--orange-m:  #FED7AA   /* 中橘：邊框 */
--green:     #15803D   /* 成功/醫療/徽章 */
--blue:      #1D4ED8   /* 資訊 */
--teal:      #0D9488   /* 療癒/溫泉 */
--purple:    #7C3AED   /* 特殊/海景 */
--text:      #1C1917   /* 主文字 */
--text2:     #57534E   /* 次要文字 */
--bg:        #FFFBF5   /* 頁面背景 */
```

### 字體
- 主字體：Noto Sans TC（Google Fonts）
- 備用：PingFang TC, Microsoft JhengHei
- 正文：20px，行高 1.8
- 標題：34px（section-title）

### 間距
- 8pt/4pt 網格系統
- 按鈕最小高度：60px（大按鈕 72px）
- 圓角：--r-sm(14px) / --r-md(20px) / --r-lg(28px) / --r-xl(40px)

---

## 五、技術架構

### 單頁架構
- 所有功能整合在單一 `銀遊通.html` 檔案
- 無需伺服器、無需建構工具
- 直接在瀏覽器開啟：`file:///C:/Users/Lovell_Chang/OneDrive/Desktop/AI_Training/銀遊通/銀遊通.html`

### 核心 JS 函式
| 函式 | 用途 |
|------|------|
| `setLang(lang)` | 切換中英文 |
| `openMeals()` / `closeMeals()` | 開關銀髮餐 Overlay |
| `filterMeals(btn, tag)` | 篩選餐點 |
| `toggleMeal(card)` | 選取/取消餐點 |
| `renderMealCart()` | 更新購物車 |
| `confirmMeals()` | 確認餐點預約 |
| `runHealthMatch()` | 執行旅遊健康配對 |
| `resetQuiz()` | 重設問卷 |
| `openModal(key)` | 開啟行程 Modal |
| `closeModal()` | 關閉 Modal |
| `joinGroup(name)` | 申請加入揪團 |
| `filterTours(btn, tag)` | 篩選行程卡片 |
| `scrollTo(id)` | 平滑捲動至區塊 |
| `showToast(msg, color)` | 顯示 Toast 通知 |

### 重要 HTML ID
| ID | 用途 |
|----|------|
| `meals-overlay` | 銀髮餐全螢幕 Overlay |
| `tours-grid` | 行程卡片格（S 物件替換） |
| `group-cta-box` | 揪團 CTA（S 物件替換） |
| `group-grid` | 揪團卡片格（S 物件替換） |
| `family-body` | 家人專區主體（S 物件替換） |
| `reviews-grid` | 評價卡片格（S 物件替換） |
| `footer-grid` | 頁尾格線（S 物件替換） |
| `footer-bottom` | 版權列（S 物件替換） |
| `quiz-panel` | 問卷面板 |
| `match-results` | 配對結果區 |
| `match-grid` | 配對行程卡片格 |
| `tour-modal` | 行程詳情 Modal |
| `meal-cart` | 餐點購物車面板 |
| `btn-zh` / `btn-en` | 語言切換按鈕 |

---

## 六、資料結構

### tourMatchData（健康配對用）
```javascript
{
  key: 'kyoto',            // 對應 tours 物件的 key
  name: '中文名稱',
  name_en: 'English Name',
  emoji: '🌸',
  color: 'linear-gradient(...)',
  price: 'NT$48,800',
  priceVal: 48800,         // 用於預算篩選
  tags: ['中文標籤'],
  tags_en: ['EN Tags'],
  keywords: ['配對關鍵字'],  // 與用戶答案比對
  badgeClass: 'b-green',
  reason: '中文配對理由',
  reason_en: 'EN match reason'
}
```

### tours（行程 Modal 用）
```javascript
{
  emoji, color,
  title: '中文標題', title_en: 'EN Title',
  tags: ['中文'], tags_en: ['EN'],
  price,
  highlights: [{icon, label}],    // 中文
  highlights_en: [{icon, label}], // EN
  days: [{day, title, desc}],     // 中文
  days_en: [{day, title, desc}],  // EN
  dates: [{date, status, ok}],    // 中文
  dates_en: [{date, status, ok}], // EN
}
```

---

## 七、未完成工作 / 下次繼續事項

### 優先級 1（重要）：完成英文翻譯
上一個對話的最後任務是讓 `setLang('en')` 切換時**全部內容**都變成英文。截至 2026-04-14 仍缺以下部分：

1. **tourMatchData** — 需加入 `name_en`, `reason_en`, `tags_en` 欄位
2. **runHealthMatch()** — 需用 `currentLang` 選擇語言版本輸出
3. **tours 物件** — 需加入 `title_en`, `tags_en`, `highlights_en`, `days_en`, `dates_en`
4. **openModal()** — 需用 `currentLang` 切換顯示語言
5. **銀髮餐 Overlay 靜態文字** — 需加 `data-i18n` 到步驟、篩選標籤、購物車、營養師區塊
6. **餐點卡片** — 需加 `data-i18n` 到每張卡片的名稱/描述/標籤（6 張 × 5 個元素）
7. **JS 動態文字** — `toggleMeal`, `renderMealCart`, `clearMeals`, `confirmMeals` 需要雙語

### 優先級 2（功能增強）
- 健康問卷**逐題自動前進**精靈模式（用戶曾要求但未完整實現）
- 實際訂購/報名流程接入後端

---

## 八、對話歷史摘要

| 日期 | 用戶請求 | 完成狀態 |
|------|----------|----------|
| 2026-04 | 想直接看網頁 link | ✅ 提供 file:// 路徑 |
| 2026-04 | 在銀髮餐列出適合餐點 | ✅ 加入 6 種銀髮餐 |
| 2026-04 | 銀髮餐可供選擇 | ✅ 加入可選餐點卡片 |
| 2026-04 | 點銀髮餐直接連到餐點頁面 | ✅ 改為全螢幕 Overlay |
| 2026-04 | 設計健康問卷 + 顯示適合行程 | ✅ 5 題問卷 + 智能配對 |
| 2026-04 | 健康問卷直接連到問題+顯示結果 | ✅ 問卷與配對結果整合 |
| 2026-04 | 增加英文版供海外華人使用 | ✅ 基礎雙語系統建立 |
| 2026-04 | 確保英文版全部翻成英文 | ⏳ 進行中（下次繼續） |

---

## 九、檔案清單

```
c:\Users\Lovell_Chang\OneDrive\Desktop\AI_Training\銀遊通\
├── 銀遊通.html    ← 主要產品檔案（單一 HTML）
└── PRD.md         ← 本文件
```

---

*此 PRD 由 Claude Code 根據對話記錄自動生成，2026-04-14*
