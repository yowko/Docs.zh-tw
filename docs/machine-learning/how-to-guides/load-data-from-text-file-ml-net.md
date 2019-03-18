---
title: 從文字檔載入資料以進行機器學習處理 - ML.NET
description: 探索如何使用 ML.NET，從文字檔載入資料，供機器學習模型建置、訓練及評分之用
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 14b1f8c99da6f1b8da436d9afef5b2ac8d36ecae
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843365"
---
# <a name="load-data-from-a-text-file-for-machine-learning-processing---mlnet"></a><span data-ttu-id="5d98c-103">從文字檔載入資料以進行機器學習處理 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="5d98c-103">Load data from a text file for machine learning processing - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="5d98c-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="5d98c-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="5d98c-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="5d98c-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="5d98c-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="5d98c-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="5d98c-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="5d98c-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="5d98c-108">`TextLoader` 是用來從文字檔載入資料。</span><span class="sxs-lookup"><span data-stu-id="5d98c-108">`TextLoader` is used to load data from text files.</span></span> <span data-ttu-id="5d98c-109">您需要指定資料行、其類型，以及它們在文字檔中的位置。</span><span class="sxs-lookup"><span data-stu-id="5d98c-109">You need to specify the data columns, their types, and their location in the text file.</span></span>

<span data-ttu-id="5d98c-110">請注意，它可接受讀取檔案的部分資料行，或是多次讀取相同的資料行。</span><span class="sxs-lookup"><span data-stu-id="5d98c-110">Note that it's perfectly acceptable to read some columns of a file, or read the same column multiple times.</span></span>

<span data-ttu-id="5d98c-111">[範例檔案](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt)：</span><span class="sxs-lookup"><span data-stu-id="5d98c-111">[Example file](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span></span>

<!-- markdownlint-disable MD010 -->
```console
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="5d98c-112">從文字檔載入資料：</span><span class="sxs-lookup"><span data-stu-id="5d98c-112">To load the data from a text file:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // A boolean column depicting the 'target label'.
        new TextLoader.Column("IsOver50k",DataKind.BL,0),
        // Three text columns.
        new TextLoader.Column("WorkClass",DataKind.TX,1),
        new TextLoader.Column("Education",DataKind.TX,2),
        new TextLoader.Column("MaritalStatus",DataKind.TX,3)
    },
    hasHeader: true
);

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```
