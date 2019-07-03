---
title: 使用 Permutation Feature Importance 說明模型預測
description: 在 ML.NET 中使用 Permutation Feature Importance 了解模型的功能重要性
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 1037a1f1c21ef2c9b9a87a070a7d2003c1e76eb4
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307376"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="1f639-103">使用 Permutation Feature Importance 說明模型預測</span><span class="sxs-lookup"><span data-stu-id="1f639-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="1f639-104">透過了解使用 Permutation Feature Importance (PFI) 之預測的貢獻功能，了解如何解釋 ML.NET 機器學習模型預測。</span><span class="sxs-lookup"><span data-stu-id="1f639-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="1f639-105">機器學習模型常被視為接受輸入和產生輸出的黑箱。</span><span class="sxs-lookup"><span data-stu-id="1f639-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="1f639-106">很少有人了解影響輸出之功能間的中繼步驟或互動。</span><span class="sxs-lookup"><span data-stu-id="1f639-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="1f639-107">隨著更多日常生活層面引入機器學習 (例如醫療保健)，了解機器學習模型所做決策的原因至關重要。</span><span class="sxs-lookup"><span data-stu-id="1f639-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="1f639-108">例如，如果診斷經由機器學習模型確立，醫護專業人員需要能夠查看確立該診斷的因素。</span><span class="sxs-lookup"><span data-stu-id="1f639-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="1f639-109">提供正確的診斷可能會對病患能否快速復原造成極大差異。</span><span class="sxs-lookup"><span data-stu-id="1f639-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="1f639-110">因此，模型的可解釋性層級愈高，醫護專業人員接受或拒絕模型決策的信賴度就愈高。</span><span class="sxs-lookup"><span data-stu-id="1f639-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="1f639-111">解釋模型的技巧各種各樣，PFI 是其中之一。</span><span class="sxs-lookup"><span data-stu-id="1f639-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="1f639-112">PFI 是用來解釋分類和迴歸模型的技巧，受 [Breiman 的 *Random Forests* 報告](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (請參閱第 10 節) 所啟廸。</span><span class="sxs-lookup"><span data-stu-id="1f639-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="1f639-113">概括而言，它的運作方式是針對整個資料集一次一種特性地隨機打亂資料，計算感興趣的效能計量會降低多少。</span><span class="sxs-lookup"><span data-stu-id="1f639-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="1f639-114">變更愈大，該特性愈重要。</span><span class="sxs-lookup"><span data-stu-id="1f639-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="1f639-115">此外，透過醒目提示最重要的特性，模型產生器可以專注於使用可降低雜訊及定型時間之更有意義的部分特性。</span><span class="sxs-lookup"><span data-stu-id="1f639-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="1f639-116">載入資料</span><span class="sxs-lookup"><span data-stu-id="1f639-116">Load the data</span></span>

<span data-ttu-id="1f639-117">資料集用於此範例的特性位在 1-12 行。</span><span class="sxs-lookup"><span data-stu-id="1f639-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="1f639-118">目標是預測 `Price`。</span><span class="sxs-lookup"><span data-stu-id="1f639-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="1f639-119">資料行</span><span class="sxs-lookup"><span data-stu-id="1f639-119">Column</span></span> | <span data-ttu-id="1f639-120">功能</span><span class="sxs-lookup"><span data-stu-id="1f639-120">Feature</span></span> | <span data-ttu-id="1f639-121">說明</span><span class="sxs-lookup"><span data-stu-id="1f639-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="1f639-122">1</span><span class="sxs-lookup"><span data-stu-id="1f639-122">1</span></span> | <span data-ttu-id="1f639-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="1f639-123">CrimeRate</span></span> | <span data-ttu-id="1f639-124">人均犯罪率</span><span class="sxs-lookup"><span data-stu-id="1f639-124">Per capita crime rate</span></span>
| <span data-ttu-id="1f639-125">2</span><span class="sxs-lookup"><span data-stu-id="1f639-125">2</span></span> | <span data-ttu-id="1f639-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="1f639-126">ResidentialZones</span></span> | <span data-ttu-id="1f639-127">城市住宅區</span><span class="sxs-lookup"><span data-stu-id="1f639-127">Residential zones in town</span></span>
| <span data-ttu-id="1f639-128">3</span><span class="sxs-lookup"><span data-stu-id="1f639-128">3</span></span> | <span data-ttu-id="1f639-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="1f639-129">CommercialZones</span></span> | <span data-ttu-id="1f639-130">城市非住宅區</span><span class="sxs-lookup"><span data-stu-id="1f639-130">Non-residential zones in town</span></span>
| <span data-ttu-id="1f639-131">4</span><span class="sxs-lookup"><span data-stu-id="1f639-131">4</span></span> | <span data-ttu-id="1f639-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="1f639-132">NearWater</span></span> | <span data-ttu-id="1f639-133">鄰水區</span><span class="sxs-lookup"><span data-stu-id="1f639-133">Proximity to body of water</span></span>
| <span data-ttu-id="1f639-134">5</span><span class="sxs-lookup"><span data-stu-id="1f639-134">5</span></span> | <span data-ttu-id="1f639-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="1f639-135">ToxicWasteLevels</span></span> | <span data-ttu-id="1f639-136">毒性層級 (PPM)</span><span class="sxs-lookup"><span data-stu-id="1f639-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="1f639-137">6</span><span class="sxs-lookup"><span data-stu-id="1f639-137">6</span></span> | <span data-ttu-id="1f639-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="1f639-138">AverageRoomNumber</span></span> | <span data-ttu-id="1f639-139">家屋平均房間數</span><span class="sxs-lookup"><span data-stu-id="1f639-139">Average number of rooms in house</span></span>
| <span data-ttu-id="1f639-140">7</span><span class="sxs-lookup"><span data-stu-id="1f639-140">7</span></span> | <span data-ttu-id="1f639-141">HomeAge</span><span class="sxs-lookup"><span data-stu-id="1f639-141">HomeAge</span></span> | <span data-ttu-id="1f639-142">家屋年限</span><span class="sxs-lookup"><span data-stu-id="1f639-142">Age of home</span></span>
| <span data-ttu-id="1f639-143">8</span><span class="sxs-lookup"><span data-stu-id="1f639-143">8</span></span> | <span data-ttu-id="1f639-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="1f639-144">BusinessCenterDistance</span></span> | <span data-ttu-id="1f639-145">最近商業區的距離</span><span class="sxs-lookup"><span data-stu-id="1f639-145">Distance to nearest business district</span></span>
| <span data-ttu-id="1f639-146">9</span><span class="sxs-lookup"><span data-stu-id="1f639-146">9</span></span> | <span data-ttu-id="1f639-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="1f639-147">HighwayAccess</span></span> | <span data-ttu-id="1f639-148">鄰近高速公路</span><span class="sxs-lookup"><span data-stu-id="1f639-148">Proximity to highways</span></span>
| <span data-ttu-id="1f639-149">10</span><span class="sxs-lookup"><span data-stu-id="1f639-149">10</span></span> | <span data-ttu-id="1f639-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="1f639-150">TaxRate</span></span> | <span data-ttu-id="1f639-151">房地產稅率</span><span class="sxs-lookup"><span data-stu-id="1f639-151">Property tax rate</span></span>
| <span data-ttu-id="1f639-152">11</span><span class="sxs-lookup"><span data-stu-id="1f639-152">11</span></span> | <span data-ttu-id="1f639-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="1f639-153">StudentTeacherRatio</span></span> | <span data-ttu-id="1f639-154">學生與老師的比率</span><span class="sxs-lookup"><span data-stu-id="1f639-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="1f639-155">12</span><span class="sxs-lookup"><span data-stu-id="1f639-155">12</span></span> | <span data-ttu-id="1f639-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="1f639-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="1f639-157">生活在貧窮線以下的人口百分比</span><span class="sxs-lookup"><span data-stu-id="1f639-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="1f639-158">13</span><span class="sxs-lookup"><span data-stu-id="1f639-158">13</span></span> | <span data-ttu-id="1f639-159">Price</span><span class="sxs-lookup"><span data-stu-id="1f639-159">Price</span></span> | <span data-ttu-id="1f639-160">住屋的價格</span><span class="sxs-lookup"><span data-stu-id="1f639-160">Price of the home</span></span>

<span data-ttu-id="1f639-161">資料集範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f639-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="1f639-162">此範例中的資料可由 `HousingPriceData` 等類別建立模型：</span><span class="sxs-lookup"><span data-stu-id="1f639-162">The data in this sample can be modeled by a class like `HousingPriceData`:</span></span>

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

<span data-ttu-id="1f639-163">將資料載入 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="1f639-163">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="train-the-model"></a><span data-ttu-id="1f639-164">將模型定型</span><span class="sxs-lookup"><span data-stu-id="1f639-164">Train the model</span></span>

<span data-ttu-id="1f639-165">下列程式碼範例會示範定型線性迴歸模型的程序，預測房屋價格。</span><span class="sxs-lookup"><span data-stu-id="1f639-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="1f639-166">說明具有 Permutation Feature Importance (PFI) 的模型</span><span class="sxs-lookup"><span data-stu-id="1f639-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="1f639-167">在 ML.NET 中，使用 [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) 方法處理您的個別工作。</span><span class="sxs-lookup"><span data-stu-id="1f639-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="1f639-168">對定型資料集使用 [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) 的結果是 [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) 物件的 [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray)。</span><span class="sxs-lookup"><span data-stu-id="1f639-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="1f639-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) 提供的摘要統計資料，例如 [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) 多個觀察值的平均值和標準差，等於 `permutationCount` 參數指定的排列數目。</span><span class="sxs-lookup"><span data-stu-id="1f639-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="1f639-170">重要性，或在本例中為 [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) 所計算 R 平方計量的絕對平均下降，可以從最重要排至最不重要。</span><span class="sxs-lookup"><span data-stu-id="1f639-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

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

<span data-ttu-id="1f639-171">列印 `featureImportanceMetrics` 中每個特性的值會產生類似以下輸出。</span><span class="sxs-lookup"><span data-stu-id="1f639-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="1f639-172">請記住，您應該預期會看到不同的結果，因為這些值會隨著指定的資料而變化。</span><span class="sxs-lookup"><span data-stu-id="1f639-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="1f639-173">功能</span><span class="sxs-lookup"><span data-stu-id="1f639-173">Feature</span></span> | <span data-ttu-id="1f639-174">變更為 R 平方</span><span class="sxs-lookup"><span data-stu-id="1f639-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="1f639-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="1f639-175">HighwayAccess</span></span>       |   <span data-ttu-id="1f639-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="1f639-176">-0.042731</span></span>
<span data-ttu-id="1f639-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="1f639-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="1f639-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="1f639-178">-0.012730</span></span>
<span data-ttu-id="1f639-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="1f639-179">BusinessCenterDistance</span></span>| <span data-ttu-id="1f639-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="1f639-180">-0.010491</span></span>
<span data-ttu-id="1f639-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="1f639-181">TaxRate</span></span>             |   <span data-ttu-id="1f639-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="1f639-182">-0.008545</span></span>
<span data-ttu-id="1f639-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="1f639-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="1f639-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="1f639-184">-0.003949</span></span>
<span data-ttu-id="1f639-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="1f639-185">CrimeRate</span></span>           |   <span data-ttu-id="1f639-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="1f639-186">-0.003665</span></span>
<span data-ttu-id="1f639-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="1f639-187">CommercialZones</span></span>     |   <span data-ttu-id="1f639-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="1f639-188">0.002749</span></span>
<span data-ttu-id="1f639-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="1f639-189">HomeAge</span></span>             |   <span data-ttu-id="1f639-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="1f639-190">-0.002426</span></span>
<span data-ttu-id="1f639-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="1f639-191">ResidentialZones</span></span>    |   <span data-ttu-id="1f639-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="1f639-192">-0.002319</span></span>
<span data-ttu-id="1f639-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="1f639-193">NearWater</span></span>           |   <span data-ttu-id="1f639-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="1f639-194">0.000203</span></span>
<span data-ttu-id="1f639-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="1f639-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="1f639-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="1f639-196">0.000031</span></span>
<span data-ttu-id="1f639-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="1f639-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="1f639-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="1f639-198">-0.000019</span></span>

<span data-ttu-id="1f639-199">看一下此資料集中五個最重要的特性，此模型預測的房屋價格受到它們的影響：鄰近高速公路、地區學校的師生比、鄰近主要人才市場、房地產稅率和家屋平均房間數。</span><span class="sxs-lookup"><span data-stu-id="1f639-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
