# BlockHouse_Internship
This repo includes OFI feature construction (Best-Level, Multi-Level, Integrated, Cross-Asset) based on equity market data and related research. It also contains a LaTeX PDF with conceptual answers.
# OFI Feature Construction

This notebook calculates Order Flow Imbalance (OFI) features based on the methodology described in the paper 'Cross-Impact of Order Flow Imbalance in Equity Markets' and the requirements of the Trial Task.

**Data:** `first_25000_rows.csv`

**Features Calculated:**
1.  Best-Level OFI (`ofi_best`) - Approximation based on price/size changes.
2.  Multi-Level OFI (`ofi_multi`) - Sum across top 5 levels (using approximation).
3.  Integrated OFI (`ofi_integrated`) - Weighted sum across top 5 levels (using linear decay weights as approximation instead of PCA).
4.  Cross-Asset OFI (`ofi_cross_asset`) - Simulated using lagged best-level OFI.

**Note on Approximations:** The OFI calculations here are simplified versions using `bid_px_XX` and `ask_px_XX` columns. Accurate calculation often requires full event reconstruction. Integrated OFI uses linear weights instead of PCA weights from the paper. Cross-Asset OFI is simulated due to lack of data for a second asset.

**Data Handling:** Timestamps are made unique (keeping last entry), data is resampled to 1-second frequency using forward-fill (limited gap filling), and rows with missing essential price data (best bid/ask) after resampling are dropped before calculations.

**Steps of Execution**

 1. Download the first_25000_rows.csv file as the input dataset.
 2. Run the ofi_feature_construction-checkpoint.ipynb notebook. 
 3. Upon execution, the notebook will automatically generate the ofi_features_output.csv file.
 4. The code will then visualize the constructed OFI features based on the generated output.
 5. Accuracy metrics are calculated and displayed.
