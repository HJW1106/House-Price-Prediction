# 永豐AI GO競賽-攻房戰
最終排名：87/972

相關比賽資訊如下

[比賽心得](https://medium.com/@p112098/11f638e6c4bf)

[競賽官網](https://tbrain.trendmicro.com.tw/Competitions/Details/30)
# 簡介

## 競賽目的
如何透過影響房價高低的關鍵因素，包括坪數大小、屋齡屋況、地段環境及居住條件等，找出房屋的真正價值，是本次技術主題競賽的活動目標。
## 除官方提供資料及外，可使用所有可取得知開放資源，額外資料集使用如下

a. 房屋仲介營業登記地：[商工行政資料開放平臺](https://data.gcis.nat.gov.tw/main/index)

b. 科學園區位置：[政府資料開放平臺](https://data.gov.tw/)

c. 百貨公司位置：[商工行政資料開放平臺](https://data.gcis.nat.gov.tw/main/index)

# 資料前處理

## 基礎處理

### 排除outlier

### 處理缺失值

### 使用onehotencoder類別型資料

## 進階處理

### 關鍵資料處理
影響房價最重要之關鍵因素為其本身及鄰避設施所在位置，因此使用與鄰避設施之最短距離及鄰避設施密集度概念作為主要處理資料方法。

### 判斷相同標的
因資料橫跨兩個年度，資料集內同標的物件可能會因屋齡不同產生兩筆不同資料，為了不受到同一標的因不同狀況買賣產生價差過大的情況，將變數"鄉鎮市區"、"路名"、"總樓層數"、"建物型態"、"主要用途"相同之資料視為同一標的並使用平均房價作為其模型訓練之房價。

# 模型 - XGBoost
本競賽資料筆數不多且只有單一變數輸出，使用深度學習方法並不一定能達到更好的效果，可能有Overfitting狀況出現，XGBoost為Kaggle機器學習競賽中獲獎作品最常出現的模型算法，結合常見於機器學習方法中Boosting及Bagging，且其提供"fine tuning"功能，節省更多調參時間更有效率。

# Note
final code in directory `SINOPAC_HousePrice_XGB-finalcode.ipynb` 
