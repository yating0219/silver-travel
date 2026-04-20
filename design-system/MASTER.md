# 銀遊通 Design System — MASTER.md

## 品牌定位
- 產品名稱：銀遊通 SilverTravel
- 定位：溫暖、安心、簡單、值得信賴的銀髮旅遊平台
- 用戶：55–80 歲，數位能力初中級

---

## 色彩系統 Color Tokens

### 主色 Primary
- `--color-primary: #F97316`       橙色（活力、溫暖）
- `--color-primary-dark: #EA6000`  深橙（hover 狀態）
- `--color-primary-light: #FED7AA` 淡橙（背景填色）
- `--color-primary-pale: #FFF7ED`  極淡橙（卡片底色）

### 輔色 Accent
- `--color-accent: #0891B2`        青藍（信任、安全感）
- `--color-accent-light: #E0F2FE`  淡藍（標籤、徽章）

### 中性色 Neutral
- `--color-gray-900: #111827`      主要文字
- `--color-gray-700: #374151`      次要文字
- `--color-gray-500: #6B7280`      輔助說明文字
- `--color-gray-200: #E5E7EB`      邊框、分隔線
- `--color-gray-100: #F3F4F6`      頁面背景
- `--color-white: #FFFFFF`         卡片背景

### 語意色 Semantic
- `--color-success: #16A34A`       綠（銀髮友善認證）
- `--color-warning: #D97706`       琥珀（警示購物次數）
- `--color-danger: #DC2626`        紅（緊急、警告）
- `--color-info: #0891B2`          青（資訊提示）

---

## 字體系統 Typography

### 字型
```css
font-family: 'Noto Sans TC', sans-serif;
```
（CDN: https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;500;700&display=swap）

### 字級
- `--text-xs: 14px`    法律文字、版權
- `--text-sm: 16px`    輔助說明
- `--text-base: 18px`  **預設內文**（銀髮族標準）
- `--text-lg: 20px`    卡片標題、重要資訊
- `--text-xl: 24px`    大字模式內文 / 區塊標題
- `--text-2xl: 30px`   頁面主標題
- `--text-3xl: 36px`   Hero 標題

### 行距
- 內文 line-height: 1.75（寬鬆易讀）
- 標題 line-height: 1.3

---

## 間距系統 Spacing (8pt Grid)
- 4px / 8px / 12px / 16px / 24px / 32px / 48px / 64px

---

## 圓角 Border Radius
- 按鈕：`border-radius: 12px`
- 卡片：`border-radius: 16px`
- 標籤：`border-radius: 9999px`（pill）

---

## 陰影 Shadow
- 卡片：`box-shadow: 0 2px 12px rgba(0,0,0,0.08)`
- 按鈕 hover：`box-shadow: 0 4px 16px rgba(249,115,22,0.3)`

---

## 元件規則 Component Rules

### 按鈕 Button
- 最小高度：52px（銀髮易點觸）
- 最小寬度：120px
- 字體：18px Bold
- 觸控區域 ≥ 44×44px（WCAG 2.1 AA）
- 主按鈕：橙底白字
- 次按鈕：白底橙框橙字
- 危險按鈕：紅底白字

### 輸入欄 Input
- 高度：52px
- 字體：18px
- 邊框：2px solid #E5E7EB
- Focus：2px solid #F97316
- 錯誤：2px solid #DC2626

### 卡片 Card
- 白底、圓角 16px、輕陰影
- 行程卡片最低高度：200px
- 必含：圖片、標題（20px）、價格（橙色）、認證標章

### 固定底部 Sticky Footer
- **每頁必須**有固定底部，包含：
  - 📞 撥打客服（主要行動）
  - 底部導航（首頁、搜尋、問卷、家庭）

### 銀髮友善標章 Badge
- 綠色背景、白字
- 最小寬度 80px、高度 28px
- 種類：♿ 無障礙 / 🏥 醫療 / 🍚 銀髮餐 / 🚶 緩步行

---

## 無障礙規範 Accessibility

- 對比度：≥ 4.5:1（WCAG AA）
- 所有圖片必須有 alt 屬性
- 表單必須有 label 對應
- Focus 狀態必須可見（橙色 outline）
- 語義化 HTML：使用 header, main, nav, section, footer

---

## 導航結構 Navigation

### 桌面 Header
Logo | 搜尋 | 首頁 | 揪團廣場 | 家庭 | 📞 客服

### 底部固定 Sticky Bar（行動優先）
🏠 首頁 | 🔍 搜尋 | ❤️ 問卷 | 👨‍👩‍👧 家庭 | 📞 客服
