# PropSky 會計後端數據指標儀表板

## 📋 專案概述

這是一個**前端設計參考頁面**，展示 PropSky 會計系統的後端數據視覺化儀表板。本專案為前端工程師和 UI/UX 設計師提供完整的介面設計範例，包含數據展示、篩選功能和響應式佈局。

## 🎯 目標用戶

- **前端工程師**: 參考介面實作和 JavaScript 邏輯
- **UI/UX 設計師**: 了解數據儀表板的設計模式和互動流程
- **產品經理**: 檢視功能需求和用戶體驗流程

## ✨ 功能特色

### 📊 數據模組
- **JJBB 刷卡資料**: 營收、手續費、日租費、實際入帳等財務指標
- **開心小卡營業資料**: 幣量、出獎次數、電子支付次數等遊戲營運數據
- **中華電信資料**: 預留擴展功能區塊

### 🎛️ 互動功能
- 多頁籤切換 (Tab Navigation)
- 場地篩選 (單一場地/所有場地個別/所有場地加總)
- 日期範圍查詢
- 資料表格展示
- 模擬數據自動更新 (每 10 秒)
- 報表匯出按鈕 (UI Only)

### 📱 響應式設計
- 支援桌面和行動裝置
- 使用 Tailwind CSS 框架
- 彈性網格佈局和適應式組件

## 🔧 技術架構

```
技術棧:
├── HTML5 - 語義化結構
├── CSS3 - 使用 Tailwind CSS 框架
├── JavaScript (ES6+) - 原生 JS，無外部依賴
└── Google Fonts - Inter + Noto Sans TC 字體
```

## 🗂️ 檔案結構

```
propsky-accounting-dashboard/
├── index.html          # 主要儀表板頁面
├── CLAUDE.md           # Claude Code 開發指南
├── README.md           # 專案說明 (本檔案)
└── .gitignore         # Git 忽略檔案設定
```

## 🚀 快速開始

### 本地預覽
```bash
# 直接用瀏覽器開啟
open index.html

# 或使用簡單的 HTTP 伺服器
python -m http.server 8000
# 然後開啟 http://localhost:8000
```

### GitHub Pages 部署
1. Fork 或 Clone 此專案
2. 在 GitHub 儲存庫設定中啟用 Pages
3. 選擇 `main` 分支作為來源
4. 網站將自動部署到 `https://您的用戶名.github.io/儲存庫名稱`

## ⚠️ 重要注意事項

### 🔴 資料安全
- **此為前端展示頁面，所有資料均為模擬數據**
- **請勿在此頁面中加入真實的營運數據或敏感資訊**
- 實際部署時需要移除所有模擬數據產生邏輯

### 🔧 開發注意事項
- **API 整合**: 頁面已預留 API 端點建議，實際開發時需要替換模擬數據
- **資料格式**: 請確保後端 API 回傳的資料結構與前端預期格式一致
- **錯誤處理**: 目前缺少網路錯誤和空資料的處理邏輯
- **載入狀態**: 實際開發時需要加入載入指示器和骨架屏

### 🎨 UI/UX 考量
- **繁體中文介面**: 所有文字內容應保持繁體中文
- **色彩系統**: 使用 Tailwind CSS 預設調色盤，可根據品牌需求調整
- **字型選擇**: Inter (英文) + Noto Sans TC (中文) 組合
- **互動回饋**: 需要加強按鈕點擊和狀態變化的視覺回饋

### 🔒 資訊安全
- 請確保生產環境中移除所有開發用的註解和模擬邏輯
- 實作適當的輸入驗證和 XSS 防護
- 使用 HTTPS 和適當的 CSP 標頭

## 📊 建議的 API 端點

```javascript
// JJBB 刷卡資料
GET /api/jjbb/daily-summary?site={site}&start_date={date}&end_date={date}

// 開心小卡營業資料  
GET /api/happycard/daily-stats?site={site}&start_date={date}&end_date={date}

// 中華電信資料 (待定義)
GET /api/cht/data?site={site}&start_date={date}&end_date={date}
```

## 📝 授權

此專案為內部開發參考用途，請遵循公司內部的程式碼使用規範。

---

**注意**: 這是一個設計參考頁面，實際部署前請確保所有敏感資訊已被移除，並實作適當的安全防護措施。