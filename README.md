# 用新聞與社群媒體數據預測航運股漲跌

### 資料概要

### 資料標記

### 資料前處理

- 使用中研院 [CKIP Tagger](https://github.com/ckiplab/ckiptagger) 進行斷詞、詞性標記，篩選出文章中的**普通名詞**、**動詞**與**形容詞**。
- 使用 `TfidfVectorizer` 建構詞彙的向量空間。
  - 考慮 1-gram 至 3-gram 的詞彙組合。
  - 篩選掉 document frequency 大於文件數 95% 與出現小於 2 次的詞彙。
- 對上述向量空間，我們使用 chi-square 選出前 k 名的最佳特徵作為模型的輸入。

### 模型訓練

#### 訓練方式

- 採用模型：Naive Bayes, SVM, Random Forest, XGBoost 與 stacking model
  - 將資料隨機切分成訓練資料集 (80%) 與測試資料集 (20%)，並對訓練資料集進行 5-fold cross validation
  - 用 Grid Search 找到 Naive Bayes, SVM, Random Forest, XGBoost 的最佳參數
  - 再分別執行最佳模型與四者的 stacking model，紀錄結果。

#### 不同內容種類間之比較

針對不同內容種類 (ptt, dcard, 新聞) 選取不同的 d (天數)和 k (特徵數) 進行模型訓練，並比較結果。ㄐㄧㄤ

#### 所有資料

把所有資料 (ptt, dcard, 新聞) 串接起來，選取 d = 3 和不同的 k (特徵數) 進行模型訓練，並比較結果。

### 移動回測

#### 回測方式

- 把所有資料 (ptt, dcard, 新聞) 串接起來，從 2022 年 3 月開始，用前 3 個月的數據訓練模型並預測第 4 個月的股市漲跌。
- 對每一組四個月的資料，我們將前三個月視為訓練資料集、第四個月視為測試資料集，選取 d = 3 和不同的 k (特徵數) 進行模型訓練，並選擇表現最佳的模型進行股票預測。

#### 回測結果



### 進階討論

#### 加入籌碼面數據

- 將三大法人的買/賣超經過標準化的值作為模型特徵
- 準確率變化：









