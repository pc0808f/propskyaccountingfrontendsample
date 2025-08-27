# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 專案概述

這是一個單頁面 HTML 應用程式，用於顯示企業會計後端數據的視覺化儀表板。專案名為「後端待辦事項儀表板」，使用繁體中文界面。

## 技術架構

- **前端技術**: 純 HTML + JavaScript + CSS
- **樣式框架**: Tailwind CSS (透過 CDN)
- **字型**: Inter + Noto Sans TC (透過 Google Fonts)
- **資料處理**: 前端 JavaScript 模擬數據生成

## 檔案結構

```
propskyaccountingfrontendsample/
└── sample.html - 主要的儀表板頁面
```

## 核心功能模組

### 1. 資料類型
- **JJBB 刷卡資料**: 包含營收、金流手續費、日租費、實際入帳等財務指標
- **開心小卡營業資料**: 包含幣量、出獎次數、電子支付次數等遊戲營運數據  
- **中華電信資料**: 待開發的功能區塊

### 2. API 端點建議
專案中標明了建議的 API 端點：
- JJBB 資料: `/api/jjbb/daily-summary`
- 開心小卡資料: `/api/happycard/daily-stats`

### 3. 主要 JavaScript 函數
- `generateJjbbTableData()`: 產生 JJBB 模擬數據
- `generateHappyCardTableData()`: 產生開心小卡模擬數據
- `renderJjbbTable()`: 渲染 JJBB 資料表
- `renderHappyCardTable()`: 渲染開心小卡資料表
- `updatePageData()`: 主要資料更新邏輯
- `formatCurrency()`: 貨幣格式化
- `formatNumber()`: 數字格式化

## 場地配置

### JJBB 場地
- 信義A8館
- 南西誠品  
- 板橋大遠百
- 台中新光
- 高雄夢時代

### 開心小卡場地
- 西門萬年
- 士林夜市
- 逢甲商圈

## 開發注意事項

- 所有顯示文字應使用繁體中文
- 資料篩選支援「所有場個別」和「所有場加總」兩種模式
- 頁面每 10 秒自動更新一次模擬數據
- 使用 Tailwind CSS 類別進行樣式設計
- 響應式設計適配桌面和行動裝置

## 執行方式

由於這是純 HTML 檔案，可以：
1. 直接在瀏覽器中開啟 `sample.html`
2. 使用任何靜態檔案伺服器提供服務