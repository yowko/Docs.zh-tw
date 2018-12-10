---
title: 使用正常化來前置處理訓練資料，以用於資料處理 - ML.NET
description: 了解如何使用正常化工具來前置處理訓練資料，以用於使用 ML.NET 進行的機器學習模型建置、訓練及評分
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c8b959904705e996c97bdcd8b3444e754d14d046
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148830"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a><span data-ttu-id="9259b-103">使用正常化來前置處理訓練資料，以用於資料處理 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="9259b-103">Preprocess training data with normalizers to use in data processing - ML.NET</span></span>

<span data-ttu-id="9259b-104">ML.NET 公開了許多[參數及非參數演算法](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)。</span><span class="sxs-lookup"><span data-stu-id="9259b-104">ML.NET exposes a number of [parametric and non-parametric algorithms](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span></span>

<span data-ttu-id="9259b-105">選擇哪種正常化工具並**不**比在訓練線性或其他參數模型時**使用**正常化工具來得重要。</span><span class="sxs-lookup"><span data-stu-id="9259b-105">It's **not** as important which normalizer you choose as it is to **use** a normalizer when training linear or other parametric models.</span></span>

<span data-ttu-id="9259b-106">請一律直接在 ML.NET 學習管線中包含正常化工具，確保其：</span><span class="sxs-lookup"><span data-stu-id="9259b-106">Always include the normalizer directly in the ML.NET learning pipeline, so it:</span></span>

- <span data-ttu-id="9259b-107">只在訓練資料 (而不在測試資料) 上接受訓練，</span><span class="sxs-lookup"><span data-stu-id="9259b-107">is only trained on the training data, and not on your test data,</span></span>
- <span data-ttu-id="9259b-108">正確地套用至所有新的傳入資料，而不需在預測時間另外前置處理。</span><span class="sxs-lookup"><span data-stu-id="9259b-108">is correctly applied to all the new incoming data, without the need for extra pre-processing at prediction time.</span></span>

<span data-ttu-id="9259b-109">下列為在學習管線中示範正規化的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="9259b-109">Here's a snippet of code that demonstrates normalization in learning pipelines.</span></span> <span data-ttu-id="9259b-110">其假設 Iris 資料集：</span><span class="sxs-lookup"><span data-stu-id="9259b-110">It assumes the Iris dataset:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("Features", DataKind.R4, 0, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    // Default separator is tab, but the dataset has comma.
    Separator = ","
});

// Read the training data.
var trainData = reader.Read(dataPath);

// Apply all kinds of standard ML.NET normalization to the raw features.
var pipeline =
    mlContext.Transforms.Normalize(
        new NormalizingEstimator.MinMaxColumn("Features", "MinMaxNormalized", fixZero: true),
        new NormalizingEstimator.MeanVarColumn("Features", "MeanVarNormalized", fixZero: true),
        new NormalizingEstimator.BinningColumn("Features", "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
