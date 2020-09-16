---
title: 使用交叉驗證定型機器學習模型
description: 了解如何使用交叉驗證在 ML.NET 中建置更強大的機器學習模型。 交叉驗證是一種定型和模型評估技巧，會將資料分割成幾個分割，在這些分割上定型多個演算法。
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 02cec3d22588d8f10d36216422bc19faafffe94b
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679517"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a>使用交叉驗證定型機器學習模型

了解如何使用交叉驗證在 ML.NET 中定型更強固的機器學習模型。

交叉驗證是一種定型和模型評估技巧，會將資料分割成幾個分割，在這些分割上定型多個演算法。 這項技巧藉由定型程序提供的資料，改善模型的穩定性。 除了提升看不見的觀察值效能之外，在資料限制的環境中，它是使用較小資料集定型模型的有效工具。

## <a name="the-data-and-data-model"></a>資料和資料模型

檔案提供的資料具有下列格式：

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

您可以使用類似的類別模型化資料 `HousingData` ，並將其載入至 [`IDataView`](xref:Microsoft.ML.IDataView) 。

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

## <a name="prepare-the-data"></a>準備資料

先前置處理資料，再用它建置機器學習模型。 在此範例中， `Size` 和資料行會 `HistoricalPrices` 合併成單一特徵向量，輸出到使用方法呼叫的新資料行 `Features` [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) 。 除了將資料變成 ML.NET 演算法預期的格式，串連資料行最佳化管線中的後續作業，方法是將作業一次套用到串連資料行，而不是各個資料行分別套用。

一旦將資料行合併成單一向量， [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) 就會套用至資料 `Features` 行，以取得 `Size` 和 `HistoricalPrices` 在0-1 之間的相同範圍內。

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

## <a name="train-model-with-cross-validation"></a>使用交叉驗證定型模型

一旦資料經過預先處理，就可以定型模型。 首先，選取最能配合機器學習工作執行的演算法。 因為預測的值是數值連續值，所以工作為迴歸。 ML.NET 所執行的其中一個回歸演算法是 [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) 演算法。 若要使用交叉驗證來定型模型，請使用 [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) 方法。

> [!NOTE]
> 雖然這個範例使用線性迴歸模型，但除異常偵測外，CrossValidate 適用於 ML.NET 中的所有其他機器學習工作。

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) 會執行下列作業：

1. 將資料分割成 `numberOfFolds` 參數指定值的數目。 每個分割的結果都是 [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) 物件。
1. 對定型資料集使用指定的機器學習演算法評估工具，在每個分割上定型模型。
1. 每個模型的效能都是使用 [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) 測試資料集上的方法來評估。
1. 針對每個模型傳回模型及其計量。

中儲存的結果 `cvResults` 是物件的集合 [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) 。 此物件包含已定型的模型，以及可分別從和屬性存取的 [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) 度量 [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) 。 在此範例中， `Model` 屬性的型別是 [`ITransformer`](xref:Microsoft.ML.ITransformer) ，而且 `Metrics` 屬性的型別為 [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) 。

## <a name="evaluate-the-model"></a>評估模型

您可以透過個別物件的屬性來存取不同定型模型的計量 `Metrics` [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) 。 在本例中，[R 平方計量](https://en.wikipedia.org/wiki/Coefficient_of_determination)是在變數 `rSquared` 中存取儲存。

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

如果您檢查 `rSquared` 變數的內容，輸出應該是介於 0-1 之間的五個值，接近 1 表示最佳。 使用如 R 平方的計量，選取表現最佳到最差的模型。 然後，選取要進行預測或執行其他作業的最上層模型。

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
