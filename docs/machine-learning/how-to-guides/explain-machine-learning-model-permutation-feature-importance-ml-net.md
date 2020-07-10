---
title: 使用排列功能重要性來解讀 ML.NET 模型
description: 在 ML.NET 中使用 Permutation Feature Importance 了解模型的功能重要性
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: ed0d6736f1f2e988d96a397cad77a7fc743489da
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174227"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="63d7b-103">使用排列功能重要性來解讀模型預測</span><span class="sxs-lookup"><span data-stu-id="63d7b-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="63d7b-104">使用排列功能重要性 (PFI) ，瞭解如何解讀 ML.NET 機器學習模型預測。</span><span class="sxs-lookup"><span data-stu-id="63d7b-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="63d7b-105">PFI 會提供每項功能對預測的相對比重。</span><span class="sxs-lookup"><span data-stu-id="63d7b-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="63d7b-106">機器學習模型通常會被視為不透明的方塊，它會接受輸入並產生輸出。</span><span class="sxs-lookup"><span data-stu-id="63d7b-106">Machine learning models are often thought of as opaque boxes that take inputs and generate an output.</span></span> <span data-ttu-id="63d7b-107">很少有人了解影響輸出之功能間的中繼步驟或互動。</span><span class="sxs-lookup"><span data-stu-id="63d7b-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="63d7b-108">隨著更多日常生活層面引入機器學習 (例如醫療保健)，了解機器學習模型所做決策的原因至關重要。</span><span class="sxs-lookup"><span data-stu-id="63d7b-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="63d7b-109">例如，如果診斷經由機器學習模型確立，醫護專業人員需要能夠查看確立該診斷的因素。</span><span class="sxs-lookup"><span data-stu-id="63d7b-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="63d7b-110">提供正確的診斷可能會對病患能否快速復原造成極大差異。</span><span class="sxs-lookup"><span data-stu-id="63d7b-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="63d7b-111">因此，模型的可解釋性層級愈高，醫護專業人員接受或拒絕模型決策的信賴度就愈高。</span><span class="sxs-lookup"><span data-stu-id="63d7b-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="63d7b-112">解釋模型的技巧各種各樣，PFI 是其中之一。</span><span class="sxs-lookup"><span data-stu-id="63d7b-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="63d7b-113">PFI 是一種技術，用來說明[Breiman 的*隨機*](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)樹系論文所能啟發的分類和回歸模型 (請參閱第10節) 。</span><span class="sxs-lookup"><span data-stu-id="63d7b-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="63d7b-114">概括而言，它的運作方式是針對整個資料集一次一種特性地隨機打亂資料，計算感興趣的效能計量會降低多少。</span><span class="sxs-lookup"><span data-stu-id="63d7b-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="63d7b-115">變更愈大，該特性愈重要。</span><span class="sxs-lookup"><span data-stu-id="63d7b-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="63d7b-116">此外，透過醒目提示最重要的特性，模型產生器可以專注於使用可降低雜訊及定型時間之更有意義的部分特性。</span><span class="sxs-lookup"><span data-stu-id="63d7b-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="63d7b-117">載入資料</span><span class="sxs-lookup"><span data-stu-id="63d7b-117">Load the data</span></span>

<span data-ttu-id="63d7b-118">資料集用於此範例的特性位在 1-12 行。</span><span class="sxs-lookup"><span data-stu-id="63d7b-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="63d7b-119">目標是預測 `Price`。</span><span class="sxs-lookup"><span data-stu-id="63d7b-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="63d7b-120">Column</span><span class="sxs-lookup"><span data-stu-id="63d7b-120">Column</span></span> | <span data-ttu-id="63d7b-121">功能</span><span class="sxs-lookup"><span data-stu-id="63d7b-121">Feature</span></span> | <span data-ttu-id="63d7b-122">描述</span><span class="sxs-lookup"><span data-stu-id="63d7b-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="63d7b-123">1</span><span class="sxs-lookup"><span data-stu-id="63d7b-123">1</span></span> | <span data-ttu-id="63d7b-124">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="63d7b-124">CrimeRate</span></span> | <span data-ttu-id="63d7b-125">人均犯罪率</span><span class="sxs-lookup"><span data-stu-id="63d7b-125">Per capita crime rate</span></span>
| <span data-ttu-id="63d7b-126">2</span><span class="sxs-lookup"><span data-stu-id="63d7b-126">2</span></span> | <span data-ttu-id="63d7b-127">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="63d7b-127">ResidentialZones</span></span> | <span data-ttu-id="63d7b-128">城市住宅區</span><span class="sxs-lookup"><span data-stu-id="63d7b-128">Residential zones in town</span></span>
| <span data-ttu-id="63d7b-129">3</span><span class="sxs-lookup"><span data-stu-id="63d7b-129">3</span></span> | <span data-ttu-id="63d7b-130">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="63d7b-130">CommercialZones</span></span> | <span data-ttu-id="63d7b-131">城市非住宅區</span><span class="sxs-lookup"><span data-stu-id="63d7b-131">Non-residential zones in town</span></span>
| <span data-ttu-id="63d7b-132">4</span><span class="sxs-lookup"><span data-stu-id="63d7b-132">4</span></span> | <span data-ttu-id="63d7b-133">NearWater</span><span class="sxs-lookup"><span data-stu-id="63d7b-133">NearWater</span></span> | <span data-ttu-id="63d7b-134">鄰水區</span><span class="sxs-lookup"><span data-stu-id="63d7b-134">Proximity to body of water</span></span>
| <span data-ttu-id="63d7b-135">5</span><span class="sxs-lookup"><span data-stu-id="63d7b-135">5</span></span> | <span data-ttu-id="63d7b-136">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="63d7b-136">ToxicWasteLevels</span></span> | <span data-ttu-id="63d7b-137">毒性層級 (PPM)</span><span class="sxs-lookup"><span data-stu-id="63d7b-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="63d7b-138">6</span><span class="sxs-lookup"><span data-stu-id="63d7b-138">6</span></span> | <span data-ttu-id="63d7b-139">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="63d7b-139">AverageRoomNumber</span></span> | <span data-ttu-id="63d7b-140">家屋平均房間數</span><span class="sxs-lookup"><span data-stu-id="63d7b-140">Average number of rooms in house</span></span>
| <span data-ttu-id="63d7b-141">7</span><span class="sxs-lookup"><span data-stu-id="63d7b-141">7</span></span> | <span data-ttu-id="63d7b-142">HomeAge</span><span class="sxs-lookup"><span data-stu-id="63d7b-142">HomeAge</span></span> | <span data-ttu-id="63d7b-143">家屋年限</span><span class="sxs-lookup"><span data-stu-id="63d7b-143">Age of home</span></span>
| <span data-ttu-id="63d7b-144">8</span><span class="sxs-lookup"><span data-stu-id="63d7b-144">8</span></span> | <span data-ttu-id="63d7b-145">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="63d7b-145">BusinessCenterDistance</span></span> | <span data-ttu-id="63d7b-146">最近商業區的距離</span><span class="sxs-lookup"><span data-stu-id="63d7b-146">Distance to nearest business district</span></span>
| <span data-ttu-id="63d7b-147">9</span><span class="sxs-lookup"><span data-stu-id="63d7b-147">9</span></span> | <span data-ttu-id="63d7b-148">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="63d7b-148">HighwayAccess</span></span> | <span data-ttu-id="63d7b-149">鄰近高速公路</span><span class="sxs-lookup"><span data-stu-id="63d7b-149">Proximity to highways</span></span>
| <span data-ttu-id="63d7b-150">10</span><span class="sxs-lookup"><span data-stu-id="63d7b-150">10</span></span> | <span data-ttu-id="63d7b-151">TaxRate</span><span class="sxs-lookup"><span data-stu-id="63d7b-151">TaxRate</span></span> | <span data-ttu-id="63d7b-152">房地產稅率</span><span class="sxs-lookup"><span data-stu-id="63d7b-152">Property tax rate</span></span>
| <span data-ttu-id="63d7b-153">11</span><span class="sxs-lookup"><span data-stu-id="63d7b-153">11</span></span> | <span data-ttu-id="63d7b-154">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="63d7b-154">StudentTeacherRatio</span></span> | <span data-ttu-id="63d7b-155">學生與老師的比率</span><span class="sxs-lookup"><span data-stu-id="63d7b-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="63d7b-156">12</span><span class="sxs-lookup"><span data-stu-id="63d7b-156">12</span></span> | <span data-ttu-id="63d7b-157">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="63d7b-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="63d7b-158">生活在貧窮線以下的人口百分比</span><span class="sxs-lookup"><span data-stu-id="63d7b-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="63d7b-159">13</span><span class="sxs-lookup"><span data-stu-id="63d7b-159">13</span></span> | <span data-ttu-id="63d7b-160">價格</span><span class="sxs-lookup"><span data-stu-id="63d7b-160">Price</span></span> | <span data-ttu-id="63d7b-161">住屋的價格</span><span class="sxs-lookup"><span data-stu-id="63d7b-161">Price of the home</span></span>

<span data-ttu-id="63d7b-162">資料集範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="63d7b-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="63d7b-163">這個範例中的資料可以透過之類的類別模型化 `HousingPriceData` ，並載入至 [`IDataView`](xref:Microsoft.ML.IDataView) 。</span><span class="sxs-lookup"><span data-stu-id="63d7b-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

## <a name="train-the-model"></a><span data-ttu-id="63d7b-164">定型模型</span><span class="sxs-lookup"><span data-stu-id="63d7b-164">Train the model</span></span>

<span data-ttu-id="63d7b-165">下列程式碼範例會示範定型線性迴歸模型的程序，預測房屋價格。</span><span class="sxs-lookup"><span data-stu-id="63d7b-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames =
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="63d7b-166">說明具有 Permutation Feature Importance (PFI) 的模型</span><span class="sxs-lookup"><span data-stu-id="63d7b-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="63d7b-167">在 ML.NET 中， [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) 針對您的個別工作使用方法。</span><span class="sxs-lookup"><span data-stu-id="63d7b-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="63d7b-168">[`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions)在訓練資料集上使用的結果是 [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) 物件的 [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) 。</span><span class="sxs-lookup"><span data-stu-id="63d7b-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="63d7b-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)提供的摘要統計資料，如平均和標準差，適用于多個 [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) 等於參數所指定之排列數目的觀察 `permutationCount` 。</span><span class="sxs-lookup"><span data-stu-id="63d7b-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="63d7b-170">重要性，或在此情況下，由計算的 R 平方標準中的絕對平均減少， [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) 可以從最重要到最重要的順序排序。</span><span class="sxs-lookup"><span data-stu-id="63d7b-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

<span data-ttu-id="63d7b-171">列印 `featureImportanceMetrics` 中每個特性的值會產生類似以下輸出。</span><span class="sxs-lookup"><span data-stu-id="63d7b-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="63d7b-172">請記住，您應該預期會看到不同的結果，因為這些值會隨著指定的資料而變化。</span><span class="sxs-lookup"><span data-stu-id="63d7b-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="63d7b-173">功能</span><span class="sxs-lookup"><span data-stu-id="63d7b-173">Feature</span></span> | <span data-ttu-id="63d7b-174">變更為 R 平方</span><span class="sxs-lookup"><span data-stu-id="63d7b-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="63d7b-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="63d7b-175">HighwayAccess</span></span>       |   <span data-ttu-id="63d7b-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="63d7b-176">-0.042731</span></span>
<span data-ttu-id="63d7b-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="63d7b-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="63d7b-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="63d7b-178">-0.012730</span></span>
<span data-ttu-id="63d7b-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="63d7b-179">BusinessCenterDistance</span></span>| <span data-ttu-id="63d7b-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="63d7b-180">-0.010491</span></span>
<span data-ttu-id="63d7b-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="63d7b-181">TaxRate</span></span>             |   <span data-ttu-id="63d7b-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="63d7b-182">-0.008545</span></span>
<span data-ttu-id="63d7b-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="63d7b-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="63d7b-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="63d7b-184">-0.003949</span></span>
<span data-ttu-id="63d7b-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="63d7b-185">CrimeRate</span></span>           |   <span data-ttu-id="63d7b-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="63d7b-186">-0.003665</span></span>
<span data-ttu-id="63d7b-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="63d7b-187">CommercialZones</span></span>     |   <span data-ttu-id="63d7b-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="63d7b-188">0.002749</span></span>
<span data-ttu-id="63d7b-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="63d7b-189">HomeAge</span></span>             |   <span data-ttu-id="63d7b-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="63d7b-190">-0.002426</span></span>
<span data-ttu-id="63d7b-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="63d7b-191">ResidentialZones</span></span>    |   <span data-ttu-id="63d7b-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="63d7b-192">-0.002319</span></span>
<span data-ttu-id="63d7b-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="63d7b-193">NearWater</span></span>           |   <span data-ttu-id="63d7b-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="63d7b-194">0.000203</span></span>
<span data-ttu-id="63d7b-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="63d7b-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="63d7b-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="63d7b-196">0.000031</span></span>
<span data-ttu-id="63d7b-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="63d7b-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="63d7b-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="63d7b-198">-0.000019</span></span>

<span data-ttu-id="63d7b-199">看一下此資料集中五個最重要的特性，此模型預測的房屋價格受到它們的影響：鄰近高速公路、地區學校的師生比、鄰近主要人才市場、房地產稅率和家屋平均房間數。</span><span class="sxs-lookup"><span data-stu-id="63d7b-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
