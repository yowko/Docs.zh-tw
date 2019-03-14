---
title: 使用正常化來前置處理訓練資料，以用於資料處理 - ML.NET
description: 了解如何使用正常化工具來前置處理訓練資料，以用於使用 ML.NET 進行的機器學習模型建置、訓練及評分
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2d18f7c19a51fd929ac6efb7f600cb1ac2733de8
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676599"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a><span data-ttu-id="1b967-103">使用正常化來前置處理訓練資料，以用於資料處理 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="1b967-103">Preprocess training data with normalizers to use in data processing - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="1b967-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="1b967-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="1b967-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="1b967-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="1b967-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="1b967-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="1b967-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="1b967-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="1b967-108">ML.NET 公開了許多[參數及非參數演算法](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)。</span><span class="sxs-lookup"><span data-stu-id="1b967-108">ML.NET exposes a number of [parametric and non-parametric algorithms](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span></span>

<span data-ttu-id="1b967-109">選擇哪種正常化工具並**不**比在訓練線性或其他參數模型時**使用**正常化工具來得重要。</span><span class="sxs-lookup"><span data-stu-id="1b967-109">It's **not** as important which normalizer you choose as it is to **use** a normalizer when training linear or other parametric models.</span></span>

<span data-ttu-id="1b967-110">請一律直接在 ML.NET 學習管線中包含正常化工具，確保其：</span><span class="sxs-lookup"><span data-stu-id="1b967-110">Always include the normalizer directly in the ML.NET learning pipeline, so it:</span></span>

- <span data-ttu-id="1b967-111">只在訓練資料 (而不在測試資料) 上接受訓練，</span><span class="sxs-lookup"><span data-stu-id="1b967-111">is only trained on the training data, and not on your test data,</span></span>
- <span data-ttu-id="1b967-112">正確地套用至所有新的傳入資料，而不需在預測時間另外前置處理。</span><span class="sxs-lookup"><span data-stu-id="1b967-112">is correctly applied to all the new incoming data, without the need for extra pre-processing at prediction time.</span></span>

<span data-ttu-id="1b967-113">下列為在學習管線中示範正規化的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="1b967-113">Here's a snippet of code that demonstrates normalization in learning pipelines.</span></span> <span data-ttu-id="1b967-114">其假設 Iris 資料集：</span><span class="sxs-lookup"><span data-stu-id="1b967-114">It assumes the Iris dataset:</span></span>

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
