---
title: 從多個檔案載入資料，供機器學習處理之用 - ML.NET
description: 學習如何使用 ML.NET，從多個檔案載入資料，供機器學習模型建置、訓練及評分之用
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c9b34bd6bcbac62e9f9c33226f5d0feb41168392
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150728"
---
# <a name="load-data-from-multiple-files-for-machine-learning-processing---mlnet"></a><span data-ttu-id="dc3d9-103">從多個檔案載入資料，供機器學習處理之用 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="dc3d9-103">Load data from multiple files for machine learning processing - ML.NET</span></span>

<span data-ttu-id="dc3d9-104">使用 `TextLoader`，並為 `Read` 方法指定檔案陣列。</span><span class="sxs-lookup"><span data-stu-id="dc3d9-104">Use the `TextLoader`, and specify an array of files to the `Read` method.</span></span> <span data-ttu-id="dc3d9-105">所有檔案的結構描述必須相同 (相同數量及相同的資料行類型)：</span><span class="sxs-lookup"><span data-stu-id="dc3d9-105">The files must have the same schema (same number and type of columns):</span></span>

* [<span data-ttu-id="dc3d9-106">範例檔案 1</span><span class="sxs-lookup"><span data-stu-id="dc3d9-106">Example file1</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.train)
* [<span data-ttu-id="dc3d9-107">範例檔案 2</span><span class="sxs-lookup"><span data-stu-id="dc3d9-107">Example file2</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.test)

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // A boolean column depicting the 'label'.
        new TextLoader.Column("IsOver50k", DataKind.BL, 0),
        // Three text columns.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
        new TextLoader.Column("Education", DataKind.TX, 2),
        new TextLoader.Column("MaritalStatus", DataKind.TX, 3)
    },
    // First line of the file is a header, not a data row.
    HasHeader = true
});

var data = reader.Read(exampleFile1, exampleFile2);
```