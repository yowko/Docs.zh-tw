---
title: 使用定型的模型預測
description: 了解使用定型的模型預測
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: dac3b3bfa68776975a2e5e762f46db16e39d61fb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065601"
---
# <a name="make-predictions-with-a-trained-model"></a>使用定型的模型預測

了解如何使用定型的模型建立預測

## <a name="create-data-models"></a>建立資料模型

### <a name="input-data"></a>輸入資料

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="output-data"></a>輸出資料

例如 `Features` 和 `Label` 輸入資料行名稱，ML.NET 有模型產生的預測值資料行預設名稱。 依工作不同，名稱可能不同。

因為用於此範例的演算法是線性迴歸演算法，所以輸出資料行預設名稱是 `Score`，由 `PredictedPrice` 屬性的 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性所定義。

```csharp
class HousingPrediction : HousingData
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

繼承自 `HousingData` 的 `HousingPrediction` 資料模型，讓視覺化原始輸入資料以及模型產生的輸出變得容易。  

## <a name="set-up-a-prediction-pipeline"></a>設定預測管線

無論是建立單一或批次預測，預測管線都需要載入到應用程式中。 此管線包含資料前置處理轉換以及定型的模型。 下列程式碼片段會從名為 `model.zip` 的檔案載入預測管線。

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>單一預測

若要建立單一預測，請使用載入的預測管線建立 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

然後，使用 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) 方法，並傳入您的輸入資料作為參數。 請注意，使用 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) 方法不要求輸入成為 [`IDataView`](xref:Microsoft.ML.IDataView))。 這是因為它方便內化輸入資料類型操作，使您可以傳入輸入資料類型的物件。 此外，因為 `CurrentPrice` 是您想要使用新資料嘗試預測的目標或標籤，所以假設它目前沒有任何值。

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

如果您存取 `prediction` 物件的 `Score` 屬性，您應該取得類似 `150079` 的值。

## <a name="batch-prediction"></a>批次預測

指定下列資料，將它載入 [`IDataView`](xref:Microsoft.ML.IDataView)。 因為 `CurrentPrice` 是您想要使用新資料嘗試預測的目標或標籤，所以假設它目前沒有任何值。

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

然後，使用 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 方法套用資料轉換並產生預測。

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

使用 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) 方法檢查預測的值。

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

分數資料行中的預測值看起來應該如下所示：

| 觀測 | 預測 |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
