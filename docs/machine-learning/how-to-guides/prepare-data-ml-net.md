---
title: 準備資料以建置模型
description: 了解如何在 ML.NET 中使用轉換來操縱及準備資料，以進行額外的處理或模型建置。
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452983"
---
# <a name="prepare-data-for-building-a-model"></a>準備資料以建置模型

了解如何使用 ML.NET 準備資料，以進行額外的處理或建置模型。

資料通常都是未經處理且疏鬆的。 ML.NET 機器學習演算法會預期輸入或特徵會在單一數值向量中。 同樣地，要預測的值（標籤）（特別是當它的類別資料）必須經過編碼。 因此，資料準備的其中一個目標就是將資料轉換成 ML.NET 演算法所預期格式。

## <a name="filter-data"></a>篩選資料

有時候，並非資料集中的所有資料都與分析有關。 其中一個移除無關資料的方法便是篩選。 [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) 包含一組篩選作業，可接受一個包含所有資料的 [`IDataView`](xref:Microsoft.ML.IDataView)，並傳回僅包含相關資料的 [IDataView](xref:Microsoft.ML.IDataView)。 請務必注意，因為篩選作業並非和 [`IEstimator`](xref:Microsoft.ML.IEstimator%601) 中項目相似的 [`ITransformer`](xref:Microsoft.ML.ITransformer) 或 [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)，它們無法作為 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 或 [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) 資料準備管線的一部分包含在其中。

請採用下列輸入資料，並將其載入至稱為 `data`的[`IDataView`](xref:Microsoft.ML.IDataView) ：

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

若要根據資料行的值篩選資料，請使用 [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) 方法。

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

以上範例會擷取資料集中價格介於 200000 及 1000000 之間的資料列。 套用此篩選的結果只會傳回資料中最後兩個資料列，並排除第一個資料列，因為其價格為 100000，而非介於指定的範圍。

## <a name="replace-missing-values"></a>取代遺漏值

遺漏值在資料集中經常出現。 其中一種處理遺漏值的方式是若資料中存在任何或其他有意義值 (例如平均數)，則將它們取代成指定類型的預設值。

請採用下列輸入資料，並將其載入至稱為 `data`的[`IDataView`](xref:Microsoft.ML.IDataView) ：

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

請注意我們清單中的最後一個項目針對 `Price` 具有遺漏值。 若要取代 `Price` 資料行中的遺漏值，請使用 [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) 方法來填入該遺漏值。

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) 只能針對數字資料運作。

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET 支援各種[取代模式](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)。 上述範例使用 `Mean` 取代模式，這會以該資料行的平均值填滿遺漏值。 取代之結果會將 200,000 填入我們資料中最後一個項目的 `Price` 屬性，因為它是 100,000 和 300,000 的平均。

## <a name="use-normalizers"></a>使用正規器

正規化[是一種資料](https://en.wikipedia.org/wiki/Feature_scaling)預先處理技術，用來將功能調整為相同的範圍（通常介於0和1之間），以便機器學習演算法更精確地處理。 例如，年齡和收入的範圍明顯不同，年齡通常在0-100 和收入範圍內，通常會在零到數千的範圍內。 請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及正規化轉換的描述。

### <a name="min-max-normalization"></a>最小-最大正規化

請採用下列輸入資料，並將其載入至稱為 `data`的[`IDataView`](xref:Microsoft.ML.IDataView) ：

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

正規化可以套用至具有單一數值和向量的資料行。 搭配 `Price`[`NormalizeMinMax` 方法使用最小值和最大值正規化將 ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) 資料行中的資料正規化。

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

原始的價格值 `[200000,100000]` 會使用 `MinMax` 正規化公式（會產生0-1 範圍內的輸出值），轉換成 `[ 1, 0.5 ]`。

### <a name="binning"></a>量化

[Binning](https://en.wikipedia.org/wiki/Data_binning) (資料收納) 會將連續值轉換成輸入的離散表示。 例如，假設您的其中一個特徵為年齡。 資料收納會建立該值的範圍，而非使用實際的年齡值。 其中一個收納可能是 0 到 18，另一收納則可能是 19 到 35 等。

請採用下列輸入資料，並將其載入至稱為 `data`的[`IDataView`](xref:Microsoft.ML.IDataView) ：

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

使用 [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) 方法將資料正規化成收納。 `maximumBinCount` 參數可讓您指定分類資料所需要的收納數。 在此範例中，資料會放入兩個收納。

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

其中一個最常見的資料類型是類別資料。 類別資料具有有限數目的分類。 例如，美國的州，或在一組圖片中找到的動物類型清單。 不論類別資料是特徵或標籤，它們都必須對應到數值，才能用來產生機器學習模型。 根據您要解決的問題，有幾種方式可以在 ML.NET 中使用類別資料。

### <a name="key-value-mapping"></a>金鑰值對應

在 ML.NET 中，索引鍵是代表類別目錄的整數值。 索引鍵值對應最常用來將字串標籤對應到唯一整數值進行定型，然後在模型用來進行預測時，再回到其字串值。

用來執行金鑰值對應的轉換是[MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A)和[MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A)。

`MapValueToKey` 會在模型中加入對應的字典，以便在進行預測時，`MapKeyToValue` 可以執行反向轉換。

### <a name="one-hot-encoding"></a>一個熱編碼

一個熱編碼會採用一組有限的值，並將它們對應到整數，其二進位表示在字串中的唯一位置具有單一 `1` 值。 如果沒有分類資料的隱含排序，則一個熱編碼可能是最佳選擇。 下表顯示 zip 代碼為原始值的範例。

|原始值|一個熱編碼值|
|---------|---------------------|
|98052|00 ... 01|
|98100|00 ... 10|
|...|...|
|98109|10 ... 00|

[`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)，將類別資料轉換成一個經常性編碼數位的轉換。

### <a name="hashing"></a>處理

雜湊是將類別資料轉換成數位的另一種方式。 雜湊函式會將任意大小的資料（例如文字字串）對應到具有固定範圍的數位。 雜湊可以是快速且具有空間效益的向量化功能方式。 機器學習中有一個值得注意的雜湊範例是以電子郵件傳送垃圾郵件，而不是維護已知單字的字典，電子郵件中的每個單字都會雜湊並新增至大型功能向量。 以這種方式使用雜湊可避免使用不在字典中的單字，欺詐惡意垃圾郵件篩選的問題。

ML.NET 提供[雜湊](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A)轉換來對文字、日期和數值資料執行雜湊。 就像值索引鍵對應一樣，雜湊轉換的輸出是索引鍵類型。

## <a name="work-with-text-data"></a>使用文字資料

就像類別資料，文字資料必須先轉換成數值特徵，才能使用它來建立機器學習模型。 請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及文字轉換的描述。

使用如下的資料，該資料已載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

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

ML.NET 提供的[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A)轉換會接受文字的字串值，並藉由套用一系列的個別轉換來建立文字的一組功能。

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

產生的轉換會將 `Description` 資料行中的文字值轉換成數值向量，看起來會類似以下的輸出：

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

組成 `FeaturizeText` 的轉換也可以個別套用，以更精確地控制功能產生。

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` 包含 [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) 方法所執行作業的子集。 更複雜管線之優點是對套用到資料的轉換進行控制和其可見度。

使用第一個項目作為範例，下列是由 `textEstimator` 所定義轉換步驟產生結果的詳細描述：

**原始文字：這是很好的產品**

|轉換 | 描述 | 結果
|--|--|--|
|1. NormalizeText | 根據預設，將所有字母轉換成小寫 | this is a good product
|2. TokenizeWords | 將字串分割成個別的字組 | ["this","is","a","good","product"]
|3. RemoveDefaultStopWords | 移除停用字詞，例如 *is* 和 *a*。 | ["good","product"]
|4. MapValueToKey | 根據輸入資料，將值對應到索引鍵 (類別) |  [1,2]
|5. ProduceNGrams | 將文字轉換成連續字組的序列 | [1,1,1,0,0]
|6. NormalizeLpNorm | 使用輸入的 lp-norm 縮放輸入 | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
