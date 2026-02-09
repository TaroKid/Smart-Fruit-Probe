# Smart Fruit Probe 專案協作公約

為了確保兩人合作順利，避免檔案衝突、數據遺失或「不知道現在進度到哪」的狀況，請務必遵守以下開發規範。

---

## 1. 🔴 最高準則 (The Golden Rules)

1.  **嚴禁直接 Push 到 `main` 分支**
    * `main` 分支是專案的「正式發布版」，必須保證上面的程式碼隨時都能編譯通過、電路圖都是正確的。
    * 所有修改都必須透過 **開新分支 (Branch)** -> **提交 (Commit)** -> **發 PR (Pull Request)** 的流程進入 `main`。

2.  **禁止捏造實驗數據**
    * `data/raw/` 裡面的原始數據 (CSV/TXT) 一旦產出，**禁止手動修改數值**。
    * 如果數據測爛了，請在檔名標註 `_failed`，不可直接改數字。

---

## 2. 🌿 分支管理 (Git Flow)

請依照你要做的事情類別，使用以下命名規則開設分支：

| 類別 | 分支命名範例 | 說明 |
| :--- | :--- | :--- |
| **新增功能** | `feat/adc-reading` | 寫新的程式功能、設計新電路 |
| **硬體相關** | `hw/op-amp-simulation` | LTspice 模擬、PCB 繪製、機構設計 |
| **修復錯誤** | `fix/sensor-noise` | 修正 Bug、解決電路雜訊 |
| **文件撰寫** | `docs/week1-log` | 寫實驗日誌、更新 README、規格書 |
| **數據處理** | `data/melon-test` | 上傳新的實驗數據 |

**操作流程：**
1.  `git checkout -b feat/你的功能名稱`
2.  開發、存檔
3.  `git add .`
4.  `git commit -m "清楚的訊息"`
5.  `git push origin feat/你的功能名稱`
6.  到 GitHub 發起 **Pull Request (PR)**
7.  **通知組員 Review** (口頭或訊息)，確認沒問題後 **Merge**。

---

## 3. 📝 Commit 訊息規範

請使用 **[類別]: 說明** 的格式，讓隊友一眼看懂你做了什麼。

* `feat`: 新增軟體功能或電路模組 (Feature)
* `fix`: 修復 Bug (Fix)
* `docs`: 僅修改文件或日誌 (Documentation)
* `style`: 修改格式（不影響程式邏輯，如縮排）
* `refactor`: 程式碼重構
* `test`: 增加測試代碼或測試數據
* `hw`: 硬體相關變更 (Hardware)

**範例：**
* ✅ `feat: 完成 LM358 放大電路 LTspice 模擬`
* ✅ `fix: 修正 ADC 讀取數值飄移問題`
* ✅ `docs: 新增 2/10 苦瓜測試日誌`
* ❌ `update code`, `修正`, `123` `(無意義訊息禁止)`

---

## 4. 📂 檔案存放守則

為了保持專案乾淨，請嚴格遵守目錄結構：

* **規格書 (Datasheets):**
    * 一律放在 `docs/datasheets/`。
    * 檔名請包含型號，例如 `LM358_TI.pdf`，不要叫 `spec.pdf`。
* **電路模擬 (Simulation):**
    * 放在 `hardware/simulation/`。
    * 主要模擬檔請標註版本，如 `Amplifier_v1.asc`。
* **程式碼 (Firmware/Software)(待加入):**
    * MCU 韌體放 `firmware/`。
    * Python 分析腳本放 `software/data_analysis/`。
* **測試數據 (Data):**
    * 原始檔放 `data/raw/`。
    * 分析後的圖表或整理過的 Excel 放 `data/processed/`。

---

## 5. 🗓️ 進度日誌 (Dev Logs)

**這非常重要！** 這是我們寫結案報告的救命稻草。

* **位置：** `docs/logs/`
* **頻率：** 每次有「實質產出」（如：測了一組數據、焊好一塊板子、解決一個 Bug）都要寫。
* **格式：** 檔名 `YYYYMMDD_主題_姓名.md`
* **內容模板：**
    ```markdown
    ##  本日目標
    
    ##  實作過程 / 實驗數據
    (附上照片或截圖更好)
    
    ##  遇到的問題
    
    ##  下一步計畫
    ```

---

## 6. ⚠️ 硬體安全須知

* 更換電路接線時，務必**先斷電**。
* 長時間通電測試前，請先用電表檢查 VCC 與 GND 是否短路。
* 若燒毀元件，請在日誌中記錄原因（過壓、反接、過流），作為「失敗經驗」寫進報告。

---

## 7. 補充

* logs和commit comment可使用英文或中文撰寫，盡量避免生難字。

---
