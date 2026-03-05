
本資料夾包含光子晶體腔 (Photonic Crystal Cavity) 設計、優化及物理特性分析的腳本與數據。

**本設計參數**  
$ \text{cell\_size} = (0.8\,\mu\text{m}, 0.8\,\mu\text{m}) $

**Figure of Merit**  
$ \text{FoM}(1) = \frac{1}{N_{\text{grid}}} \sum_{N_x,N_y} |E_y|^2 $

**FoM monitor 大小**  
$ \text{cell\_size} = (0.2\,\mu\text{m}, 0.2\,\mu\text{m}) $

## 📂 檔案清單與功能說明

### 🛠️ 執行腳本 (Scripts)
* **`casea.py`**: 核心執行腳本，用於執行設計與優化 Cavity Period 的模擬流程。
* **`dftscrp.py`**: 執行離散傅立葉轉換 (DFT) 運算，提取電磁場分量資訊。

### 📊 分析與繪圖 (Notebooks)
* **`fom_chang.ipynb`**: 讀取優化紀錄，繪製 FOM (Figure of Merit) 隨時間或迭代次數變化的趨勢圖。
* **`harm.ipynb`**: 計算並分析腔體的 **Q 值** (Quality Factor / Harmonic analysis)。
* **`replot_field.ipynb`**: 
    * 重繪 DFT 場圖分布。
    * 計算 **模式體積 (Mode Volume, $V_{\mathrm{IPR}}$)**。

---

## 🔬 物理公式：Mode Volume ($V_{\mathrm{IPR}}$)

在模式分析中，我們使用 **IPR (Inverse Participation Ratio)** 定義來計算模式體積：

$$
V_{\mathrm{IPR}} = \left[ \frac{\iiint_{\Omega} \lvert \mathbf{E}(\mathbf{r}) \rvert^{4}\, \mathrm{d}V}{\left(\iiint_{\Omega} \lvert \mathbf{E}(\mathbf{r}) \rvert^{2}\, \mathrm{d}V\right)^{2}} \right]^{-1}
$$



---

## 📁 資料目錄 (data/)

所有的模擬產出與設計結果均儲存於 `data/` 資料夾中：

| 檔案名稱 | 內容說明 |
| :--- | :--- |
| **`eval_history.npy`** | 紀錄優化過程中每一代的 FOM 數值。 |
| **`fields_ref.npz`** | 參考場圖（無結構之純矽波導，Background field）。 |
| **`fields_struct.npz`** | 含有結構設計後的電磁場分布圖。 |
| **`final_design.npy`** | 最終優化完成的結構幾何參數。 |

---