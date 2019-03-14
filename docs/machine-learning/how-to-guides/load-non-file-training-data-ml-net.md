---
title: 使用文字檔 ML.NET 內容以外的資料，訓練機器學習模型
description: 探索如何使用 ML.NET，載入此檔案內容以外的訓練資料，供預測管線中的機器學習模型訓練之用。
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 27b327a63cb55b7fce0f4ff7facd3ee7c4a1c85c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678609"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="b52b1-103">使用文字檔 ML.NET 內容以外的資料，訓練機器學習模型</span><span class="sxs-lookup"><span data-stu-id="b52b1-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="b52b1-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="b52b1-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b52b1-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="b52b1-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b52b1-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="b52b1-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="b52b1-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="b52b1-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="b52b1-108">使用 `TextLoader` 從檔案讀取訓練資料，是常見用來示範 ML.NET 的情境。</span><span class="sxs-lookup"><span data-stu-id="b52b1-108">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="b52b1-109">但在真實的訓練情境下，資料可能俯拾皆是，例如：</span><span class="sxs-lookup"><span data-stu-id="b52b1-109">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="b52b1-110">在 SQL 資料表中</span><span class="sxs-lookup"><span data-stu-id="b52b1-110">in SQL tables</span></span>
* <span data-ttu-id="b52b1-111">從記錄檔案擷取</span><span class="sxs-lookup"><span data-stu-id="b52b1-111">extracted from log files</span></span>
* <span data-ttu-id="b52b1-112">即時產生</span><span class="sxs-lookup"><span data-stu-id="b52b1-112">generated on the fly</span></span>

<span data-ttu-id="b52b1-113">使用[結構描述理解](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md)，將現有的 C# `IEnumerable` 放入 ML.NET 成為 `DataView`。</span><span class="sxs-lookup"><span data-stu-id="b52b1-113">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="b52b1-114">在此範例中，您將建置客戶變換預測模型，並從您的生產系統擷取下列特性：</span><span class="sxs-lookup"><span data-stu-id="b52b1-114">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="b52b1-115">客戶識別碼 (模型會忽略此項)</span><span class="sxs-lookup"><span data-stu-id="b52b1-115">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="b52b1-116">無論客戶變換與否 (目標 'label')</span><span class="sxs-lookup"><span data-stu-id="b52b1-116">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="b52b1-117">’demographic category’ (一個字串，例如 'young adult' 之類)</span><span class="sxs-lookup"><span data-stu-id="b52b1-117">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="b52b1-118">過去 5 天內的瀏覽量。</span><span class="sxs-lookup"><span data-stu-id="b52b1-118">The number of visits from the last 5 days.</span></span>

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

<span data-ttu-id="b52b1-119">使用下列程式碼，將此資料載入 `DataView` 並訓練該模型：</span><span class="sxs-lookup"><span data-stu-id="b52b1-119">Load this data into the `DataView` and train the model, using the following code:</span></span>

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
