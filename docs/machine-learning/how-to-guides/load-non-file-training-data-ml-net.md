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
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="0759f-103">使用文字檔 ML.NET 內容以外的資料，訓練機器學習模型</span><span class="sxs-lookup"><span data-stu-id="0759f-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

<span data-ttu-id="0759f-104">使用 `TextLoader` 從檔案讀取訓練資料，是常見用來示範 ML.NET 的情境。</span><span class="sxs-lookup"><span data-stu-id="0759f-104">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="0759f-105">但在真實的訓練情境下，資料可能俯拾皆是，例如：</span><span class="sxs-lookup"><span data-stu-id="0759f-105">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="0759f-106">在 SQL 資料表中</span><span class="sxs-lookup"><span data-stu-id="0759f-106">in SQL tables</span></span>
* <span data-ttu-id="0759f-107">從記錄檔案擷取</span><span class="sxs-lookup"><span data-stu-id="0759f-107">extracted from log files</span></span>
* <span data-ttu-id="0759f-108">即時產生</span><span class="sxs-lookup"><span data-stu-id="0759f-108">generated on the fly</span></span>

<span data-ttu-id="0759f-109">使用[結構描述理解](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md)，將現有的 C# `IEnumerable` 放入 ML.NET 成為 `DataView`。</span><span class="sxs-lookup"><span data-stu-id="0759f-109">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="0759f-110">在此範例中，您將建置客戶變換預測模型，並從您的生產系統擷取下列特性：</span><span class="sxs-lookup"><span data-stu-id="0759f-110">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="0759f-111">客戶識別碼 (模型會忽略此項)</span><span class="sxs-lookup"><span data-stu-id="0759f-111">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="0759f-112">無論客戶變換與否 (目標 'label')</span><span class="sxs-lookup"><span data-stu-id="0759f-112">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="0759f-113">’demographic category’ (一個字串，例如 'young adult' 之類)</span><span class="sxs-lookup"><span data-stu-id="0759f-113">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="0759f-114">過去 5 天內的瀏覽量。</span><span class="sxs-lookup"><span data-stu-id="0759f-114">The number of visits from the last 5 days.</span></span>

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

<span data-ttu-id="0759f-115">使用下列程式碼，將此資料載入 `DataView` 並訓練該模型：</span><span class="sxs-lookup"><span data-stu-id="0759f-115">Load this data into the `DataView` and train the model, using the following code:</span></span>

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
