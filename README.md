# Aqive Healing Platform - 高保真原型

## 📱 專案概述

這是 Aqive Healing Platform 的高保真 HTML 原型，基於 PRD v1.4 設計，呈現完整的用戶體驗流程。

### 設計特色
- ✨ 可愛友善的角色感元素
- 🎨 現代化 UI 設計，符合 iPhone 15 Pro 螢幕比例（393 x 852）
- 🌈 柔和漸層色彩與流暢動效
- 📱 完整的手機端交互體驗
- 🎯 符合身心靈療癒平台的溫暖氛圍

## 🗂️ 頁面結構

### 主要頁面
1. **index.html** - 主入口（iPhone 容器）
2. **home.html** - 首頁/Dashboard
3. **discover.html** - 探索頁面
4. **ai-chat.html** - AI 對話陪伴
5. **player.html** - 冥想音頻播放器
6. **profile.html** - 個人檔案

### 功能頁面
7. **course-detail.html** - 課程詳情
8. **quiz.html** - 能量測驗問卷
9. **quiz-result.html** - 測驗結果（過渡頁）
10. **quiz-detail.html** - 五境詳細分析
11. **product.html** - 我的產品列表
12. **product-activate.html** - 產品能量同步
13. **breath.html** - 呼吸練習

### 樣式文件
14. **styles.css** - 自定義樣式

## 🚀 快速開始

### 方法一：本地開啟
1. 在瀏覽器中打開 `index.html`
2. 即可在 iPhone 容器中瀏覽所有頁面

### 方法二：直接瀏覽單頁
直接在瀏覽器打開任何 HTML 頁面（如 `home.html`）即可單獨預覽

## 🎨 技術架構

### 技術棧
- **HTML5** - 語義化標籤
- **Tailwind CSS** - 快速樣式開發（CDN）
- **Font Awesome 6** - 圖標庫（CDN）
- **Vanilla JavaScript** - 輕量級交互

### 設計規範
- **配色方案**：
  - 主色：`#D7E6E3`（柔和青綠）
  - 次色：`#C8B6E2`（能量紫）
  - 強調色：`#F5E6CC`（金光）
- **字體**：系統字體 + Noto Sans TC
- **圓角**：2xl (16px) 至 3xl (24px)
- **陰影**：柔和多層次

## 📐 頁面導航關係

```
index.html (主容器)
│
├─ home.html (首頁)
│  ├─ player.html (冥想播放)
│  ├─ ai-chat.html (AI 對話)
│  ├─ breath.html (呼吸練習)
│  ├─ quiz.html → quiz-result.html → quiz-detail.html
│  ├─ course-detail.html
│  └─ product.html → product-activate.html
│
├─ discover.html (探索)
│  └─ course-detail.html
│
├─ ai-chat.html (AI)
│
├─ player.html (播放器)
│
└─ profile.html (個人)
   ├─ product.html
   └─ (我的課程、收藏等)
```

## 🎯 核心功能展示

### 1. 今日頻率與快速行動（home.html）
- 每日能量狀態展示
- 快速啟動冥想、AI 對話、呼吸練習
- 個人化推薦課程

### 2. AI 陪伴對話（ai-chat.html）
- 對話式介面
- 快速話題按鈕
- 抽卡功能展示
- 行動建議卡片

### 3. 冥想音頻播放（player.html）
- 全螢幕沉浸式播放器
- 進度控制
- 播放列表預覽

### 4. 五境能量測驗（quiz.html 系列）
- 問卷流程
- 生成動畫
- 五境詳細分析（身體/情緒/心智/人際/靈性）

### 5. 產品能量同步（product.html 系列）
- 產品列表與狀態
- 啟動儀式動畫
- 使用記錄追蹤

### 6. 呼吸練習（breath.html）
- 視覺引導呼吸
- 4-2-6 呼吸法
- 進度追蹤

## 💡 互動亮點

1. **柔和動畫**：
   - Blob 形狀變形（`@keyframes morph`）
   - 能量光暈效果（`energy-glow`）
   - 平滑過渡（`transition-smooth`）

2. **友善角色**：
   - Emoji 作為視覺角色
   - 圓潤的卡片設計
   - 明亮漸層色彩

3. **引導式體驗**：
   - 清晰的操作指引
   - 進度條反饋
   - 完成成就感

## 📱 響應式設計

- iPhone 15 Pro 比例（393 x 852）
- Safe Area 處理
- 適配瀏海屏幕
- 底部導航避讓

## 🎨 轉為 Figma 說明

### 建議流程
1. 使用 Figma 的 "Import from HTML" 插件
2. 或使用截圖後在 Figma 中重建
3. 所有尺寸、間距、顏色都已標準化，便於重建

### 設計 Token
```css
/* 間距系統 */
gap-2: 8px
gap-3: 12px
gap-4: 16px
gap-6: 24px

/* 圓角系統 */
rounded-xl: 12px
rounded-2xl: 16px
rounded-3xl: 24px
rounded-full: 9999px

/* 陰影系統 */
shadow-sm: 0 1px 2px rgba(0,0,0,0.05)
shadow-md: 0 4px 6px rgba(0,0,0,0.1)
shadow-lg: 0 10px 15px rgba(0,0,0,0.1)
shadow-xl: 0 20px 25px rgba(0,0,0,0.1)
```

## 🔧 自定義與擴展

### 修改顏色
在 `styles.css` 的 `:root` 中修改 CSS 變數：
```css
:root {
  --primary: #D7E6E3;
  --secondary: #C8B6E2;
  --accent: #F5E6CC;
}
```

### 新增頁面
1. 複製任一現有頁面
2. 修改內容
3. 確保包含 `navigate()` 函數
4. 在相關頁面加入導航按鈕

## 📊 頁面統計

- 總頁面數：13 頁
- 總行數：約 3,500 行
- 使用 Token：優化後約 50,000 tokens
- 開發時間：完整流程設計

## 🎯 下一步建議

1. **整合真實數據**：串接後端 API
2. **動畫優化**：加入 Lottie 或 Spline 3D
3. **互動增強**：觸覺反饋（Haptic Feedback）
4. **多語言支持**：i18n 系統
5. **暗黑模式**：依據 PRD 需求實作

## 👥 目標用戶體驗

✅ **輕鬆** - 介面友善，一看就懂  
✅ **有趣** - 角色元素讓療癒變得可愛  
✅ **專業** - 五境模型完整呈現  
✅ **安心** - 柔和色彩與引導流程  
✅ **成就** - 進度追蹤與徽章系統

---

**設計與開發**：Aqive CDO  
**版本**：v1.0  
**日期**：2025-11-10

