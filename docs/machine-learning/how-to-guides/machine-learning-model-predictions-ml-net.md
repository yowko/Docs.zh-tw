---
title: 使用定型的模型預測
description: 了解使用定型的模型預測
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2e8263db289bed50e7437b695134458b8c07e0e5
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679569"
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

因為此範例中使用的演算法是線性回歸演算法，所以輸出資料行的預設名稱是 `Score` 由屬性（attribute）上的屬性（property）所定義 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) `PredictedPrice` 。

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

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

若要進行單一預測，請 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 使用載入的預測管線來建立。

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

然後，使用 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) 方法，並傳入您的輸入資料作為參數。 請注意，使用此 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) 方法不需要 [`IDataView`](xref:Microsoft.ML.IDataView)) 輸入。 這是因為它方便內化輸入資料類型操作，使您可以傳入輸入資料類型的物件。 此外，因為 `CurrentPrice` 是您想要使用新資料嘗試預測的目標或標籤，所以假設它目前沒有任何值。

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

## <a name="multiple-predictions"></a>多個預測

假設有下列資料，請將它載入至 [`IDataView`](xref:Microsoft.ML.IDataView) 。 在此情況下，的名稱 [`IDataView`](xref:Microsoft.ML.IDataView) 為 `inputData` 。 因為 `CurrentPrice` 是您想要使用新資料嘗試預測的目標或標籤，所以假設它目前沒有任何值。

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
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

然後，使用 [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) 方法來套用資料轉換和產生預測。

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

使用方法檢查預測的值 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) 。

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
