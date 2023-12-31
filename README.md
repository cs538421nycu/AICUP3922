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
[下載Train Dataset](https://drive.google.com/drive/folders/1dl55gEXbeT2VDWOHFdwUshtqoHx9LQX3?usp=drive_link)\
[下載Dan最後權重](https://drive.google.com/file/d/1U38RxNY0KhakDvWE9OYGyzPNI4Ns1_ih/view?usp=sharing)\
[下載Kyu最後權重](https://drive.google.com/file/d/1Vf_ejOC-yB-Tk3N6RaH3qAmWwzYc8lUQ/view?usp=sharing)\
下載後放入棋力模仿資料夾即可\
[也可至此下載所有檔案](https://drive.google.com/drive/folders/1YG9770fNYPKr6OruFTDA9nNHEb4mbSkC?usp=drive_link)\
[備用檔案連結](https://drive.google.com/drive/folders/1u62bujVYEopXl4cJm1csixmR6anGKl1N?usp=sharing)
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
    1. 打開Make_Upload.ipynb
    2. 如果有自己訓練的weight可以修改一開始的kyu_weight_path及dan_weight_path
    3. 如果有修改model需要去下面Kyu Model或是Dan Model部分修改成自己的model

# 棋風辨識
### 執行順序
1. 訓練完五個檔案，會自動存取validation loss最低的權重。
2. 將該權重load進model，進行測試，輸出預測結果。
3. 將模型三的三種不同結果進行投票，輸出結果再和模型一、模型二投票，獲得最終結果。

### 投票方法
1. 開啟vote.ipynb
2. 在三個file中輸入要投票的檔案名稱（含副檔名.csv）
3. 輸入output file名稱（結果將寫入此名的檔案）
4. 執行檔案
