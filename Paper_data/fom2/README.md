# Cavity Period 設計與分析專案

# Photonic Crystal Cavity Design & Optimization

本資料夾包含用於光子晶體腔 (Photonic Crystal Cavity) 設計、優化及物理特性分析的腳本與數據資料。

---

## 📐 設計參數 (Design Parameters)

### 1. 設計區域 (Design Region)
本設計的設計空間尺寸為：
$$(1\,\mu m, 1\,\mu m)$$

### 2. 品質因數 (Figure of Merit, FoM)
我們定義 $FoM(2)$ 用於衡量電場在特定空間內的集中程度，其公式如下：

$$FoM(2) = \frac{J_1}{J_2}$$

其中：
* **$J_1$ (目標集中區域):** $$J_1 = \frac{1}{N_{A_1 \text{ grid}}} \sum_{A_1} |E_y|^2$$
* **$J_2$ (參考對照區域):** $$J_2 = \frac{1}{N_{A_2 \text{ grid}}} \sum_{A_2} |E_y|^2$$

#### 區域尺寸定義 (Area Dimensions):
* $A_1 = (0.01\,\mu m, 0.01\,\mu m)$
* $A_2 = (0.01\,\mu m, 1\,\mu m)$

> [!NOTE]
> 關於 FoM 區域分佈的視覺化示意圖，如下  
![FoM 示意圖](Paper_data_and_Tutorial/Paper_data/figure_in_paper/fom2/plot_fom2.png)



### 3. 監測器設定 (Monitor Settings)
FoM Monitor 的物理尺寸大小設定為：
$$(0.1\,\mu m, 0.1\,\mu m)$$

---

## 🛠 使用說明
1.  確保模擬環境的網格解析度 (Mesh Resolution) 足以捕捉 $0.01\,\mu m$ 等級的場強變化。
2.  優化腳本會根據上述 $FoM(2)$ 定義進行梯度運算，以極大化電場在 $A_1$ 區域的佔比。

---

## 📂 檔案清單與功能說明

### 🛠️ 執行腳本 (Scripts)
* **`fom2.py`**: 核心執行腳本，用於執行設計與優化 Cavity Period 的模擬流程。
* **`dftscrp.py`**: 執行離散傅立葉轉換 (DFT) 運算，提取電磁場分量資訊。

### 📊 分析與繪圖 (Notebooks)
* **`fom_chang.ipynb`**: 讀取優化紀錄，繪製 FOM (Figure of Merit) 隨時間或迭代次數變化的趨勢圖。
* **`anlyze.ipynb`**: 計算並分析腔體的 **Q 值** (Quality Factor / Harmonic analysis)。
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