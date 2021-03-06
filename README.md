# 各版本的更動說明

**<font size=3 color='blue'>edition01 說明:<br></font>**
```
    (1)修改中文文字敘述，以及修正所有的indentation
    (2)調整姿勢分類計算方式: 將np.max那段從最小誤差的前30張改成最小誤差的前80%圖片
    (3)調整信心分數圖的折線圖顏色及大小
    (4)調整姿勢分類class: 增加一個計算距離特徵誤差的練習函數
        簡單說明: 先找出要判定的類別樣本(深蹲[蹲])作為正確姿勢，透過比較單張frame與所有樣本距離特徵的差距，
        找出誤差最小的三張圖來當基準，接著將三者距離都拿來計算誤差，最終再取平均，得到一組新的距離特徵誤差輸出。(M,3)
        未來應用: 透過這個距離特徵輸出，之後可以拿來計算我們想要求得的分數。
        
    
```
**<font size=3 color='blue'>edition02 說明:<br></font>**
```
    (1)[深蹲距離特徵調整]將人體姿勢特徵嵌入所選擇的距離特徵，做篩選以及添加新特徵，由於深蹲姿勢主要跟手
        的位置沒什麼關係，於是我們從原本23個距離特徵中砍掉12個與手相關的特徵，並且增添左右肩到膝的兩個向量，
        因此最終定案是13個距離特徵向量。 (2021/12/20)
        
[完成膝蓋平行評分]
    (2)[測試]膝蓋平行角度函數測試成功。(2021/12/21)
    (3)[測試]膝蓋平行角度分數平滑測試成功。(2021/12/21)
    (4)[實裝]膝蓋平行角度平滑分數已能在main code執行
    (5)[實裝]設立一個可以讀取計數器開關的函數，將門檻值進入到離開期間，score最低的數值取出作為最終的評分。
    (6)[實裝]將膝蓋平行角度評分作圖在output影片中
    

edition02-py [涵訓練版本]說明:<br>

    (1)將所有import module移動到最前面
    (2)刪除掉 [9.建立分類器] 中移除異常值的部分，並且將零散的code整合在一起，並將程式碼改成函數型式。
    (3)將[11.影片預測]的code包成函數
    (4)此版本還是會使用到[9.建立分類器]的函數來訓練圖片
    
    
    
edition02-py [上機版本]說明:<br>

    (1)為了減少jetson nano負擔，我們將函數9訓練完存成的csv檔案，當成附件一併傳給AIoT，這樣就不用傳給AIoT圖片檔，
        也不會讓它花費資源去跑函數9。
    (2)此版本只需要輸入函數11，給定欲分析影片位置路徑及影片輸出路徑，就能夠產生輸出圖片
    
    
```


**<font size=3 color='blue'>edition03 說明:<br></font>**
```
    (1)[完成新增膝蓋前傾評分] (2021/12/24)
    (2)[完成即時攝影動作辨識](2021/12/24)
        (即時圖片無法放入中文字幕，只能用英文來排版)



edition03-py [上機版本]說明:

    (1)增加攝像機實時辨識功能。
    (2)為了減少實時辨識對 jetson nano 的負擔，上機版拔掉了使用pillow套件的所有作圖，所以無法每張frame呈現動作
        分數的歷史折線圖表，也無法使用本地端中文字體。
    (3)為了克服無法嵌字，我們使用openCV一個對程式沒負擔的套件。(但這個套件提供字體有限，沒有中文)
    (4)該上機版本亦包含前面版本的功能: [1]訓練 [2]影片辨識 [3]攝像機實時辨識
    
```
**<font size=3 color='blue'>edition04 說明:<br></font>**
```
    (1)調整人體特徵權重 (將與肩膀有關的向量乘以1/5的權重)
    (2)[完成臀部下壓評分] (2021/12/28)
    (3)[完成背部挺直評分] (2021/12/28)
    


edition04-py [上機版本]說明:

    (1)將四項深蹲細節評分實裝，可以在AIoT (jetson nano) 正常運行。
    (2)為了後續雲端跟地端資料庫能保存數據，我們output的函數增加一個 return list的功能，將每次深蹲的次數及4項細節評分都能取得。
    (3)該上機版本亦包含前面版本的功能: [1]訓練 [2]影片辨識 [3]攝像機實時辨識
    
```
