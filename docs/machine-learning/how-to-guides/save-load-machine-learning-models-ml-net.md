---
title: 儲存並載入定型的模型
description: 了解如何儲存並載入定型的模型
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3d4a51ceaf707d30c5072b91d7baf7fe02ef433
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065581"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="c425b-103">儲存並載入定型的模型</span><span class="sxs-lookup"><span data-stu-id="c425b-103">Save and load trained models</span></span>

<span data-ttu-id="c425b-104">了解如何在您的應用程式中儲存並載入已定型模型。</span><span class="sxs-lookup"><span data-stu-id="c425b-104">Learn how to save and load trained models in your application.</span></span> 

<span data-ttu-id="c425b-105">在整個模型建置流程中，模型會存留在記憶體中，並可在整個應用程式的生命週期內存取。</span><span class="sxs-lookup"><span data-stu-id="c425b-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="c425b-106">不過，一旦應用程式停止執行，如果模型未儲存在本機或遠端的某個位置，即無法再存取。</span><span class="sxs-lookup"><span data-stu-id="c425b-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="c425b-107">模型一般會用在其他應用程式定型後的某個點，用於推斷或重新定型。</span><span class="sxs-lookup"><span data-stu-id="c425b-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="c425b-108">因此，請務必儲存模型。</span><span class="sxs-lookup"><span data-stu-id="c425b-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="c425b-109">使用資料準備和模型定型管線時 (如以下詳加說明者)，使用本文件後續章節所述的步驟儲存並載入模型。</span><span class="sxs-lookup"><span data-stu-id="c425b-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="c425b-110">雖然這個範例使用線性迴歸模型，但相同的程序適用於其他 ML.NET 演算法。</span><span class="sxs-lookup"><span data-stu-id="c425b-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    }
};

// Create MLContext
MLContext mlContext = new MLContext();

// Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Define data preparation estimator
EstimatorChain<RegressionPredictionTransformer<LinearRegressionModelParameters>> pipelineEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .Append(mlContext.Regression.Trainers.Sdca());

// Train model
ITransformer trainedModel = pipelineEstimator.Fit(data);

// Save model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

<span data-ttu-id="c425b-111">因為大部分的模型和資料準備管線繼承自相同類別集，所以這些元件的儲存並載入方法簽章相同。</span><span class="sxs-lookup"><span data-stu-id="c425b-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="c425b-112">根據您的使用案例，您可將資料準備管線和模型結合為單一的 [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601)，這會輸出單一的 [`ITransformer`](xref:Microsoft.ML.ITransformer)，或分開它們為各自建立個別的 [`ITransformer`](xref:Microsoft.ML.ITransformer)。</span><span class="sxs-lookup"><span data-stu-id="c425b-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span> 

## <a name="save-a-model-locally"></a><span data-ttu-id="c425b-113">將模型儲存在本機</span><span class="sxs-lookup"><span data-stu-id="c425b-113">Save a model locally</span></span>

<span data-ttu-id="c425b-114">儲存模型時您需要兩個物件：</span><span class="sxs-lookup"><span data-stu-id="c425b-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="c425b-115">模型的 [`ITransformer`](xref:Microsoft.ML.ITransformer)。</span><span class="sxs-lookup"><span data-stu-id="c425b-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="c425b-116">[`ITransformer`](xref:Microsoft.ML.ITransformer) 之預期輸入的 [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema)。</span><span class="sxs-lookup"><span data-stu-id="c425b-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="c425b-117">定型模型後，請使用 [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) 方法，以輸入資料之 `DataViewSchema` 將已定型模型儲存至稱為 `model.zip` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="c425b-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span> 

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="c425b-118">載入儲存在本機的模型</span><span class="sxs-lookup"><span data-stu-id="c425b-118">Load a model stored locally</span></span>

<span data-ttu-id="c425b-119">儲存在本機的模型可以用在其他處理序或應用程式，例如 `ASP.NET Core` 和 `Serverless Web Applications`。</span><span class="sxs-lookup"><span data-stu-id="c425b-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="c425b-120">若要深入了解，請參閱[在 Web API 中使用 ML.NET](./serve-model-web-api-ml-net.md) 和[部署 ML.NET 無伺服器 Web 應用程式](./serve-model-serverless-azure-functions-ml-net.md)的操作說明文章。</span><span class="sxs-lookup"><span data-stu-id="c425b-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span> 

<span data-ttu-id="c425b-121">在個別的應用程式或處理序中，使用 [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) 方法和檔案路徑，將已定型模型放入您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c425b-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="c425b-122">載入儲存在遠端的模型</span><span class="sxs-lookup"><span data-stu-id="c425b-122">Load a model stored remotely</span></span>

<span data-ttu-id="c425b-123">若要將儲存在遠端位置的資料準備管線和模型載入應用程式，請使用 [`Stream`](xref:System.IO.Stream)，不要使用 [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) 方法中的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="c425b-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema and ITransformers
DataViewSchema modelSchema;
ITransformer trainedModel;

// Load data prep pipeline and trained model 
using (HttpClient client = new HttpClient())
{
    Stream modelFile = await client.GetStreamAsync("<YOUR-REMOTE-FILE-LOCATION>");

    trainedModel = mlContext.Model.Load(modelFile, out modelSchema);
}
```

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="c425b-124">使用不同的資料準備和模型管線</span><span class="sxs-lookup"><span data-stu-id="c425b-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="c425b-125">使用不同的資料準備和模型定型管線為選用項目。</span><span class="sxs-lookup"><span data-stu-id="c425b-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="c425b-126">管線分隔可讓您更輕鬆地檢查所學到的模型參數。</span><span class="sxs-lookup"><span data-stu-id="c425b-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="c425b-127">針對預測，儲存並載入包含資料準備和模型定型作業的單一管線更容易。</span><span class="sxs-lookup"><span data-stu-id="c425b-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="c425b-128">使用不同的資料準備管線和模型時，會套用和單一管線相同的程序；但不包括現在這兩種管線都需要同時儲存並載入。</span><span class="sxs-lookup"><span data-stu-id="c425b-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="c425b-129">指定不同的資料準備和模型定型管線：</span><span class="sxs-lookup"><span data-stu-id="c425b-129">Given separate data preparation and model training pipelines:</span></span>

```csharp
// Define data preparation estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data preparation transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Pre-process data using data prep operations
IDataView transformedData = dataPrepTransformer.Transform(data);

// Train regression model
RegressionPredictionTransformer<LinearRegressionModelParameters> trainedModel = sdcaEstimator.Fit(transformedData);
```

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="c425b-130">儲存資料準備管線和定型的模型</span><span class="sxs-lookup"><span data-stu-id="c425b-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="c425b-131">若要儲存資料準備管線和定型的模型，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="c425b-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="c425b-132">載入資料準備管線和定型的模型</span><span class="sxs-lookup"><span data-stu-id="c425b-132">Load data preparation pipeline and trained model</span></span> 

<span data-ttu-id="c425b-133">在不同的處理序或應用程式中，同時載入資料準備管線和定型的模型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c425b-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
