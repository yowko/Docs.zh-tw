---
title: 使用正常化來前置處理訓練資料，以用於資料處理 - ML.NET
description: 了解如何使用正常化工具來前置處理訓練資料，以用於使用 ML.NET 進行的機器學習模型建置、訓練及評分
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 28d358cd381f71b4116e1dd25d847fc51835f09e
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093043"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a>使用正常化來前置處理訓練資料，以用於資料處理 - ML.NET

ML.NET 公開了許多[參數及非參數演算法](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)。

選擇哪種正常化工具並**不**比在訓練線性或其他參數模型時**使用**正常化工具來得重要。

請一律直接在 ML.NET 學習管線中包含正常化工具，確保其：

- 只在訓練資料 (而不在測試資料) 上接受訓練，
- 正確地套用至所有新的傳入資料，而不需在預測時間另外前置處理。

下列為在學習管線中示範正規化的程式碼片段。 其假設 Iris 資料集：

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("Features",DataKind.R4,0,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    // Default separator is tab, but the dataset has comma.
    separatorChar: ',',
    // First line of the file is a header, not a data row.
    hasHeader: true
);

// Read the training data.
var trainData = reader.Read(dataPath);

// Apply all kinds of standard ML.NET normalization to the raw features.
var pipeline =
    mlContext.Transforms.Normalize(
            new NormalizingEstimator.MinMaxColumn(inputColumnName:"Features", outputColumnName:"MinMaxNormalized", fixZero: true),
            new NormalizingEstimator.MeanVarColumn(inputColumnName: "Features", outputColumnName: "MeanVarNormalized", fixZero: true),
            new NormalizingEstimator.BinningColumn(inputColumnName: "Features", outputColumnName: "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
