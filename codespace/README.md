## 函數實作說明

### `def label(df_article, df_stock, n, sigma):`

#### Description

對傳入的資料用自編碼的方式進行標記，並回傳標記後的 dataframe。

#### Input

- `df_article`：將要被標記的文章資料集
- `df_stock`：標記文章所依據的股市資料
- `n`：天數的門檻值
- `sigma`：漲跌幅的門檻值

#### Output

回傳一個 numpy array `Y`，內容是 `df_article` 每一列所對應到的標記內容。

### `def preprocess(df_article, features, n):`

#### Description

對傳入的資料進行前處理與特徵提取。

#### Input

- `df_article`：將要被前處理的文章資料集。

- `features`：一個 dictionary，註明了在特徵組合中所要使用的特徵類別。

  ```py
  # Example
  features = {'ngram': True...}
  ```

- `n`：若我們要使用 n-gram feature 的話，使用 chi-square 選取最重要的 `n` 個詞。

#### Output

回傳一個 **dictionary**，該 **dictionary** 的 key 為特徵組合的文字敘述，value 為其所對應的矩陣 `X`。

### `def train(X_dict, Y):`

#### Description

針對給定在不同特徵組合之下的輸入矩陣與標籤，訓練各種分類模型，並且回傳訓練結果（confusion matrix），並儲存最佳的數個模型在本機上。

#### Input

- `X_dict` 為**前處理後** (`preprocess()`) 所得到的字典，裡面含有不同特徵組合所構成的矩陣。
- `Y`為**標記後** (`label()`) 所得到的輸出矩陣。

#### Output

### `def backtest(df_article):`

#### Input 

#### Output



