# 🚀 Aqive v2.0 - GitHub 部署指南

## ✅ 為什麼適合上傳到 GitHub？

### 完全可以！優勢包括：

1. ✅ **純靜態網頁**：無需後端服務器
2. ✅ **使用 CDN**：Tailwind CSS 和 Font Awesome 都是 CDN
3. ✅ **無敏感資訊**：沒有 API 密鑰或私密數據
4. ✅ **免費託管**：GitHub Pages 完全免費
5. ✅ **自動部署**：推送即更新
6. ✅ **專業展示**：獲得一個線上可訪問網址

---

## 📦 部署步驟

### 方法一：使用 GitHub Desktop（最簡單）

#### 步驟 1：準備 Repository
```bash
1. 打開 GitHub Desktop
2. File → New Repository
   - Name: aqive-healing-platform-v2
   - Description: Professional stress management platform with dual language support
   - Local Path: 選擇 p2 資料夾的上層目錄
3. Create Repository
```

#### 步驟 2：添加文件
```bash
1. 所有 p2 資料夾的文件會自動顯示
2. 在左側勾選要上傳的文件：
   ✅ 所有 .html 文件（21 個頁面）
   ✅ styles.css
   ✅ README.md
   ✅ .gitignore
   ✅ 所有 .md 文檔
3. 左下角填寫 Commit message：
   "Initial commit: Aqive v2.0 dual-language prototype"
4. 點擊 "Commit to main"
```

#### 步驟 3：推送到 GitHub
```bash
1. 點擊 "Publish repository"
2. 選擇：
   - Name: aqive-healing-platform-v2
   - Description: 填寫描述
   - ✅ Keep this code private（如果需要私密）
   - 或 ⬜ 保持公開
3. 點擊 "Publish Repository"
```

#### 步驟 4：啟用 GitHub Pages
```bash
1. 在 GitHub Desktop 點擊 "View on GitHub"
2. 進入 Repository → Settings
3. 左側選單 → Pages
4. Source 選擇：
   - Branch: main
   - Folder: / (root)
5. 點擊 Save
6. 等待 1-2 分鐘，會看到網址：
   https://你的用戶名.github.io/aqive-healing-platform-v2/
```

---

### 方法二：使用命令列（進階）

```bash
# 1. 進入 p2 資料夾
cd "/Users/miyabi/Documents/Aqive app/p2"

# 2. 初始化 Git
git init

# 3. 添加所有文件
git add .

# 4. 提交
git commit -m "Initial commit: Aqive v2.0 dual-language prototype"

# 5. 連接遠端 repository（需先在 GitHub 創建）
git remote add origin https://github.com/你的用戶名/aqive-healing-platform-v2.git

# 6. 推送
git branch -M main
git push -u origin main
```

---

## 🌐 部署後的訪問方式

### 主要入口
```
https://你的用戶名.github.io/aqive-healing-platform-v2/index.html
```

### 直接訪問頁面
```
# 英文版
https://你的用戶名.github.io/aqive-healing-platform-v2/home.html
https://你的用戶名.github.io/aqive-healing-platform-v2/discover.html

# 中文版
https://你的用戶名.github.io/aqive-healing-platform-v2/home-zh.html
https://你的用戶名.github.io/aqive-healing-platform-v2/discover-zh.html
```

### 頁面總覽（推薦分享這個）
```
https://你的用戶名.github.io/aqive-healing-platform-v2/page-overview.html
```

### 所有頁面展示
```
https://你的用戶名.github.io/aqive-healing-platform-v2/all-pages-showcase.html
```

---

## 📋 建議的 Repository 設置

### Repository 名稱
```
aqive-healing-platform-v2
```

### Description
```
🌿 Professional stress management and energy balance platform with dual language support (English & Traditional Chinese). Features AI companion, mood tracking, meditation, and breathing exercises. Built with HTML, Tailwind CSS, and responsive iPhone 15 Pro design.
```

### Topics (標籤)
```
wellness
meditation
mental-health
stress-management
mindfulness
ui-design
prototype
tailwindcss
dual-language
responsive-design
```

### README.md
已經包含完整的項目說明，無需修改！✅

---

## 🎯 部署後的檢查清單

部署完成後，確認以下項目：

- [ ] ✅ 主頁可以正常訪問
- [ ] ✅ 所有 21 個頁面都可以打開
- [ ] ✅ 語言切換功能正常
- [ ] ✅ 頁面跳轉正常運作
- [ ] ✅ Tailwind CSS 樣式正確顯示
- [ ] ✅ Font Awesome 圖標正常顯示
- [ ] ✅ Unsplash 圖片正常載入
- [ ] ✅ 動畫效果正常（呼吸練習等）
- [ ] ✅ iPhone 容器正確顯示
- [ ] ✅ 響應式設計正常

---

## 🔧 常見問題

### Q1: 圖片顯示不正常？
**A:** Unsplash 圖片使用 HTTPS，GitHub Pages 也是 HTTPS，應該沒問題。如果有問題，可以：
1. 下載圖片到本地 `/images` 資料夾
2. 更新 HTML 中的圖片路徑

### Q2: CSS 樣式沒有載入？
**A:** 確認：
1. Tailwind CSS CDN 連結正確
2. `styles.css` 在同一目錄下
3. 清除瀏覽器快取重新載入

### Q3: 頁面跳轉不正常？
**A:** GitHub Pages 的路徑是絕對的，如果有問題：
1. 確認所有 `navigate()` 函數中的路徑正確
2. 檢查大小寫（GitHub Pages 對大小寫敏感）

### Q4: 想要自定義網域？
**A:** 在 GitHub Pages 設置中：
1. Settings → Pages
2. Custom domain 輸入你的網域
3. 在你的網域 DNS 設置 CNAME 記錄

### Q5: 如何更新網站？
**A:** 
```bash
# 修改文件後
git add .
git commit -m "Update: 描述你的更新"
git push

# GitHub Pages 會自動重新部署（1-2 分鐘）
```

---

## 📱 分享建議

### 給客戶展示
```
分享連結：
https://你的用戶名.github.io/aqive-healing-platform-v2/

說明：
"這是 Aqive Healing Platform 的高保真原型，
支援英文和繁體中文雙語切換，
請在電腦上訪問以獲得最佳體驗。"
```

### 給設計師查看
```
分享連結：
https://你的用戶名.github.io/aqive-healing-platform-v2/all-pages-showcase.html

說明：
"這個頁面可以同時看到所有 11 個頁面的設計，
方便快速瀏覽和評審。"
```

### 給投資者演示
```
分享連結：
https://你的用戶名.github.io/aqive-healing-platform-v2/page-overview.html

說明：
"從這裡開始體驗完整的產品原型，
包含情緒管理、AI 陪伴、課程探索等核心功能。"
```

---

## 🎨 SEO 優化建議（可選）

如果想要更好的搜尋引擎收錄，可以：

### 1. 添加 meta 標籤
在每個 HTML 的 `<head>` 中添加：
```html
<meta name="description" content="Aqive - Professional stress management platform">
<meta name="keywords" content="wellness, meditation, stress management">
<meta property="og:title" content="Aqive Healing Platform">
<meta property="og:description" content="Your journey to balance and awareness">
<meta property="og:image" content="封面圖片網址">
```

### 2. 創建 sitemap.xml
列出所有頁面，方便搜尋引擎索引。

### 3. 添加 robots.txt
告訴搜尋引擎哪些頁面可以索引。

---

## 📊 監控與分析（進階）

### Google Analytics
如果想追蹤訪問數據：
1. 註冊 Google Analytics
2. 在每個頁面 `<head>` 加入追蹤代碼

### GitHub Insights
在 Repository → Insights 可以看到：
- 訪問次數
- Clone 次數
- 流量來源

---

## 🎁 額外福利

### GitHub Pages 的優勢

✅ **完全免費**  
✅ **無流量限制**（月流量 100GB）  
✅ **HTTPS 加密**（自動提供 SSL）  
✅ **全球 CDN**（載入速度快）  
✅ **自動部署**（推送即更新）  
✅ **穩定可靠**（GitHub 基礎設施）  
✅ **支援自定義網域**

### 適合用途

✅ 產品原型展示  
✅ 客戶演示  
✅ 設計評審  
✅ 團隊協作  
✅ 投資者展示  
✅ 作品集展示

---

## 🚀 開始部署

準備好了嗎？按照上面的步驟：

1. ✅ 確認 .gitignore 已創建
2. ✅ 檢查所有文件完整
3. ✅ 選擇部署方法（GitHub Desktop 或命令列）
4. ✅ 上傳到 GitHub
5. ✅ 啟用 GitHub Pages
6. ✅ 測試網站
7. ✅ 分享連結！

---

**祝部署順利！** 🎉

如有任何問題，請參考 GitHub Pages 官方文檔：
https://docs.github.com/pages

---

**撰寫日期**：2025-11-10  
**版本**：v2.0（雙語版）

