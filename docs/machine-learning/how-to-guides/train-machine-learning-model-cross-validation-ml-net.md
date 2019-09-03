---
title: 使用交叉驗證定型機器學習模型
description: 了解如何使用交叉驗證在 ML.NET 中建置更強大的機器學習模型。 交叉驗證是一種定型和模型評估技巧，會將資料分割成幾個分割，在這些分割上定型多個演算法。
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: f29103d0cf59cdec10a641b05ce359bf95c01ccd
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169064"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="a79b0-104">使用交叉驗證定型機器學習模型</span><span class="sxs-lookup"><span data-stu-id="a79b0-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="a79b0-105">了解如何使用交叉驗證在 ML.NET 中定型更強固的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="a79b0-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span> 

<span data-ttu-id="a79b0-106">交叉驗證是一種定型和模型評估技巧，會將資料分割成幾個分割，在這些分割上定型多個演算法。</span><span class="sxs-lookup"><span data-stu-id="a79b0-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="a79b0-107">這項技巧藉由定型程序提供的資料，改善模型的穩定性。</span><span class="sxs-lookup"><span data-stu-id="a79b0-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="a79b0-108">除了提升看不見的觀察值效能之外，在資料限制的環境中，它是使用較小資料集定型模型的有效工具。</span><span class="sxs-lookup"><span data-stu-id="a79b0-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="a79b0-109">資料和資料模型</span><span class="sxs-lookup"><span data-stu-id="a79b0-109">The data and data model</span></span>

<span data-ttu-id="a79b0-110">檔案提供的資料具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="a79b0-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="a79b0-111">資料可由 `HousingData` 等類別建立模型，並載入至 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }
 
    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

## <a name="prepare-the-data"></a><span data-ttu-id="a79b0-112">準備資料</span><span class="sxs-lookup"><span data-stu-id="a79b0-112">Prepare the data</span></span>

<span data-ttu-id="a79b0-113">先前置處理資料，再用它建置機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="a79b0-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="a79b0-114">在此範例中，`Size` 和 `HistoricalPrices` 資料行會結合成單一的特性向量，使用 [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) 方法輸出至新的資料行，稱為 `Features`。</span><span class="sxs-lookup"><span data-stu-id="a79b0-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="a79b0-115">除了將資料變成 ML.NET 演算法預期的格式，串連資料行最佳化管線中的後續作業，方法是將作業一次套用到串連資料行，而不是各個資料行分別套用。</span><span class="sxs-lookup"><span data-stu-id="a79b0-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span> 

<span data-ttu-id="a79b0-116">一旦資料行結合成單一的向量，[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) 就會套用至 `Features` 資料行，讓 `Size` 和 `HistoricalPrices` 都在 0-1 間的相同範圍內。</span><span class="sxs-lookup"><span data-stu-id="a79b0-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span> 

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator = 
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="a79b0-117">使用交叉驗證定型模型</span><span class="sxs-lookup"><span data-stu-id="a79b0-117">Train model with cross validation</span></span>

<span data-ttu-id="a79b0-118">一旦資料經過預先處理，就可以定型模型。</span><span class="sxs-lookup"><span data-stu-id="a79b0-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="a79b0-119">首先，選取最能配合機器學習工作執行的演算法。</span><span class="sxs-lookup"><span data-stu-id="a79b0-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="a79b0-120">因為預測的值是數值連續值，所以工作為迴歸。</span><span class="sxs-lookup"><span data-stu-id="a79b0-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="a79b0-121">ML.NET 實作的其中一個迴歸演算法是 [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) 演算法。</span><span class="sxs-lookup"><span data-stu-id="a79b0-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="a79b0-122">使用 [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) 方法以交叉驗證定型模型。</span><span class="sxs-lookup"><span data-stu-id="a79b0-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span> 

> [!NOTE]
> <span data-ttu-id="a79b0-123">雖然這個範例使用線性迴歸模型，但除異常偵測外，CrossValidate 適用於 ML.NET 中的所有其他機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="a79b0-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="a79b0-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) 執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a79b0-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="a79b0-125">將資料分割成 `numberOfFolds` 參數指定值的數目。</span><span class="sxs-lookup"><span data-stu-id="a79b0-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="a79b0-126">每個分割的結果都是 [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) 物件。</span><span class="sxs-lookup"><span data-stu-id="a79b0-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="a79b0-127">對定型資料集使用指定的機器學習演算法評估工具，在每個分割上定型模型。</span><span class="sxs-lookup"><span data-stu-id="a79b0-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="a79b0-128">對測試資料集使用 [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) 方法，評估每個模型的效能。</span><span class="sxs-lookup"><span data-stu-id="a79b0-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span> 
1. <span data-ttu-id="a79b0-129">針對每個模型傳回模型及其計量。</span><span class="sxs-lookup"><span data-stu-id="a79b0-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="a79b0-130">儲存在 `cvResults` 中的結果是 [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="a79b0-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="a79b0-131">此物件包含定型的模型以及計量，可分別從 [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) 和 [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) 屬性中存取。</span><span class="sxs-lookup"><span data-stu-id="a79b0-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="a79b0-132">在此範例中，`Model` 屬性的類型是 [`ITransformer`](xref:Microsoft.ML.ITransformer)，而 `Metrics` 屬性的類型是 [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span> 

## <a name="evaluate-the-model"></a><span data-ttu-id="a79b0-133">評估模型</span><span class="sxs-lookup"><span data-stu-id="a79b0-133">Evaluate the model</span></span>

<span data-ttu-id="a79b0-134">您可以透過個別 [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) 物件的 `Metrics` 屬性存取不同定型模型的計量。</span><span class="sxs-lookup"><span data-stu-id="a79b0-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="a79b0-135">在本例中，[R 平方計量](https://en.wikipedia.org/wiki/Coefficient_of_determination)是在變數 `rSquared` 中存取儲存。</span><span class="sxs-lookup"><span data-stu-id="a79b0-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span> 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="a79b0-136">如果您檢查 `rSquared` 變數的內容，輸出應該是介於 0-1 之間的五個值，接近 1 表示最佳。</span><span class="sxs-lookup"><span data-stu-id="a79b0-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="a79b0-137">使用如 R 平方的計量，選取表現最佳到最差的模型。</span><span class="sxs-lookup"><span data-stu-id="a79b0-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="a79b0-138">然後，選取要進行預測或執行其他作業的最上層模型。</span><span class="sxs-lookup"><span data-stu-id="a79b0-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
