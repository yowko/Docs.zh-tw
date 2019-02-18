---
title: 使用文字檔 ML.NET 內容以外的資料，訓練機器學習模型
description: 探索如何使用 ML.NET，載入此檔案內容以外的訓練資料，供預測管線中的機器學習模型訓練之用。
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4ffbc69629aa9dc6cea5d33c704bc9c57a4a612c
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092016"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a>使用文字檔 ML.NET 內容以外的資料，訓練機器學習模型

使用 `TextLoader` 從檔案讀取訓練資料，是常見用來示範 ML.NET 的情境。
但在真實的訓練情境下，資料可能俯拾皆是，例如：

* 在 SQL 資料表中
* 從記錄檔案擷取
* 即時產生

使用[結構描述理解](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md)，將現有的 C# `IEnumerable` 放入 ML.NET 成為 `DataView`。

在此範例中，您將建置客戶變換預測模型，並從您的生產系統擷取下列特性：

* 客戶識別碼 (模型會忽略此項)
* 無論客戶變換與否 (目標 'label')
* ’demographic category’ (一個字串，例如 'young adult' 之類)
* 過去 5 天內的瀏覽量。

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

使用下列程式碼，將此資料載入 `DataView` 並訓練該模型：

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.Data.ReadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
