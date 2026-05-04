# Screen Mirror (螢幕鏡像監視工具)

![OS](https://img.shields.io/badge/OS-Windows-blue?style=flat-square&logo=windows)
![Language](https://img.shields.io/badge/Language-AutoHotkey_v2-green?style=flat-square&logo=autohotkey)
![Locale](https://img.shields.io/badge/Locale-正體中文-orange?style=flat-square)
![License](https://img.shields.io/badge/License-GPL_v3-red?style=flat-square)


**Screen Mirror** 是一款基於 AutoHotkey v2 開發的輕量化螢幕監視工具，專為多螢幕環境設計。它能將指定的螢幕畫面即時鏡像至一個可縮放的視窗中，讓您在操作主螢幕時，也能輕鬆監視副螢幕或遠端顯示器的動態。

---

## 🌟 技術亮點

*   **極致輕量**：單一執行檔即可運行，啟動速度極快，不佔用多餘系統資源。
*   **Per-Monitor V2 DPI 感知**：完美支援 Windows 10/11 的多螢幕縮放，無論鏡像視窗移至哪個螢幕，畫面皆能保持精確不模糊。
*   **物理像素渲染**：底層採用 Win32 GDI 引擎，直接存取顯示器物理像素，確保鏡像內容與來源完全一致。
*   **智慧座標換算**：自動處理 Windows 邏輯座標與物理座標的換算，支援跨螢幕的即時更新。
*   **低延遲體驗**：針對渲染循環進行優化，提供流暢的視覺反饋。

---

## 🛠️ 主要功能

*   **多螢幕支援**：自動偵測系統所有顯示器，並可透過托盤選單快速開啟指定螢幕的鏡像。
*   **等比例縮放**：支援滑鼠自由拖曳調整大小，並始終保持來源螢幕的長寬比。
*   **全螢幕切換**：支援雙擊視窗快速切換全螢幕與還原模式。
*   **最上層顯示**：可自由切換視窗是否置頂，方便在操作其他程式時持續監視。
*   **滑鼠指標鏡像**：視窗內會同步顯示來源螢幕的滑鼠位置與圖示狀態。

---

## ⌨️ 快捷鍵指南

| 快捷鍵 | 功能說明 |
| :--- | :--- |
| **F9** | 將視窗縮放至 **100%** (原始解析度) |
| **F10** | 將視窗縮放至 **50%** |
| **按兩下左鍵** | 切換 **全螢幕 / 還原視窗** |
| **按一下右鍵** | 顯示快速功能表 (選單) |
| **Alt + F4** | 關閉當前鏡像視窗 |

---

## 🚀 系統需求

*   **作業系統**：Windows 10 x64 / Windows 11 或更高版本
*   **權限要求**：建議以管理員權限執行以獲得最佳相容性
*   **語言環境**：正體中文 (繁體中文)

---

## ⚖️ 授權協議

本專案採用 [GPL-3.0 License](LICENSE) 開源協議。您可以自由地使用、修改及散佈本軟體，但請務必遵守協議中的相關條款。

---

## 👨‍💻 關於開發者

*   **設計開發**：林彥丞 (Yancheng Lin)
*   **電子郵件**：[lin.yancheng@outlook.com](mailto:lin.yancheng@outlook.com)
*   **GitHub**：[ArtLife-Software](https://github.com/ArtLife-Software)
*   **Facebook 社群**：[O & C VBA 研究社](https://www.facebook.com/groups/vba.club)
*   **所在地**：中華民國 台灣

---

> **開發初衷**：本工具旨在解決多螢幕使用者在視角切換上的不便，提供一個最純粹、高效的監視解決方案。如果您覺得實用，歡迎給予 Star 鼓勵！
