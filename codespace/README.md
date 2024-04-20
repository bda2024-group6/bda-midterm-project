## 程式實作說明

### 資料標記

### 資料前處理

- 使用中研院 CKIP Tagger 進行斷詞、詞性標註，保留文章中的普通名詞、動詞與形容詞
- 建立 1-gram 至 3-gram 的 tf-idf 矩陣，並且使用 chi-square 分數選取前 n 名的特徵
  - n = 50, 100, 200, 300, 400, 500, 600, 700

### 模型訓練

- 使用 Naive Bayes, SVM, Random Forest, XGBoost 與上述三者的 stacked model
- 先用 GridSearchCV 對訓練資料尋找最佳的模型超參數，並進行 5-fold cross validation
- 對不同的天數、特徵數、模型進行準確度比較

### 移動回測

