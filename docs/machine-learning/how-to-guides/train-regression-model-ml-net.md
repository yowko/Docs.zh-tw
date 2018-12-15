---
title: 使用 ML.NET 將迴歸模型定型以預測值
description: 探索如何使用 ML.NET 將機器學習迴歸模型定型以預測值
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: e6cd62876f6ac9497e7485b93d4dbd8f95ccc1bb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156526"
---
# <a name="train-a-regression-model-to-predict-a-value-using-mlnet"></a><span data-ttu-id="1dd05-103">使用 ML.NET 將迴歸模型定型以預測值</span><span class="sxs-lookup"><span data-stu-id="1dd05-103">Train a regression model to predict a value using ML.NET</span></span>

<span data-ttu-id="1dd05-104">一般而言，ML.NET 中的模型定型有三個步驟：</span><span class="sxs-lookup"><span data-stu-id="1dd05-104">Generally, there are three steps for model training in ML.NET:</span></span>

1. <span data-ttu-id="1dd05-105">取得 `IDataView` 格式的定型資料</span><span class="sxs-lookup"><span data-stu-id="1dd05-105">Get the training data in a form of an `IDataView`</span></span>
2. <span data-ttu-id="1dd05-106">將「學習管線」建置為一連串的基本「運算子」(估算程式)。</span><span class="sxs-lookup"><span data-stu-id="1dd05-106">Build the 'learning pipeline' as a sequence of elementary 'operators' (estimators).</span></span>
3. <span data-ttu-id="1dd05-107">在管線上呼叫 `Fit`，以取得定型模型。</span><span class="sxs-lookup"><span data-stu-id="1dd05-107">Call `Fit` on the pipeline to obtain the trained model.</span></span>

<span data-ttu-id="1dd05-108">在此[範例檔案](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv)中，預測標籤 (`target`) 是最後一行 (第 12 行)，而其他是特徵：</span><span class="sxs-lookup"><span data-stu-id="1dd05-108">In this [Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv),the predicted label (`target`) is the last column (12th) and all the rest are features:</span></span>

```console
feature_0;feature_1;feature_2;feature_3;feature_4;feature_5;feature_6;feature_7;feature_8;feature_9;feature_10;target
-2.75;0.77;-0.61;0.14;1.39;0.38;-0.53;-0.50;-2.13;-0.39;0.46;140.66
-0.61;-0.37;-0.12;0.55;-1.00;0.84;-0.02;1.30;-0.24;-0.50;-2.12;148.12
-0.85;-0.91;1.81;0.02;-0.78;-1.41;-1.09;-0.65;0.90;-0.37;-0.22;402.20
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // We read the first 11 values as a single float vector.
        new TextLoader.Column("FeatureVector", DataKind.R4, 0, 10),

        // Separately, read the target variable.
        new TextLoader.Column("Target", DataKind.R4, 11),
    },
    // First line of the file is a header, not a data row.
    HasHeader = true,
    Separator = ";"
});

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var trainData = reader.Read(trainDataPath);

// Step two: define the learning pipeline.

// We 'start' the pipeline with the output of the reader.
var pipeline =
    // First 'normalize' the data (rescale to be
    // between -1 and 1 for all examples)
    mlContext.Transforms.Normalize("FeatureVector")
    // Add the SDCA regression trainer.
    .Append(mlContext.Regression.Trainers.StochasticDualCoordinateAscent(label: "Target", features: "FeatureVector"));

// Step three. Fit the pipeline to the training data.
var model = pipeline.Fit(trainData);
```