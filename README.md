# 環境安裝
1. 先在window11系統上安裝好anaconda
2. 打開anaconda的終端機
3. 進入AICUP.yml所在的目錄
4. 輸入下列程式碼建立虛擬環境
```shell=
conda env create -f AICUP.yml
```
5. 輸入下列程式碼進去虛擬環境
```shell=
conda activate AICUP
```

# 棋力模仿
1. Dan
    1. 模型架構如下圖
    ![Dan_Model](https://hackmd.io/_uploads/rkDMNpOra.png)
    ![Dan_input_block](https://hackmd.io/_uploads/Hy4QVa_Ba.png)
    ![Dan_basic_block](https://hackmd.io/_uploads/r1cXE6OSp.png)
    2. 執行順序： Dan_Adam.ipynb->Dan_SGD1.ipynb->Dan_SGD2.ipynb
    3. 可以視情況自行調整個檔案中參數。
    4. 執行程式後會產生txt檔紀錄訓練過程的loss和accuracy，及建立一個資料夾保存各個epoch的權重，此外還會產生一個pth檔會保存validation loss最低的權重。
    5. Dan_Final_Weight.pth為AICUP競賽中正確率最高的權重。



2. Kyu
    1. 模型架構如下圖
    ![Kyu_Model](https://hackmd.io/_uploads/ByE1w6dBT.png)
    ![Kyu_input_block](https://hackmd.io/_uploads/B1egw6dHp.png)
    ![Kyu_basic_block](https://hackmd.io/_uploads/B15gD6dSa.png)
    ![Kyu_SE Block](https://hackmd.io/_uploads/Bkx-Pp_ra.png)
    2. 執行順序： Kyu_Adam.ipynb->Kyu_SGD.ipynb
    3. 可以視情況自行調整個檔案中參數。
    4. 執行程式後會產生txt檔紀錄訓練過程的loss和accuracy，及建立一個資料夾保存各個epoch的權重，此外還會產生一個pth檔會保存validation loss最低的權重。
    5. Kyu_Final_Weight.pth為AICUP競賽中正確率最高的權重。
    
3. 輸出upload.csv
    1.打開Make_Upload.ipynb
    2.如果有自己訓練的weight可以修改一開始的kyu_weight_path及dan_weight_path
    3.如果有修改model需要去下面Kyu Model或是Dan Model部分修改成自己的model
