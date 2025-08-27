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

## 📊 實際 API 整合指引

### 🔗 API 基礎資訊
- **API 文檔**: https://smartpay.propskynet.com/docs
- **基礎 URL**: `https://smartpay.propskynet.com`
- **認證方式**: OAuth2 Bearer Token

### 🏪 與目前頁面對應的 API 端點

#### 1. JJBB 刷卡資料 → 卡機管理 API
```javascript
// 取得卡機列表 (對應 JJBB 機台資料)
GET /api/cardmachines
Query Parameters:
- page: 頁數
- per_page: 每頁筆數
- store_id: 店家 ID (對應場地篩選)
- start_date: 開始日期
- end_date: 結束日期

// 回應資料結構對應前端欄位:
{
  "data": [
    {
      "id": "machine_id",           // → 機台 ID
      "store_name": "site_name",    // → 場地名稱  
      "daily_revenue": "gross_revenue",     // → 營收總額
      "transaction_fee": "gateway_fee",     // → 金流手續費
      "daily_rent": "daily_rent",           // → 日租費
      "net_amount": "net_settlement",       // → 實際入帳總額
      "transaction_count": "txn_count",     // → 交易次數
      "settlement_date": "settlement_date"  // → 結算日期
    }
  ]
}
```

#### 2. 開心小卡營業資料 → 娃娃機管理 API  
```javascript
// 取得娃娃機統計資料 (對應開心小卡資料)
GET /api/claw-machines
Query Parameters:
- page: 頁數
- per_page: 每頁筆數  
- store_id: 店家 ID
- start_date: 開始日期
- end_date: 結束日期

// 回應資料結構對應前端欄位:
{
  "data": [
    {
      "id": "machine_id",              // → 機台 ID
      "store_name": "site_name",       // → 場地名稱
      "coin_count": "coin_count",      // → 幣量
      "payout_count": "payout_count",  // → 出獎次數
      "epay_count": "epay_count",      // → 電子支付次數
      "gift_rounds": "gift_rounds",    // → 贈獎局次數
      "free_rounds": "free_rounds",    // → 免費局次數
      "settlement_date": "settlement_date"
    }
  ]
}
```

#### 3. 店家資料 → 場地篩選選項
```javascript
// 取得店家列表 (用於場地篩選下拉選單)
GET /api/stores
Response:
{
  "data": [
    {
      "id": 1,
      "name": "信義A8館",
      "status": "active"
    }
  ]
}
```

### 🔧 前端工程師實作建議

#### API 整合步驟
1. **認證處理**: 實作 OAuth2 token 管理
2. **資料映射**: 將 API 回應映射到前端資料格式
3. **錯誤處理**: 加入 API 失敗和網路錯誤處理
4. **分頁處理**: 實作資料分頁載入
5. **篩選邏輯**: 整合店家篩選和日期範圍查詢

#### 範例實作 (JavaScript)
```javascript
// 範例: 取得 JJBB 資料的函數
async function fetchJjbbData(filters = {}) {
  const params = new URLSearchParams({
    page: 1,
    per_page: 25,
    ...filters
  });
  
  try {
    const response = await fetch(`https://smartpay.propskynet.com/api/cardmachines?${params}`, {
      headers: {
        'Authorization': `Bearer ${getAccessToken()}`,
        'Content-Type': 'application/json'
      }
    });
    
    if (!response.ok) throw new Error('API request failed');
    
    const data = await response.json();
    return mapToFrontendFormat(data.data);
  } catch (error) {
    console.error('Failed to fetch JJBB data:', error);
    return [];
  }
}

// 資料映射函數
function mapToFrontendFormat(apiData) {
  return apiData.map(item => ({
    settlement_date: item.settlement_date,
    site_name: item.store_name,
    machine_id: item.id,
    gross_revenue: item.daily_revenue || 0,
    gateway_fee: item.transaction_fee || 0,
    daily_rent: item.daily_rent || 0,
    net_settlement: item.net_amount || 0,
    txn_count: item.transaction_count || 0
  }));
}
```

### ⚠️ API 整合注意事項
1. **資料對應**: 目前頁面的模擬欄位已對應實際 API 結構
2. **認證 Token**: 需要實作 OAuth2 認證流程
3. **分頁處理**: API 支援分頁，需要處理大量資料載入
4. **錯誤狀態**: 加入 loading、error 和 empty 狀態處理
5. **資料快取**: 考慮實作適當的資料快取策略

### 📈 額外可用的 API 功能
- **Excel 匯出**: `/api/cardmachines/export` - 支援報表匯出功能
- **批量操作**: 支援 Excel 批量上傳和更新
- **即時狀態**: 娃娃機連線狀態即時更新
- **財務統計**: `/api/accounting` - 詳細財務報表

## 📝 授權

此專案為內部開發參考用途，請遵循公司內部的程式碼使用規範。

---

**注意**: 這是一個設計參考頁面，實際部署前請確保所有敏感資訊已被移除，並實作適當的安全防護措施。