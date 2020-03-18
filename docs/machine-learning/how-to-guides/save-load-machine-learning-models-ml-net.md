---
title: 儲存並載入定型的模型
description: 了解如何儲存並載入定型的模型
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977000"
---
# <a name="save-and-load-trained-models"></a>儲存並載入定型的模型

了解如何在您的應用程式中儲存並載入已定型模型。

在整個模型建置流程中，模型會存留在記憶體中，並可在整個應用程式的生命週期內存取。 不過，一旦應用程式停止執行，如果模型未儲存在本機或遠端的某個位置，即無法再存取。 模型一般會用在其他應用程式定型後的某個點，用於推斷或重新定型。 因此，請務必儲存模型。 使用資料準備和模型定型管線時 (如以下詳加說明者)，使用本文件後續章節所述的步驟儲存並載入模型。 雖然這個範例使用線性迴歸模型，但相同的程序適用於其他 ML.NET 演算法。

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f, 125000f, 122000f },
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

因為大部分的模型和資料準備管線繼承自相同類別集，所以這些元件的儲存並載入方法簽章相同。 根據您的用例，您可以將資料準備管道和模型合併為單個，[`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601)這將輸出單個管道[`ITransformer`](xref:Microsoft.ML.ITransformer)或將它們分開，從而為每個管道創建單獨的[`ITransformer`](xref:Microsoft.ML.ITransformer)資料準備管道和模型。

## <a name="save-a-model-locally"></a>將模型儲存在本機

儲存模型時您需要兩個物件：

1. 模型[`ITransformer`](xref:Microsoft.ML.ITransformer)的 。
2. [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema)的預期輸入的 的[`ITransformer`](xref:Microsoft.ML.ITransformer)。

訓練模型後，使用 方法[`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*)將訓練的模型保存到使用`model.zip``DataViewSchema`輸入資料調用的檔。

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>載入儲存在本機的模型

儲存在本機的模型可以用在其他處理序或應用程式，例如 `ASP.NET Core` 和 `Serverless Web Applications`。 若要深入了解，請參閱[在 Web API 中使用 ML.NET](./serve-model-web-api-ml-net.md) 和[部署 ML.NET 無伺服器 Web 應用程式](./serve-model-serverless-azure-functions-ml-net.md)的操作說明文章。

在單獨的應用程式或進程中，[`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*)將 方法與檔路徑一起使用，將訓練的模型引入應用程式。

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>載入儲存在遠端的模型

要將存儲在遠端位置的資料準備管道和模型載入到應用程式中，請使用[`Stream`](xref:System.IO.Stream)[`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*)方法中的檔路徑而不是檔路徑。

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>使用不同的資料準備和模型管線

> [!NOTE]
> 使用不同的資料準備和模型定型管線為選用項目。 管線分隔可讓您更輕鬆地檢查所學到的模型參數。 針對預測，儲存並載入包含資料準備和模型定型作業的單一管線更容易。

使用不同的資料準備管線和模型時，會套用和單一管線相同的程序；但不包括現在這兩種管線都需要同時儲存並載入。

指定不同的資料準備和模型定型管線：

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>儲存資料準備管線和定型的模型

若要儲存資料準備管線和定型的模型，請使用下列命令：

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>載入資料準備管線和定型的模型

在不同的處理序或應用程式中，同時載入資料準備管線和定型的模型，如下所示：

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
