---
title: 套用特徵工程以對類別目錄資料進行模型定型 - ML.NET
description: 了解如何使用 ML.NET 在類別目錄資料上為機器學習模型套用特徵工程
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: eedbe0499784e7a99b0101c42892652daef3a114
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968409"
---
# <a name="apply-feature-engineering-for-model-training-on-categorical-data---mlnet"></a><span data-ttu-id="c04cf-103">套用特徵工程以對類別目錄資料進行模型定型 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="c04cf-103">Apply feature engineering for model training on categorical data - ML.NET</span></span>

<span data-ttu-id="c04cf-104">因為所有 ML.NET `learners` 都預期功能會是 `float vector`，所以您需要將所有非 float 資料轉換成 `float` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c04cf-104">You need to convert any non float data to `float` data types since all ML.NET `learners` expect features as a `float vector`.</span></span>

<span data-ttu-id="c04cf-105">如果資料集包含 `categorical` 資料 (例如，'enum')，ML.NET 提供幾種方法將它轉換成特徵：</span><span class="sxs-lookup"><span data-stu-id="c04cf-105">If the dataset contains `categorical` data (for example, 'enum'), ML.NET offers several ways of converting it to features:</span></span>

- <span data-ttu-id="c04cf-106">One-Hot 編碼</span><span class="sxs-lookup"><span data-stu-id="c04cf-106">One-hot encoding</span></span>
- <span data-ttu-id="c04cf-107">雜湊型 One-Hot 編碼</span><span class="sxs-lookup"><span data-stu-id="c04cf-107">Hash-based one-hot encoding</span></span>
- <span data-ttu-id="c04cf-108">二進位編碼 (將類別索引轉換成位元序列，並使用位元作為特徵)</span><span class="sxs-lookup"><span data-stu-id="c04cf-108">Binary encoding (convert category index into a bit sequence and use bits as features)</span></span>

<span data-ttu-id="c04cf-109">如果某些類別是非常高基數的 (有許多不同的值，經常出現的為小型集合)，則使用 `one-hot encoding` 可能會浪費資源。</span><span class="sxs-lookup"><span data-stu-id="c04cf-109">A `one-hot encoding` can be wasteful if some categories are very high-cardinality (lots of different values, with a small set commonly occurring.</span></span> <span data-ttu-id="c04cf-110">在此情況下，請減少使用計數型特徵選取來編碼之位置的數目。</span><span class="sxs-lookup"><span data-stu-id="c04cf-110">In that case, reduce the number of slots to encode with count-based feature selection.</span></span>

<span data-ttu-id="c04cf-111">將類別目錄特徵化直接包含在 ML.NET 學習管線中，以確保類別目錄轉換：</span><span class="sxs-lookup"><span data-stu-id="c04cf-111">Include categorical featurization directly in the ML.NET learning pipeline to ensure that the categorical transformation:</span></span>

- <span data-ttu-id="c04cf-112">只在定型資料 (而不在測試資料) 上接受「定型」、</span><span class="sxs-lookup"><span data-stu-id="c04cf-112">is only 'trained' on the training data, and not on your test data,</span></span>
- <span data-ttu-id="c04cf-113">正確地套用至新的內送資料、在預測時間沒有額外的前置處理。</span><span class="sxs-lookup"><span data-stu-id="c04cf-113">is correctly applied to new incoming data, without extra pre-processing at prediction time.</span></span>

<span data-ttu-id="c04cf-114">以下範例說明[成人人口普查資料集](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt)的類別目錄處理：</span><span class="sxs-lookup"><span data-stu-id="c04cf-114">The following example illustrates categorical handling for the [adult census dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span></span>

```console
Label   Workclass   education   marital-status  occupation  relationship    ethnicity   sex native-country-region   age fnlwgt  education-num   capital-gain    capital-loss    hours-per-week
0   Private 11th    Never-married   Machine-op-inspct   Own-child   Black   Male    United-States   25  226802  7   0   0   40
0   Private HS-grad Married-civ-spouse  Farming-fishing Husband White   Male    United-States   38  89814   9   0   0   50
1   Local-gov   Assoc-acdm  Married-civ-spouse  Protective-serv Husband White   Male    United-States   28  336951  12  0   0   40
1   Private Some-college    Married-civ-spouse  Machine-op-inspct   Husband Black   Male    United-States   44  160323  10  7688    0   40
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(new[] 
    {
        new TextLoader.Column("Label", DataKind.BL, 0),
        // We will load all the categorical features into one vector column of size 8.
        new TextLoader.Column("CategoricalFeatures", DataKind.TX, 1, 8),
        // Similarly, load all numerical features into one vector of size 6.
        new TextLoader.Column("NumericalFeatures", DataKind.R4, 9, 14),
        // Let's also separately load the 'Workclass' column.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
    },
    hasHeader: true
);

// Read the data.
var data = reader.Read(dataPath);

// Inspect the first 10 records of the categorical columns to check that they are correctly read.
var catColumns = data.GetColumn<string[]>(mlContext, "CategoricalFeatures").Take(10).ToArray();

// Build several alternative featurization pipelines.
var pipeline =
    // Convert each categorical feature into one-hot encoding independently.
    mlContext.Transforms.Categorical.OneHotEncoding("CategoricalFeatures", "CategoricalOneHot")
        // Convert all categorical features into indices, and build a 'word bag' of these.
        .Append(mlContext.Transforms.Categorical.OneHotEncoding("CategoricalFeatures", "CategoricalBag",OneHotEncodingTransformer.OutputKind.Bag))
        // One-hot encode the workclass column, then drop all the categories that have fewer than 10 instances in the train set.
        .Append(mlContext.Transforms.Categorical.OneHotEncoding("Workclass", "WorkclassOneHot"))
        .Append(mlContext.Transforms.FeatureSelection.SelectFeaturesBasedOnCount("WorkclassOneHot", "WorkclassOneHotTrimmed", count: 10));

// Let's train our pipeline, and then apply it to the same data.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var categoricalBags = transformedData.GetColumn<float[]>(mlContext, "CategoricalBag").Take(10).ToArray();
var workclasses = transformedData.GetColumn<float[]>(mlContext, "WorkclassOneHotTrimmed").Take(10).ToArray();

// Of course, if we want to train the model, we will need to compose a single float vector of all the features.
// Here's how we could do this:

var fullLearningPipeline = pipeline
    // Concatenate two of the 3 categorical pipelines, and the numeric features.
    .Append(mlContext.Transforms.Concatenate("Features", "NumericalFeatures", "CategoricalBag", "WorkclassOneHotTrimmed"))
    // Cache data in memory so that the following trainer will be able to access training examples without
    // reading them from disk multiple times.
    .AppendCacheCheckpoint(mlContext)
    // Now we're ready to train. We chose our FastTree trainer for this classification task.
    .Append(mlContext.BinaryClassification.Trainers.FastTree(numTrees: 50));

// Train the model.
var model = fullLearningPipeline.Fit(data);
```
