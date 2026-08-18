# Citybus GTC PIDS Simulator (城巴機場地面運輸中心旅客資訊顯示屏模擬器)

這是一個基於 HTML、JavaScript 與 Electron 開發的城巴機場地面運輸中心（GTC）旅客資訊顯示屏（PIDS）模擬器。透過直接串接香港政府「資料一線通（DATA.GOV.HK）」的城巴開放數據 API，提供高還原度、低延遲的往市區方向實時班次資訊。

---

## ✨ 核心特色

* **自動尋址引擎**：內建智慧掃描，自動校準機場總站各路線的真實 Stop ID（涵蓋 `001850`、`001824` 等多個月台），無需手動維護站位。
* **精準過濾機制**：嚴格過濾反方向（如往機場、博覽館、東涌）的班次，確保顯示屏僅提供「往市區」的有效出發班次。
* **實時狀態追蹤**：
  * **實時 GPS 圖示**：E 線班次於 3 分鐘內抵達時，自動於左上角亮起實時 `GPS.svg` 追蹤圖示。
  * **即將抵達提示**：倒數至 0 分鐘時自動切換為 `Arr` 狀態。
* **高還原度 UI**：完美復刻實體 PIDS 的深藍底亮黃字配色、Cityflyer 專屬向量標誌（`Cityflyer_logo.svg`）以及底部官方安全提示跑馬燈。
* **跨平台桌面應用程式**：支援透過 GitHub Actions 及 Electron Forge，自動編譯為 Windows (`.exe`)、macOS (`.dmg` / `.app`) 及 Linux (`.deb` / `.rpm`) 的獨立應用程式。

---

## 🚏 支援路線 (往市區方向)

系統自動收錄並監控以下所有由機場開出的城巴路線：

| 系列 | 路線編號 |
| :--- | :--- |
| **Cityflyer 機場快線** | A10, A11, A12, A17, A20, A21, A22, A23, A25, A26, A28, A29 |
| **北大嶼山對外路線 (E線)** | E11, E11A, E11B, E21, E21C, E21D, E22, E22A, E22C, E23, E23A |
| **通宵機場／特快路線 (NA/N線)** | NA10, NA11, NA12, NA20, NA21, NA29, N11, N21, N23, N26, N29 |

---

## 🚀 安裝與執行

### 方法一：下載已編譯的桌面應用程式（推薦）
請前往本儲存庫的 **[Releases]** 頁面，下載適用於您作業系統的最新發布版本。

### 方法二：網頁瀏覽器直接開啟
本專案的顯示核心為純前端網頁架構，您可以直接在瀏覽器中開啟 `index.html`，即可全螢幕運行模擬器。

### 方法三：本地端開發與編譯
請確保您的電腦已安裝 [Node.js](https://nodejs.org/)。

```bash
# 1. 複製專案原始碼
git clone [https://github.com/kenyip0244/Citybus-GTC-PIDS-Simulator.git](https://github.com/kenyip0244/Citybus-GTC-PIDS-Simulator.git)
cd Citybus-GTC-PIDS-Simulator

# 2. 安裝依賴套件
npm install

# 3. 本地端即時測試運行
npm start

# 4. 手動打包應用程式
npm run make

```

---

## 🖱️ 隱藏操作指南

* **切換全螢幕**：雙擊畫面中央的班次顯示區域即可切換全螢幕模式。
* **強制重置站位快取**：雙擊頂部深藍色標題列（「路線 Route」區域），即可強制清除自動尋址引擎的快取並重新掃描站位。

---

## 📂 專案檔案結構

```text
Citybus-GTC-PIDS-Simulator/
├── .github/workflows/
│   └── build.yml          # GitHub Actions 跨平台 CI/CD 自動編譯腳本
├── .gitignore             # Git 忽略清單 (排除 node_modules 等編譯檔案)
├── Cityflyer_logo.svg     # 城巴機場快線標誌向量圖
├── GPS.svg                # 實時 GPS 追蹤向量圖示
├── index.html             # PIDS 主介面與即時資料處理核心邏輯
├── main.js                # Electron 主行程入口檔案
├── package.json           # Node.js 專案設定與應用程式資訊
└── README.md              # 專案說明文件

```

---

## ⚠️ 聲明

* 本專案使用的實時班次資料來自香港政府 [資料一線通 (DATA.GOV.HK)](https://data.gov.hk/) 及城巴開放數據 API。
* 本顯示屏為模擬器性質，僅供學術交流與程式開發參考，實際到站時間請以城巴官方應用程式或現場實際情況為準。

```

```
