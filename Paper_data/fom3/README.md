# Photonic Crystal Cavity Design & Optimization (FoM ３)

> [!IMPORTANT]
> **Boundary Condition:** 本設計採用 **Non-periodic boundary condition** (例如 PML)，以模擬有限尺寸腔體的物理行為。


本資料夾包含用於光子晶體腔 (Photonic Crystal Cavity) 設計、優化及物理特性分析的腳本與數據資料。

---

## 📐 物理尺寸定義 (Physical Dimensions)

### 1. 設計區域尺寸 (Design Region Size)
在模擬環境中，允許結構變動的整體設計區域大小為：

$$
(1\,\mu m,\,1\,\mu m)
$$

### 2. 監測器尺寸 (FoM Monitor Size)
用於擷取電場數據並計算品質因數的監測器區域大小為：

$$(0.２\,\mu m,\,0.２\,\mu m)$$

---

## 🎯 Figure of Merit (FoM)

本設計目標在於極大化監測器範圍內的平均電場強度。**FoM(1)** 的定義如下：

$$
FoM(1) = \frac{1}{N_{\text{grid}}}\sum_{N_x,N_y} |E_y|^2
$$

### 參數說明：
* **$|E_y|^2$**: 代表在特定網格點上的 $E_y$ 極化電場強度平方。
* **$N_{\text{grid}}$**: 代表監測器區域 $(0.1\,\mu m \times 0.1\,\mu m)$ 內的總網格點數量。
* **物理意義**: 此數值代表了目標小區域內的 **平均電場能量密度**。

---

## 📂 檔案清單與功能說明

### 🛠️ 執行腳本 (Scripts)
* **`fom3.py`**: 核心執行腳本，用於執行設計與優化 Cavity Period 的模擬流程。
* **`dftscrp.py`**: 執行離散傅立葉轉換 (DFT) 運算，提取電磁場分量資訊。

### 📊 分析與繪圖 (Notebooks)
* **`fom_chang.ipynb`**: 讀取優化紀錄，繪製 FOM (Figure of Merit) 隨時間或迭代次數變化的趨勢圖。
* **`harminv.py`**: 計算並分析腔體的 **Q 值** (Quality Factor / Harmonic analysis)。
    
    使用以下命令在背景執行 `harminv.py`：
    ```bash
    nohup mpirun -np 20 python harminv.py > logharm.txt 2>&1 &
    ```
---
**💡 提示**：
* `-np 20` 代表使用 20 個 CPU 核心進行並行運算。
* `> logharm.txt 2>&1` 會將所有輸出與錯誤訊息紀錄至 `logharm.txt`。
* 末尾的 `&` 符號會讓程式在系統後台執行，不會占用終端機視窗。

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