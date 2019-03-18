---
title: 在 ML.NET 管線處理期間檢查中繼資料值
description: 了解如何在 ML.NET 機器學習管線處理期間檢查實際中繼資料值
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 362cb9351c3cb77b6aa67d59154854e882869ad9
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843412"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="36ee4-103">在 ML.NET 管線處理期間檢查中繼資料值</span><span class="sxs-lookup"><span data-stu-id="36ee4-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

> [!NOTE]
> <span data-ttu-id="36ee4-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="36ee4-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="36ee4-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="36ee4-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="36ee4-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="36ee4-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="36ee4-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="36ee4-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="36ee4-108">在實驗期間，您可能會想在某一時間點觀察及驗證資料處理結果。</span><span class="sxs-lookup"><span data-stu-id="36ee4-108">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="36ee4-109">這並不容易，因為 ML.NET 作業是消極、建構式的物件，是資料的 'promises'。</span><span class="sxs-lookup"><span data-stu-id="36ee4-109">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="36ee4-110">`GetColumn<T>` 擴充方法可讓您檢查中繼資料。</span><span class="sxs-lookup"><span data-stu-id="36ee4-110">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="36ee4-111">其以 `IEnumerable` 的形式傳回一個資料欄位的內容。</span><span class="sxs-lookup"><span data-stu-id="36ee4-111">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="36ee4-112">下列範例顯示 `GetColumn<T>` 擴充方法的使用方法：</span><span class="sxs-lookup"><span data-stu-id="36ee4-112">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="36ee4-113">[範例檔案](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt)：</span><span class="sxs-lookup"><span data-stu-id="36ee4-113">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>

<!-- markdownlint-disable MD010 -->
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="36ee4-114">我們的類別定義如下：</span><span class="sxs-lookup"><span data-stu-id="36ee4-114">Our class is defined as follows:</span></span>

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
