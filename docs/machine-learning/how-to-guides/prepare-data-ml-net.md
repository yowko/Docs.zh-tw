---
title: 準備資料以建置模型
description: 了解如何在 ML.NET 中使用轉換來操縱及準備資料，以進行額外的處理或模型建置。
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452983"
---
# <a name="prepare-data-for-building-a-model"></a>準備資料以建置模型

了解如何使用 ML.NET 準備資料，以進行額外的處理或建置模型。

資料通常都是未經處理且疏鬆的。 ML.NET機器學習演算法期望輸入或要素位於單個數值向量中。 同樣，必須對要預測（標籤）的值進行編碼，尤其是在分類資料時。 因此，資料準備的其中一個目標就是將資料轉換成 ML.NET 演算法所預期格式。

## <a name="filter-data"></a>篩選資料

有時候，並非資料集中的所有資料都與分析有關。 其中一個移除無關資料的方法便是篩選。 [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog)包含一組篩選器操作，這些操作在 包含所有資料[`IDataView`](xref:Microsoft.ML.IDataView)的 中獲取，並返回僅包含感興趣的資料點的[IDataView。](xref:Microsoft.ML.IDataView) 請務必[`IEstimator`](xref:Microsoft.ML.IEstimator%601)注意，由於篩選器操作不是 或[`ITransformer`](xref:Microsoft.ML.ITransformer)與 中的操作類似[`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)，因此不能將其包含在[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)或[`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601)資料準備管道中。

獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

要根據列的值篩選資料，請使用 方法[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A)。

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

以上範例會擷取資料集中價格介於 200000 及 1000000 之間的資料列。 套用此篩選的結果只會傳回資料中最後兩個資料列，並排除第一個資料列，因為其價格為 100000，而非介於指定的範圍。

## <a name="replace-missing-values"></a>取代遺漏值

遺漏值在資料集中經常出現。 其中一種處理遺漏值的方式是若資料中存在任何或其他有意義值 (例如平均數)，則將它們取代成指定類型的預設值。

獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

請注意我們清單中的最後一個項目針對 `Price` 具有遺漏值。 要替換列中的`Price`缺失值，[`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)請使用 方法填充該缺失值。

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)僅適用于數值資料。

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET 支援各種[取代模式](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)。 上面的示例使用`Mean`替換模式，該模式使用該列的平均值填充缺失值。 取代之結果會將 200,000 填入我們資料中最後一個項目的 `Price` 屬性，因為它是 100,000 和 300,000 的平均。

## <a name="use-normalizers"></a>使用正規器

[正常化](https://en.wikipedia.org/wiki/Feature_scaling)是一種資料預處理技術，用於將要素縮放到相同的範圍內，通常在 0 和 1 之間，以便機器學習演算法可以更準確地處理它們。 例如，年齡和收入的範圍差別很大，年齡一般在0-100之間，收入一般在零到千之間。 請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及正規化轉換的描述。

### <a name="min-max-normalization"></a>最小-最大正規化

獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

正規化可以套用至具有單一數值和向量的資料行。 使用最小最大值與`Price`[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A)方法正常化列中的資料。

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

原始價格值`[200000,100000]`轉換為`[ 1, 0.5 ]`使用`MinMax`在 0-1 範圍內生成輸出值的正常化公式。

### <a name="binning"></a>量化

[Binning](https://en.wikipedia.org/wiki/Data_binning) (資料收納) 會將連續值轉換成輸入的離散表示。 例如，假設您的其中一個特徵為年齡。 資料收納會建立該值的範圍，而非使用實際的年齡值。 其中一個收納可能是 0 到 18，另一收納則可能是 19 到 35 等。

獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

使用[`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A)方法將資料正常化為 bin。 `maximumBinCount` 參數可讓您指定分類資料所需要的收納數。 在此範例中，資料會放入兩個收納。

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

資料收納的結果會建立 `[0,200000,Infinity]` 的收納界限。 因此，結果產生的收納將會是 `[0,1,1]`，因為第一個觀察到的結果介於 0 到 200000，其他的則大於 200000，但小於無限大。

## <a name="work-with-categorical-data"></a>使用類別資料

最常見的資料類型之一是分類資料。 分類資料具有有限的類別數。 例如，美國各州，或一組圖片中找到的動物類型清單。 無論分類資料是特徵還是標籤，都必須映射到數值，以便它們可用於生成機器學習模型。 ML.NET 中處理分類資料的方法有很多種，具體取決於要解決的問題。

### <a name="key-value-mapping"></a>鍵值對應

在ML.NET中，鍵是表示類別的整數值。 鍵值對應最常用於將字串標籤映射到用於訓練的唯一整數值，然後在模型用於預測時將其映射回其字串值。

用於執行鍵值對應的轉換是[MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A)和[MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A)。

`MapValueToKey`在模型中添加映射字典，以便在`MapKeyToValue`進行預測時執行反向轉換。

### <a name="one-hot-encoding"></a>一個熱編碼

一個熱編碼採用一組有限的值，並將其映射到二進位表示在字串中唯一位置具有單個`1`值的整數。 如果沒有分類資料的隱式排序，則熱編碼可能是最佳選擇。 下表顯示了一個將郵遞區號作為原始值的示例。

|原始值|一個熱編碼值|
|---------|---------------------|
|98052|00...01|
|98100|00...10|
|...|...|
|98109|10...00|

將分類資料轉換為一熱編碼數位的轉換為[`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)。

### <a name="hashing"></a>雜湊

雜湊是將分類資料轉換為數字的另一種方法。 雜湊函數將任意大小（例如文本字串）的資料對應到具有固定範圍的數位上。 散列是一種快速且節省空間的要素向量化方法。 機器學習中雜湊的一個顯著示例是電子郵件垃圾郵件篩選，其中不是維護已知單詞的字典，而是對電子郵件中的每個單詞進行雜湊並添加到大型要素向量中。 以這種方式使用雜湊可以避免使用字典中的單詞來規避惡意垃圾郵件篩選的問題。

ML.NET提供[雜湊](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A)轉換，用於對文本、日期和數位資料執行雜湊。 與值鍵映射一樣，雜湊轉換的輸出也是關鍵類型。

## <a name="work-with-text-data"></a>使用文字資料

與分類資料一樣，在使用文本資料構建機器學習模型之前，需要將文本資料轉換為數值要素。 請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及文字轉換的描述。

使用以下資料等已載入到 中的[`IDataView`](xref:Microsoft.ML.IDataView)資料：

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

ML.NET提供採用[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A)文本字串值的轉換，並通過應用一系列單獨的轉換從文本中創建一組要素。

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

生成的變換將列中`Description`的文本值轉換為類似于以下輸出的數位向量：

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

構成的變換`FeaturizeText`也可以單獨應用，以便對要素生成進行更精細的細微性控制。

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`包含[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A)方法執行的操作的子集。 更複雜管線之優點是對套用到資料的轉換進行控制和其可見度。

使用第一個項目作為範例，下列是由 `textEstimator` 所定義轉換步驟產生結果的詳細描述：

**原文：這是一個很好的產品**

|轉換 | 描述 | 結果
|--|--|--|
|1. 正常化文本 | 根據預設，將所有字母轉換成小寫 | this is a good product
|2. 標記詞 | 將字串分割成個別的字組 | ["this","is","a","good","product"]
|3. 刪除預設停止詞 | 移除停用字詞，例如 *is* 和 *a*。 | ["good","product"]
|4. 映射價值圖鍵 | 根據輸入資料，將值對應到索引鍵 (類別) |  [1,2]
|5. 生產NGrams | 將文字轉換成連續字組的序列 | [1,1,1,0,0]
|6. 正常化LpNorm | 使用輸入的 lp-norm 縮放輸入 | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
