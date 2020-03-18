---
title: 使用具有排列特徵重要性的ML.NET模型進行解釋
description: 在 ML.NET 中使用 Permutation Feature Importance 了解模型的功能重要性
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092612"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a>使用排列特徵重要性解釋模型預測

使用排列功能重要性 （PFI），瞭解如何解釋ML.NET機器學習模型預測。 PFI 提供每個要素對預測的相對貢獻。

機器學習模型常被視為接受輸入和產生輸出的黑箱。 很少有人了解影響輸出之功能間的中繼步驟或互動。 隨著更多日常生活層面引入機器學習 (例如醫療保健)，了解機器學習模型所做決策的原因至關重要。 例如，如果診斷經由機器學習模型確立，醫護專業人員需要能夠查看確立該診斷的因素。 提供正確的診斷可能會對病患能否快速復原造成極大差異。 因此，模型的可解釋性層級愈高，醫護專業人員接受或拒絕模型決策的信賴度就愈高。

解釋模型的技巧各種各樣，PFI 是其中之一。 PFI 是一種用於解釋分類和回歸模型的技術，其靈感來自[布賴曼的*隨機森林*論文](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)（參見第 10 節）。 概括而言，它的運作方式是針對整個資料集一次一種特性地隨機打亂資料，計算感興趣的效能計量會降低多少。 變更愈大，該特性愈重要。

此外，透過醒目提示最重要的特性，模型產生器可以專注於使用可降低雜訊及定型時間之更有意義的部分特性。

## <a name="load-the-data"></a>載入資料

資料集用於此範例的特性位在 1-12 行。 目標是預測 `Price`。

| 資料行 | 功能 | 描述
| --- | --- | --- |
| 1 | CrimeRate | 人均犯罪率
| 2 | ResidentialZones | 城市住宅區
| 3 | CommercialZones | 城市非住宅區
| 4 | NearWater | 鄰水區
| 5 | ToxicWasteLevels | 毒性層級 (PPM)
| 6 | AverageRoomNumber | 家屋平均房間數
| 7 | HomeAge | 家屋年限
| 8 | BusinessCenterDistance | 最近商業區的距離
| 9 | HighwayAccess | 鄰近高速公路
| 10 | TaxRate | 房地產稅率
| 11 | StudentTeacherRatio | 學生與老師的比率
| 12 | PercentPopulationBelowPoverty | 生活在貧窮線以下的人口百分比
| 13 | Price | 住屋的價格

資料集範例如下所示：

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

此示例中的資料可以由類（如`HousingPriceData`）建模並載入到 中。 [`IDataView`](xref:Microsoft.ML.IDataView)

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

## <a name="train-the-model"></a>將模型定型

下列程式碼範例會示範定型線性迴歸模型的程序，預測房屋價格。

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>說明具有 Permutation Feature Importance (PFI) 的模型

在ML.NET將[`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions)方法用於相應的任務。

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

在訓練資料集上[`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions)使用的結果是[`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray)[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)物件。 [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)為多個觀測值提供匯總統計資訊，如平均值和標準[`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)差，這些觀測值等於`permutationCount`參數指定的排列數。

重要性，或在這種情況下，由[`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions)計算的 R 平方指標的絕對平均下降可以從最重要到最不重要進行排序。

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

列印 `featureImportanceMetrics` 中每個特性的值會產生類似以下輸出。 請記住，您應該預期會看到不同的結果，因為這些值會隨著指定的資料而變化。

| 功能 | 變更為 R 平方 |
|:--|:--:|
HighwayAccess       |   -0.042731
StudentTeacherRatio |   -0.012730
BusinessCenterDistance| -0.010491
TaxRate             |   -0.008545
AverageRoomNumber   |   -0.003949
CrimeRate           |   -0.003665
CommercialZones     |   0.002749
HomeAge             |   -0.002426
ResidentialZones    |   -0.002319
NearWater           |   0.000203
PercentPopulationLivingBelowPoverty|    0.000031
ToxicWasteLevels    |   -0.000019

看一下此資料集中五個最重要的特性，此模型預測的房屋價格受到它們的影響：鄰近高速公路、地區學校的師生比、鄰近主要人才市場、房地產稅率和家屋平均房間數。
