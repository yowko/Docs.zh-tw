---
title: 準備資料以建置模型
description: 了解如何在 ML.NET 中使用轉換來操縱及準備資料，以進行額外的處理或模型建置。
author: luisquintanilla
ms.author: luquinta
ms.date: 06/25/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4b7d5a09044e49f1b57b8276b893e0fc962a3be2
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397711"
---
# <a name="prepare-data-for-building-a-model"></a>準備資料以建置模型

了解如何使用 ML.NET 準備資料，以進行額外的處理或建置模型。

資料通常都是未經處理且疏鬆的。 此外，ML.NET 機器學習服務演算法預期輸入或特徵為單一的數字向量。 因此，資料準備的其中一個目標就是將資料轉換成 ML.NET 演算法所預期格式。 

## <a name="filter-data"></a>篩選資料

有時候，並非資料集中的所有資料都與分析有關。 其中一個移除無關資料的方法便是篩選。 [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) 包含一組篩選作業，可接受一個包含所有資料的 [`IDataView`](xref:Microsoft.ML.IDataView)，並傳回僅包含相關資料的 [IDataView](xref:Microsoft.ML.IDataView)。 請務必注意，因為篩選作業並非和 [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog) 中項目相似的 [`IEstimator`](xref:Microsoft.ML.IEstimator%601) 或 [`ITransformer`](xref:Microsoft.ML.ITransformer)，它們無法作為 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 或 [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) 資料準備管線的一部分包含在其中。 

使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

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

若要根據資料行的值篩選資料，請使用 [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) 方法。

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

以上範例會擷取資料集中價格介於 200000 及 1000000 之間的資料列。 套用此篩選的結果只會傳回資料中最後兩個資料列，並排除第一個資料列，因為其價格為 100000，而非介於指定的範圍。

## <a name="replace-missing-values"></a>取代遺漏值

遺漏值在資料集中經常出現。 其中一種處理遺漏值的方式是若資料中存在任何或其他有意義值 (例如平均數)，則將它們取代成指定類型的預設值。 

使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

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

請注意我們清單中的最後一個項目針對 `Price` 具有遺漏值。 若要取代 `Price` 資料行中的遺漏值，請使用 [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) 方法來填入該遺漏值。

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) 只能針對數字資料運作。

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET 支援各種[取代模式](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)。 以上範例使用 `Mean` 取代模式，這種模式會使用資料行的平均值填入遺漏值。 取代之結果會將 200,000 填入我們資料中最後一個項目的 `Price` 屬性，因為它是 100,000 和 300,000 的平均。 

## <a name="use-normalizers"></a>使用正規器

[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) (正規化) 是一種資料處理技術，用來標準化規格不相同的特徵，協助演算法更快收斂。 例如，年齡值的範圍和收入值的範圍差異便非常大，因為年齡的範圍通常介於 0 到 100，收入的範圍則涵蓋零到數千不等。 請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及正規化轉換的描述。 

### <a name="min-max-normalization"></a>最小-最大正規化

使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

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

正規化可以套用至具有單一數值和向量的資料行。 搭配 [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) 方法使用最小值和最大值正規化將 `Price` 資料行中的資料正規化。

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

原始的價格值 `[200000,100000]` 會使用 `MinMax` 正規化公式轉換成 `[ 1, 0.5 ]`，該公式的輸出值範圍介於 0 到 1。

### <a name="binning"></a>資料收納

[Binning](https://en.wikipedia.org/wiki/Data_binning) (資料收納) 會將連續值轉換成輸入的離散表示。 例如，假設您的其中一個特徵為年齡。 資料收納會建立該值的範圍，而非使用實際的年齡值。 其中一個收納可能是 0 到 18，另一收納則可能是 19 到 35 等。 

使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

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

使用 [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) 方法將資料正規化成收納。 `maximumBinCount` 參數可讓您指定分類資料所需要的收納數。 在此範例中，資料會放入兩個收納。  

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

非數字類別資料需要轉換成數字，才能用來建置機器學習模型。 

使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

```csharp
CarData[] cars = new CarData[] 
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

類別 `VehicleType` 屬性可使用 [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) 方法轉換成數字。 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

產生的轉換會將 `VehicleType` 文字值轉換成數字。 `VehicleType` 資料行中的項目會在套用轉換時成為下列項目： 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>使用文字資料

文字資料需要轉換成數字，才能用來建置機器學習模型。 請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及文字轉換的描述。

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

將文字轉換成數字向量表示的最少步驟是使用 [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) 方法。 透過使用 [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) 轉換，會將一系列的轉換套用到輸入文字資料行，產生表示 lp-normalized 文字及字元 ngrams 的數字向量。 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

產生的轉換會將 `Description` 資料行中文字值轉換成數字向量，且看起來會和以下輸出相似：

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

將複雜的文字處理步驟合併成一個 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)，移除干擾並可能可以視需要降低所需要的處理資源數。

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` 包含 [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) 方法所執行作業的子集。 更複雜管線之優點是對套用到資料的轉換進行控制和其可見度。 

使用第一個項目作為範例，下列是由 `textEstimator` 所定義轉換步驟產生結果的詳細描述：

**原始文字：This is a good product**

|資料轉換 | 說明 | 結果
|--|--|--|
|1.NormalizeText | 根據預設，將所有字母轉換成小寫 | this is a good product
|2.TokenizeWords | 將字串分割成個別的字組 | ["this","is","a","good","product"]
|3.RemoveDefaultStopWords | 移除停用字詞，例如 *is* 和 *a*。 | ["good","product"]
|4.MapValueToKey | 根據輸入資料，將值對應到索引鍵 (類別) |  [1,2]
|5.ProduceNGrams | 將文字轉換成連續字組的序列 | [1,1,1,0,0]
|6.NormalizeLpNorm | 使用輸入的 lp-norm 縮放輸入 | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
