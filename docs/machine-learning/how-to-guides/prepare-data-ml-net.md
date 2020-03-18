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
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="455b7-103">準備資料以建置模型</span><span class="sxs-lookup"><span data-stu-id="455b7-103">Prepare data for building a model</span></span>

<span data-ttu-id="455b7-104">了解如何使用 ML.NET 準備資料，以進行額外的處理或建置模型。</span><span class="sxs-lookup"><span data-stu-id="455b7-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="455b7-105">資料通常都是未經處理且疏鬆的。</span><span class="sxs-lookup"><span data-stu-id="455b7-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="455b7-106">ML.NET機器學習演算法期望輸入或要素位於單個數值向量中。</span><span class="sxs-lookup"><span data-stu-id="455b7-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="455b7-107">同樣，必須對要預測（標籤）的值進行編碼，尤其是在分類資料時。</span><span class="sxs-lookup"><span data-stu-id="455b7-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="455b7-108">因此，資料準備的其中一個目標就是將資料轉換成 ML.NET 演算法所預期格式。</span><span class="sxs-lookup"><span data-stu-id="455b7-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="455b7-109">篩選資料</span><span class="sxs-lookup"><span data-stu-id="455b7-109">Filter data</span></span>

<span data-ttu-id="455b7-110">有時候，並非資料集中的所有資料都與分析有關。</span><span class="sxs-lookup"><span data-stu-id="455b7-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="455b7-111">其中一個移除無關資料的方法便是篩選。</span><span class="sxs-lookup"><span data-stu-id="455b7-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="455b7-112">[`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog)包含一組篩選器操作，這些操作在 包含所有資料[`IDataView`](xref:Microsoft.ML.IDataView)的 中獲取，並返回僅包含感興趣的資料點的[IDataView。](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="455b7-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="455b7-113">請務必[`IEstimator`](xref:Microsoft.ML.IEstimator%601)注意，由於篩選器操作不是 或[`ITransformer`](xref:Microsoft.ML.ITransformer)與 中的操作類似[`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)，因此不能將其包含在[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)或[`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601)資料準備管道中。</span><span class="sxs-lookup"><span data-stu-id="455b7-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="455b7-114">獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：</span><span class="sxs-lookup"><span data-stu-id="455b7-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="455b7-115">要根據列的值篩選資料，請使用 方法[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A)。</span><span class="sxs-lookup"><span data-stu-id="455b7-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="455b7-116">以上範例會擷取資料集中價格介於 200000 及 1000000 之間的資料列。</span><span class="sxs-lookup"><span data-stu-id="455b7-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="455b7-117">套用此篩選的結果只會傳回資料中最後兩個資料列，並排除第一個資料列，因為其價格為 100000，而非介於指定的範圍。</span><span class="sxs-lookup"><span data-stu-id="455b7-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="455b7-118">取代遺漏值</span><span class="sxs-lookup"><span data-stu-id="455b7-118">Replace missing values</span></span>

<span data-ttu-id="455b7-119">遺漏值在資料集中經常出現。</span><span class="sxs-lookup"><span data-stu-id="455b7-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="455b7-120">其中一種處理遺漏值的方式是若資料中存在任何或其他有意義值 (例如平均數)，則將它們取代成指定類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="455b7-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="455b7-121">獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：</span><span class="sxs-lookup"><span data-stu-id="455b7-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="455b7-122">請注意我們清單中的最後一個項目針對 `Price` 具有遺漏值。</span><span class="sxs-lookup"><span data-stu-id="455b7-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="455b7-123">要替換列中的`Price`缺失值，[`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)請使用 方法填充該缺失值。</span><span class="sxs-lookup"><span data-stu-id="455b7-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="455b7-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)僅適用于數值資料。</span><span class="sxs-lookup"><span data-stu-id="455b7-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="455b7-125">ML.NET 支援各種[取代模式](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)。</span><span class="sxs-lookup"><span data-stu-id="455b7-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="455b7-126">上面的示例使用`Mean`替換模式，該模式使用該列的平均值填充缺失值。</span><span class="sxs-lookup"><span data-stu-id="455b7-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="455b7-127">取代之結果會將 200,000 填入我們資料中最後一個項目的 `Price` 屬性，因為它是 100,000 和 300,000 的平均。</span><span class="sxs-lookup"><span data-stu-id="455b7-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="455b7-128">使用正規器</span><span class="sxs-lookup"><span data-stu-id="455b7-128">Use normalizers</span></span>

<span data-ttu-id="455b7-129">[正常化](https://en.wikipedia.org/wiki/Feature_scaling)是一種資料預處理技術，用於將要素縮放到相同的範圍內，通常在 0 和 1 之間，以便機器學習演算法可以更準確地處理它們。</span><span class="sxs-lookup"><span data-stu-id="455b7-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="455b7-130">例如，年齡和收入的範圍差別很大，年齡一般在0-100之間，收入一般在零到千之間。</span><span class="sxs-lookup"><span data-stu-id="455b7-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="455b7-131">請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及正規化轉換的描述。</span><span class="sxs-lookup"><span data-stu-id="455b7-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="455b7-132">最小-最大正規化</span><span class="sxs-lookup"><span data-stu-id="455b7-132">Min-Max normalization</span></span>

<span data-ttu-id="455b7-133">獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：</span><span class="sxs-lookup"><span data-stu-id="455b7-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="455b7-134">正規化可以套用至具有單一數值和向量的資料行。</span><span class="sxs-lookup"><span data-stu-id="455b7-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="455b7-135">使用最小最大值與`Price`[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A)方法正常化列中的資料。</span><span class="sxs-lookup"><span data-stu-id="455b7-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="455b7-136">原始價格值`[200000,100000]`轉換為`[ 1, 0.5 ]`使用`MinMax`在 0-1 範圍內生成輸出值的正常化公式。</span><span class="sxs-lookup"><span data-stu-id="455b7-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="455b7-137">量化</span><span class="sxs-lookup"><span data-stu-id="455b7-137">Binning</span></span>

<span data-ttu-id="455b7-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) (資料收納) 會將連續值轉換成輸入的離散表示。</span><span class="sxs-lookup"><span data-stu-id="455b7-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="455b7-139">例如，假設您的其中一個特徵為年齡。</span><span class="sxs-lookup"><span data-stu-id="455b7-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="455b7-140">資料收納會建立該值的範圍，而非使用實際的年齡值。</span><span class="sxs-lookup"><span data-stu-id="455b7-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="455b7-141">其中一個收納可能是 0 到 18，另一收納則可能是 19 到 35 等。</span><span class="sxs-lookup"><span data-stu-id="455b7-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="455b7-142">獲取以下輸入資料並將其載入到調用[`IDataView`](xref:Microsoft.ML.IDataView)`data`：</span><span class="sxs-lookup"><span data-stu-id="455b7-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="455b7-143">使用[`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A)方法將資料正常化為 bin。</span><span class="sxs-lookup"><span data-stu-id="455b7-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="455b7-144">`maximumBinCount` 參數可讓您指定分類資料所需要的收納數。</span><span class="sxs-lookup"><span data-stu-id="455b7-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="455b7-145">在此範例中，資料會放入兩個收納。</span><span class="sxs-lookup"><span data-stu-id="455b7-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="455b7-146">資料收納的結果會建立 `[0,200000,Infinity]` 的收納界限。</span><span class="sxs-lookup"><span data-stu-id="455b7-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="455b7-147">因此，結果產生的收納將會是 `[0,1,1]`，因為第一個觀察到的結果介於 0 到 200000，其他的則大於 200000，但小於無限大。</span><span class="sxs-lookup"><span data-stu-id="455b7-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="455b7-148">使用類別資料</span><span class="sxs-lookup"><span data-stu-id="455b7-148">Work with categorical data</span></span>

<span data-ttu-id="455b7-149">最常見的資料類型之一是分類資料。</span><span class="sxs-lookup"><span data-stu-id="455b7-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="455b7-150">分類資料具有有限的類別數。</span><span class="sxs-lookup"><span data-stu-id="455b7-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="455b7-151">例如，美國各州，或一組圖片中找到的動物類型清單。</span><span class="sxs-lookup"><span data-stu-id="455b7-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="455b7-152">無論分類資料是特徵還是標籤，都必須映射到數值，以便它們可用於生成機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="455b7-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="455b7-153">ML.NET 中處理分類資料的方法有很多種，具體取決於要解決的問題。</span><span class="sxs-lookup"><span data-stu-id="455b7-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="455b7-154">鍵值對應</span><span class="sxs-lookup"><span data-stu-id="455b7-154">Key value mapping</span></span>

<span data-ttu-id="455b7-155">在ML.NET中，鍵是表示類別的整數值。</span><span class="sxs-lookup"><span data-stu-id="455b7-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="455b7-156">鍵值對應最常用於將字串標籤映射到用於訓練的唯一整數值，然後在模型用於預測時將其映射回其字串值。</span><span class="sxs-lookup"><span data-stu-id="455b7-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="455b7-157">用於執行鍵值對應的轉換是[MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A)和[MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A)。</span><span class="sxs-lookup"><span data-stu-id="455b7-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="455b7-158">`MapValueToKey`在模型中添加映射字典，以便在`MapKeyToValue`進行預測時執行反向轉換。</span><span class="sxs-lookup"><span data-stu-id="455b7-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="455b7-159">一個熱編碼</span><span class="sxs-lookup"><span data-stu-id="455b7-159">One hot encoding</span></span>

<span data-ttu-id="455b7-160">一個熱編碼採用一組有限的值，並將其映射到二進位表示在字串中唯一位置具有單個`1`值的整數。</span><span class="sxs-lookup"><span data-stu-id="455b7-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="455b7-161">如果沒有分類資料的隱式排序，則熱編碼可能是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="455b7-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="455b7-162">下表顯示了一個將郵遞區號作為原始值的示例。</span><span class="sxs-lookup"><span data-stu-id="455b7-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="455b7-163">原始值</span><span class="sxs-lookup"><span data-stu-id="455b7-163">Raw value</span></span>|<span data-ttu-id="455b7-164">一個熱編碼值</span><span class="sxs-lookup"><span data-stu-id="455b7-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="455b7-165">98052</span><span class="sxs-lookup"><span data-stu-id="455b7-165">98052</span></span>|<span data-ttu-id="455b7-166">00...01</span><span class="sxs-lookup"><span data-stu-id="455b7-166">00...01</span></span>|
|<span data-ttu-id="455b7-167">98100</span><span class="sxs-lookup"><span data-stu-id="455b7-167">98100</span></span>|<span data-ttu-id="455b7-168">00...10</span><span class="sxs-lookup"><span data-stu-id="455b7-168">00...10</span></span>|
|<span data-ttu-id="455b7-169">...</span><span class="sxs-lookup"><span data-stu-id="455b7-169">...</span></span>|<span data-ttu-id="455b7-170">...</span><span class="sxs-lookup"><span data-stu-id="455b7-170">...</span></span>|
|<span data-ttu-id="455b7-171">98109</span><span class="sxs-lookup"><span data-stu-id="455b7-171">98109</span></span>|<span data-ttu-id="455b7-172">10...00</span><span class="sxs-lookup"><span data-stu-id="455b7-172">10...00</span></span>|

<span data-ttu-id="455b7-173">將分類資料轉換為一熱編碼數位的轉換為[`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)。</span><span class="sxs-lookup"><span data-stu-id="455b7-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="455b7-174">雜湊</span><span class="sxs-lookup"><span data-stu-id="455b7-174">Hashing</span></span>

<span data-ttu-id="455b7-175">雜湊是將分類資料轉換為數字的另一種方法。</span><span class="sxs-lookup"><span data-stu-id="455b7-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="455b7-176">雜湊函數將任意大小（例如文本字串）的資料對應到具有固定範圍的數位上。</span><span class="sxs-lookup"><span data-stu-id="455b7-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="455b7-177">散列是一種快速且節省空間的要素向量化方法。</span><span class="sxs-lookup"><span data-stu-id="455b7-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="455b7-178">機器學習中雜湊的一個顯著示例是電子郵件垃圾郵件篩選，其中不是維護已知單詞的字典，而是對電子郵件中的每個單詞進行雜湊並添加到大型要素向量中。</span><span class="sxs-lookup"><span data-stu-id="455b7-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="455b7-179">以這種方式使用雜湊可以避免使用字典中的單詞來規避惡意垃圾郵件篩選的問題。</span><span class="sxs-lookup"><span data-stu-id="455b7-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="455b7-180">ML.NET提供[雜湊](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A)轉換，用於對文本、日期和數位資料執行雜湊。</span><span class="sxs-lookup"><span data-stu-id="455b7-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="455b7-181">與值鍵映射一樣，雜湊轉換的輸出也是關鍵類型。</span><span class="sxs-lookup"><span data-stu-id="455b7-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="455b7-182">使用文字資料</span><span class="sxs-lookup"><span data-stu-id="455b7-182">Work with text data</span></span>

<span data-ttu-id="455b7-183">與分類資料一樣，在使用文本資料構建機器學習模型之前，需要將文本資料轉換為數值要素。</span><span class="sxs-lookup"><span data-stu-id="455b7-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="455b7-184">請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及文字轉換的描述。</span><span class="sxs-lookup"><span data-stu-id="455b7-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="455b7-185">使用以下資料等已載入到 中的[`IDataView`](xref:Microsoft.ML.IDataView)資料：</span><span class="sxs-lookup"><span data-stu-id="455b7-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="455b7-186">ML.NET提供採用[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A)文本字串值的轉換，並通過應用一系列單獨的轉換從文本中創建一組要素。</span><span class="sxs-lookup"><span data-stu-id="455b7-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="455b7-187">生成的變換將列中`Description`的文本值轉換為類似于以下輸出的數位向量：</span><span class="sxs-lookup"><span data-stu-id="455b7-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="455b7-188">構成的變換`FeaturizeText`也可以單獨應用，以便對要素生成進行更精細的細微性控制。</span><span class="sxs-lookup"><span data-stu-id="455b7-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="455b7-189">`textEstimator`包含[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A)方法執行的操作的子集。</span><span class="sxs-lookup"><span data-stu-id="455b7-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="455b7-190">更複雜管線之優點是對套用到資料的轉換進行控制和其可見度。</span><span class="sxs-lookup"><span data-stu-id="455b7-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="455b7-191">使用第一個項目作為範例，下列是由 `textEstimator` 所定義轉換步驟產生結果的詳細描述：</span><span class="sxs-lookup"><span data-stu-id="455b7-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="455b7-192">**原文：這是一個很好的產品**</span><span class="sxs-lookup"><span data-stu-id="455b7-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="455b7-193">轉換</span><span class="sxs-lookup"><span data-stu-id="455b7-193">Transform</span></span> | <span data-ttu-id="455b7-194">描述</span><span class="sxs-lookup"><span data-stu-id="455b7-194">Description</span></span> | <span data-ttu-id="455b7-195">結果</span><span class="sxs-lookup"><span data-stu-id="455b7-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="455b7-196">1. 正常化文本</span><span class="sxs-lookup"><span data-stu-id="455b7-196">1. NormalizeText</span></span> | <span data-ttu-id="455b7-197">根據預設，將所有字母轉換成小寫</span><span class="sxs-lookup"><span data-stu-id="455b7-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="455b7-198">this is a good product</span><span class="sxs-lookup"><span data-stu-id="455b7-198">this is a good product</span></span>
|<span data-ttu-id="455b7-199">2. 標記詞</span><span class="sxs-lookup"><span data-stu-id="455b7-199">2. TokenizeWords</span></span> | <span data-ttu-id="455b7-200">將字串分割成個別的字組</span><span class="sxs-lookup"><span data-stu-id="455b7-200">Splits string into individual words</span></span> | <span data-ttu-id="455b7-201">["this","is","a","good","product"]</span><span class="sxs-lookup"><span data-stu-id="455b7-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="455b7-202">3. 刪除預設停止詞</span><span class="sxs-lookup"><span data-stu-id="455b7-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="455b7-203">移除停用字詞，例如 *is* 和 *a*。</span><span class="sxs-lookup"><span data-stu-id="455b7-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="455b7-204">["good","product"]</span><span class="sxs-lookup"><span data-stu-id="455b7-204">["good","product"]</span></span>
|<span data-ttu-id="455b7-205">4. 映射價值圖鍵</span><span class="sxs-lookup"><span data-stu-id="455b7-205">4. MapValueToKey</span></span> | <span data-ttu-id="455b7-206">根據輸入資料，將值對應到索引鍵 (類別)</span><span class="sxs-lookup"><span data-stu-id="455b7-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="455b7-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="455b7-207">[1,2]</span></span>
|<span data-ttu-id="455b7-208">5. 生產NGrams</span><span class="sxs-lookup"><span data-stu-id="455b7-208">5. ProduceNGrams</span></span> | <span data-ttu-id="455b7-209">將文字轉換成連續字組的序列</span><span class="sxs-lookup"><span data-stu-id="455b7-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="455b7-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="455b7-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="455b7-211">6. 正常化LpNorm</span><span class="sxs-lookup"><span data-stu-id="455b7-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="455b7-212">使用輸入的 lp-norm 縮放輸入</span><span class="sxs-lookup"><span data-stu-id="455b7-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="455b7-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="455b7-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
