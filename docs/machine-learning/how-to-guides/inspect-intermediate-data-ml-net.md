---
title: 在 ML.NET 管線處理期間檢查中繼資料值
description: 了解如何在 ML.NET 機器學習管線處理期間檢查實際中繼資料值
ms.date: 01/30/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b3a554bf7cd88219a66f91a18b9d983bb91c0f0e
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675006"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="c2a3b-103">在 ML.NET 管線處理期間檢查中繼資料值</span><span class="sxs-lookup"><span data-stu-id="c2a3b-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

<span data-ttu-id="c2a3b-104">在實驗期間，您可能會想在某一時間點觀察及驗證資料處理結果。</span><span class="sxs-lookup"><span data-stu-id="c2a3b-104">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="c2a3b-105">這並不容易，因為 ML.NET 作業是消極、建構式的物件，是資料的 'promises'。</span><span class="sxs-lookup"><span data-stu-id="c2a3b-105">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="c2a3b-106">`GetColumn<T>` 擴充方法可讓您檢查中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c2a3b-106">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="c2a3b-107">其以 `IEnumerable` 的形式傳回一個資料欄位的內容。</span><span class="sxs-lookup"><span data-stu-id="c2a3b-107">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="c2a3b-108">下列範例顯示 `GetColumn<T>` 擴充方法的使用方法：</span><span class="sxs-lookup"><span data-stu-id="c2a3b-108">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="c2a3b-109">[範例檔案](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt)：</span><span class="sxs-lookup"><span data-stu-id="c2a3b-109">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```

<span data-ttu-id="c2a3b-110">我們的類別定義如下：</span><span class="sxs-lookup"><span data-stu-id="c2a3b-110">Our class is defined as follows:</span></span>

```csharp
public class InspectedRow
{
    [LoadColumn(0)]
    public bool IsOver50K { get; set; }
    [LoadColumn(1)]
    public string WorkClass { get; set; }
    [LoadColumn(2)]
    public string Education { get; set; }
    [LoadColumn(3)]
    public string MaritalStatus { get; set; }
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Read the data into a data view.
var data = mlContext.Data.ReadFromTextFile<InspectedRow>(dataPath, hasHeader: true);

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "WorkClass", "Education", "MaritalStatus");

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns =
    transformedData
        .GetColumn<string[]>(mlContext, "AllFeatures")
        .Take(20)
        .ToArray();
```
