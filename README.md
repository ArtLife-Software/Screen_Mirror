# Screen Mirror

![OS](https://img.shields.io/badge/OS-Windows_10%2F11-blue?style=flat-square&logo=windows)
![Language](https://img.shields.io/badge/Language-VB.NET-purple?style=flat-square&logo=dotnet)
![Framework](https://img.shields.io/badge/.NET_Framework-4.8-512BD4?style=flat-square&logo=dotnet)
![Rendering](https://img.shields.io/badge/Rendering-DXGI%20%2B%20Direct2D%20(GPU)-brightgreen?style=flat-square)
![Locale](https://img.shields.io/badge/Locale-正體中文-orange?style=flat-square)
![License](https://img.shields.io/badge/License-PolyForm--NC_1.0.0-red?style=flat-square)
![Latest Release](https://img.shields.io/github/v/release/ArtLife-Software/Screen_Mirror?style=flat-square&color=blue)
![Downloads](https://img.shields.io/github/downloads/ArtLife-Software/Screen_Mirror/total?style=flat-square&logo=github)

**Screen Mirror** 是一款專為多螢幕環境設計的輕量化螢幕鏡像工具。它能將指定的螢幕畫面即時鏡像至一個可縮放的視窗中，讓您在操作主螢幕時，也能輕鬆監視副螢幕或遠端顯示器的動態。

從 2.0.0 版起，渲染引擎全面改寫：由 GDI 換成 **DXGI Desktop Duplication + Direct2D**，畫面資料全程留在顯卡端處理，不再經過 CPU 逐像素搬移。

---

## 🌟 技術亮點

*   **GPU 硬體渲染**：透過 DXGI Desktop Duplication API 直接在顯卡端擷取畫面，搭配 Direct2D 做縮放與合成，CPU 幾乎不參與像素搬移。
*   **事件驅動更新**：畫面有變化才重繪（`AcquireNextFrame`），不是固定頻率輪詢；靜止畫面時幾乎零負擔，動態畫面時流暢度不受人為上限限制。
*   **Per-Monitor V2 DPI 感知**：完美支援 Windows 10/11 的多螢幕縮放，無論鏡像視窗移至哪個螢幕，畫面皆能保持精確不模糊。
*   **物理像素座標系**：DXGI 本身即物理像素，搭配 PerMonitorV2 宣告後，整條渲染管線不需要額外的邏輯／物理座標換算。
*   **EDID 螢幕友善名稱**：透過 WMI 解析螢幕韌體內建的 EDID 資訊，托盤選單顯示的是實際廠牌型號，而不是 `\\.\DISPLAY1` 這種裝置代碼。
*   **GPU 端游標疊加**：游標圖示轉換後快取為 Direct2D 點陣圖，每幀純 GPU 合成，不逐幀呼叫 GDI。

### 📊 實測效能對比（GDI 版 vs. GPU 版）

| 情境 | GDI 版 CPU | GPU 版 CPU | GPU 使用 |
| :--- | :---: | :---: | :---: |
| 動態畫面 | 16.2% | **2.2%** | 顯卡 3D 引擎 5.8% |
| 靜態畫面 | 14.9% | **0.6%** | 顯卡 3D 引擎 4.0% |

GDI 版不論畫面是否變化都固定輪詢重繪，CPU 用量幾乎沒有差別；GPU 版靜止時幾乎不耗資源，且 Windows 系統回報的耗電量評等也由「非常高」降為「低／非常低」。

---

## 🛠️ 主要功能

*   **多螢幕支援**：自動偵測系統所有顯示器（含 EDID 友善名稱），透過托盤選單快速開啟指定螢幕的鏡像。
*   **等比例縮放**：支援滑鼠自由拖曳調整大小，並始終保持來源螢幕的長寬比。
*   **全螢幕切換**：支援雙擊視窗快速切換全螢幕與還原模式。
*   **最上層顯示**：可自由切換視窗是否置頂，方便在操作其他程式時持續監視。
*   **滑鼠指標鏡像**：視窗內會同步顯示來源螢幕的滑鼠位置與圖示狀態（GPU 端合成）。
*   **快速右鍵選單**：視窗內右鍵可快速縮放、切換全螢幕、置頂、關閉。

---

## ⌨️ 快捷鍵指南

| 快捷鍵 | 功能說明 |
| :--- | :--- |
| **F9** | 將視窗縮放至 **100%**（原始解析度） |
| **F10** | 將視窗縮放至 **50%** |
| **按兩下左鍵** | 切換 **全螢幕 / 還原視窗** |
| **按一下右鍵** | 顯示快速功能表（選單） |
| **Alt + F4** | 關閉當前鏡像視窗 |

---

## 🚀 系統需求

*   **作業系統**：Windows 10 x64 / Windows 11 或更高版本
*   **執行環境**：.NET Framework 4.8（Windows 10/11 隨系統更新內建，免另外安裝）
*   **顯示卡**：支援 Direct3D 11 的顯示卡（市面上主流內顯／獨顯皆符合）
*   **權限要求**：需以系統管理員權限執行（啟動時會自動跳出 UAC 提示）
*   **語言環境**：正體中文（繁體中文）

---

## ⚖️ 授權協議

本專案採用 [PolyForm Noncommercial License 1.0.0](Screen_Mirror_License.txt) 授權條款，僅限**非商業用途**。您可以自由地使用、複製及散佈本軟體，但不得用於商業目的，亦不得進行逆向工程。詳細條款請參閱隨附的授權檔案，或參閱[英文原文](https://polyformproject.org/licenses/noncommercial/1.0.0)。

---

## 👨‍💻 關於開發者

*   **設計開發**：林彥丞 (Yancheng Lin)
*   **電子郵件**：[lin.yancheng@outlook.com](mailto:lin.yancheng@outlook.com)
*   **GitHub**：[ArtLife-Software](https://github.com/ArtLife-Software)
*   **Facebook 社群**：[O & C VBA 研究社](https://www.facebook.com/groups/vba.club)
*   **所在地**：中華民國 台灣

---

> **開發初衷**：本工具旨在解決多螢幕使用者在視角切換上的不便，提供一個最純粹、高效的監視解決方案。2.0.0 版換上 GPU 渲染引擎後，實測 CPU 用量降到原本的十分之一左右，待機幾乎零負擔。如果您覺得實用，歡迎給予 Star 鼓勵！
