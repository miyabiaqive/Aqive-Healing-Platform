# Flow E：問題覺察 → 智慧推薦循環 - 完整實現

## 📋 功能概述

**目標**：在使用者出現明確困擾或完成能量分析後，系統主動給出具有啟發性的內容或課程建議，延伸覺察成行動。

---

## 🎯 完整用戶旅程

### 階段一：首次用戶引導（新增）

```
用戶首次打開 App
    ↓
onboarding.html（歡迎引導）
    ├─ Step 1：歡迎來到 Aqive
    │   └─ 說明：3 分鐘了解能量狀態
    ├─ Step 2：五境模型介紹
    │   └─ 說明：身體/情緒/心智/人際/靈性
    └─ Step 3：隱私保護承諾
        └─ 點擊「開始能量評估」
            ↓
        quiz.html（能量測驗）
```

### 階段二：問題覺察

```
quiz.html（能量測驗）
    ├─ 5 個問題（涵蓋五境）
    ├─ 情緒狀態偵測
    ├─ 生活模式評估
    └─ 壓力來源識別
        ↓
quiz-result.html（生成動畫）
    └─ 3 秒過渡動畫
        ↓
quiz-detail.html（五境報告）
    ├─ 整體能量指數：77
    ├─ 五境詳細分析
    │   ├─ 身體境：85%（良好）
    │   ├─ 情緒境：68%（需關注）⚠️
    │   ├─ 心智境：78%
    │   ├─ 人際境：72%
    │   └─ 靈性境：81%
    └─ 點擊「查看個人化推薦」
```

### 階段三：智慧推薦（新增）

```
recommendations.html（智能推薦頁）
    │
    ├─ 🤖 AI 覺察分析
    │   └─ "你的情緒境指數（68%）相對較低..."
    │
    ├─ 🎯 立即開始（最推薦）
    │   └─ 3 分鐘呼吸練習
    │       ├─ 為什麼推薦？
    │       └─ "呼吸練習是調節情緒最直接有效的方法..."
    │
    ├─ 📚 推薦閱讀
    │   └─ 《情緒不是敵人，是訊息》
    │       ├─ 3 分鐘閱讀
    │       ├─ 為什麼推薦？
    │       └─ "這篇文章能幫助你重新理解情緒..."
    │
    ├─ 🎓 推薦課程
    │   └─ 情緒釋放工作坊
    │       ├─ 60 分鐘・234 人已學
    │       ├─ 為什麼推薦？
    │       └─ "這是進階的情緒修復課程..."
    │
    ├─ 💬 AI 陪伴
    │   └─ 隨時傾訴你的感受
    │
    └─ 🎯 接下來...
        ├─ 開始我的療癒之旅 → home.html
        └─ 再看一次完整報告 → quiz-detail.html
```

### 階段四：行動轉化

```
用戶選擇任一推薦內容
    │
    ├─ 呼吸練習 → breath.html
    │   └─ 完成後獲得能量光點 +8%
    │
    ├─ 閱讀文章 → 內容頁面
    │   └─ 閱讀後推薦相關課程
    │
    ├─ 課程學習 → course-detail.html → player.html
    │   └─ 學習記錄自動更新
    │
    └─ AI 對話 → ai-chat.html
        └─ 持續陪伴與覺察引導
```

---

## 🆕 新增頁面

### 1. onboarding.html - 首次用戶引導

**功能**：
- ✅ 3 步驟歡迎流程
- ✅ 進度條顯示（1/3、2/3、3/3）
- ✅ 五境模型介紹
- ✅ 隱私保護說明
- ✅ 可跳過（但會記錄）

**技術實現**：
```javascript
// 使用 LocalStorage 追蹤狀態
localStorage.setItem('aqive_onboarding_completed', 'true');
```

**視覺設計**：
- 漸層背景（紫 → 粉）
- Blob 動畫
- 流暢的步驟切換
- 白色玻璃擬態卡片

---

### 2. recommendations.html - 智能推薦頁

**功能**：
- ✅ AI 覺察分析（基於五境弱勢維度）
- ✅ 個性化內容推薦
  - 快速練習（3 分鐘）
  - 閱讀文章（3 分鐘）
  - 深度課程（60 分鐘）
- ✅ 「為什麼推薦給你」解釋框
- ✅ 多個行動入口

**推薦邏輯**：
```
IF 情緒境 < 70% THEN
  推薦：呼吸練習、情緒覺察文章、情緒釋放課程
  
IF 身體境 < 70% THEN
  推薦：身體掃描、運動課程、睡眠引導
  
IF 心智境 < 70% THEN
  推薦：正念冥想、專注力訓練、思維模式課程
```

**視覺設計**：
- AI 分析卡片（藍紫漸層）
- 推薦理由框（淺色邊框 + icon）
- 行動按鈕（大、明顯、有層次）
- 最推薦項目有「⭐ 最推薦給你」標籤

---

## 🔄 修改的現有頁面

### 1. index.html - 主入口

**新增功能**：
```javascript
// 檢測首次用戶
const hasCompletedOnboarding = localStorage.getItem('aqive_onboarding_completed');

if (!hasCompletedOnboarding) {
  appFrame.src = 'onboarding.html';  // 首次用戶 → 引導
} else {
  appFrame.src = 'home.html';        // 老用戶 → 首頁
}
```

---

### 2. quiz-detail.html - 五境報告

**新增**：
- 「查看個人化推薦」按鈕（主要 CTA）
- 「直接進入首頁」按鈕（次要）

**修改前**：
```html
<button>開始 7 天覺察之旅</button>
```

**修改後**：
```html
<button>查看個人化推薦</button>  <!-- 主要 -->
<button>直接進入首頁</button>    <!-- 次要 -->
```

---

### 3. quiz-result.html - 測驗結果

**新增功能**：
```javascript
function viewReport() {
  const isFirstAssessment = !localStorage.getItem('aqive_first_assessment_completed');
  
  if (isFirstAssessment) {
    localStorage.setItem('aqive_first_assessment_completed', 'true');
    navigate('quiz-detail.html');  // 首次 → 看報告 → 推薦
  } else {
    navigate('quiz-detail.html');  // 老用戶 → 直接看報告
  }
}
```

---

## 📊 LocalStorage 狀態管理

| Key | 作用 | 設置時機 |
|-----|------|----------|
| `aqive_onboarding_completed` | 已完成引導 | onboarding.html 完成時 |
| `aqive_first_assessment_completed` | 已完成首次測驗 | quiz-result.html 第一次查看報告時 |
| `aqive_first_recommendation_seen` | 已查看推薦 | recommendations.html 載入時 |

---

## 🎨 設計亮點

### 1. 漸進式引導
- 不強迫用戶立即測驗
- 3 步驟循序漸進
- 隨時可跳過

### 2. AI 人性化表達
```
❌ 避免：「您的情緒境指數偏低。」（機械）
✅ 使用：「你的情緒境指數（68%）相對較低，顯示最近情緒有些波動。」（同理）
```

### 3. 推薦理由可見化
每個推薦都有「為什麼推薦給你」框：
- 📘 淺色背景 + icon
- 📝 清晰的理由說明
- 🎯 連結到個人狀態

### 4. 行動層次分明
```
立即行動（3分鐘）→ 閱讀了解（3分鐘）→ 深度學習（60分鐘）
```

---

## 📱 完整用戶體驗流程圖

```
┌─────────────────────────────────────────────┐
│          用戶首次打開 App                      │
└──────────────┬──────────────────────────────┘
               ↓
    ┌──────────────────────┐
    │  檢測 onboarding 狀態  │
    └──────┬───────┬─────────┘
           │       │
    首次用戶│       │老用戶
           ↓       ↓
   onboarding  home.html
       │
       ├─ Step 1: 歡迎
       ├─ Step 2: 五境說明
       └─ Step 3: 隱私
           ↓
       quiz.html（測驗）
           ↓
    quiz-result.html（動畫）
           ↓
    quiz-detail.html（報告）
       │
       ├─ 查看個人化推薦 ←─【主要路徑】
       │       ↓
       │  recommendations.html
       │       │
       │       ├─ 呼吸練習 → breath.html
       │       ├─ 閱讀文章 → 內容頁
       │       ├─ 學習課程 → course-detail.html
       │       └─ AI 陪伴 → ai-chat.html
       │           ↓
       └─ 直接進入首頁 → home.html
```

---

## 🧪 測試指南

### 測試首次用戶流程

1. **清除 LocalStorage**
```javascript
// 在瀏覽器 Console 執行
localStorage.clear();
```

2. **重新載入 index.html**
```
應該自動進入 onboarding.html
```

3. **完成引導流程**
```
Step 1 → Step 2 → Step 3 → 開始能量評估
```

4. **完成測驗**
```
quiz.html → quiz-result.html（3秒）→ quiz-detail.html
```

5. **查看推薦**
```
點擊「查看個人化推薦」→ recommendations.html
```

6. **驗證狀態**
```javascript
// 檢查 LocalStorage
console.log(localStorage.getItem('aqive_onboarding_completed')); // "true"
console.log(localStorage.getItem('aqive_first_assessment_completed')); // "true"
```

### 測試老用戶流程

1. **模擬老用戶**
```javascript
localStorage.setItem('aqive_onboarding_completed', 'true');
localStorage.setItem('aqive_first_assessment_completed', 'true');
```

2. **重新載入 index.html**
```
應該直接進入 home.html（不會看到引導）
```

---

## 📈 成效指標

### 用戶行為指標
- ✅ 首次用戶完成引導率
- ✅ 測驗完成率
- ✅ 推薦頁面停留時間
- ✅ 推薦內容點擊率
- ✅ 從推薦到行動的轉化率

### 推薦精準度
- ✅ 用戶是否完成推薦的練習
- ✅ 用戶是否報名推薦的課程
- ✅ 用戶能量指數變化

---

## 🚀 未來優化方向

### Phase 2（短期）
1. **動態推薦算法**
   - 根據用戶行為調整推薦權重
   - A/B 測試不同推薦策略

2. **推薦內容擴充**
   - 更多文章庫
   - 更多課程類型
   - 社群推薦（其他用戶也喜歡）

3. **推薦理由個性化**
   - 基於用戶測驗回答生成
   - 引用用戶的具體描述

### Phase 3（中期）
1. **智能追蹤**
   - 用戶完成推薦內容後自動追蹤效果
   - 「這個推薦對你有幫助嗎？」反饋機制

2. **推薦演化**
   - 根據用戶持續使用調整推薦
   - 「你已經完成呼吸練習 7 天，準備好挑戰進階了嗎？」

3. **協同過濾**
   - 「和你狀態相似的用戶也喜歡...」
   - 基於大數據的推薦優化

---

## 💡 關鍵設計決策

### Q: 為什麼不強制完成引導？
**A**: 尊重用戶選擇。有些用戶可能：
- 被朋友推薦，想直接體驗
- 時間緊迫，先快速看看
- 已經了解類似產品

讓用戶可以跳過，但記錄狀態，未來可以提示補完。

### Q: 為什麼推薦頁面要有這麼多解釋？
**A**: 建立信任。用戶需要知道：
- 為什麼系統推薦這個？
- 這個內容如何幫助我？
- 系統是否真的理解我？

透明的推薦理由 = 更高的轉化率。

### Q: 為什麼首次測驗後必看推薦？
**A**: 最佳時機點：
- 用戶剛完成測驗，動機最強
- 用戶剛看到自己的弱勢維度
- 用戶正在尋找「接下來該做什麼」

錯過這個時機，用戶可能流失。

---

## 📞 技術支援

如需測試或有任何問題，請參考：
- 完整流程：打開 `index.html`（清除 LocalStorage）
- 單獨測試：直接打開 `onboarding.html` 或 `recommendations.html`
- 狀態檢查：瀏覽器 Console → `localStorage`

---

**Flow E 實現完成！** ✨  
**總新增頁面**：2 個（onboarding + recommendations）  
**總修改頁面**：3 個（index + quiz-detail + quiz-result）  
**完整流程時間**：約 5-7 分鐘（引導 1 分 + 測驗 2 分 + 報告 1 分 + 推薦 2 分）

