---
title: 使用定型的模型預測
description: 了解使用定型的模型預測
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: f764d2147ec56f8dcc38f96d566ac746cf205650
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799130"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="27c67-103">使用定型的模型預測</span><span class="sxs-lookup"><span data-stu-id="27c67-103">Make predictions with a trained model</span></span>

<span data-ttu-id="27c67-104">了解如何使用定型的模型建立預測</span><span class="sxs-lookup"><span data-stu-id="27c67-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="27c67-105">建立資料模型</span><span class="sxs-lookup"><span data-stu-id="27c67-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="27c67-106">輸入資料</span><span class="sxs-lookup"><span data-stu-id="27c67-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="27c67-107">輸出資料</span><span class="sxs-lookup"><span data-stu-id="27c67-107">Output data</span></span>

<span data-ttu-id="27c67-108">例如 `Features` 和 `Label` 輸入資料行名稱，ML.NET 有模型產生的預測值資料行預設名稱。</span><span class="sxs-lookup"><span data-stu-id="27c67-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="27c67-109">依工作不同，名稱可能不同。</span><span class="sxs-lookup"><span data-stu-id="27c67-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="27c67-110">因為用於此範例的演算法是線性迴歸演算法，所以輸出資料行預設名稱是 `Score`，由 `PredictedPrice` 屬性的 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="27c67-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="27c67-111">設定預測管線</span><span class="sxs-lookup"><span data-stu-id="27c67-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="27c67-112">無論是建立單一或批次預測，預測管線都需要載入到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="27c67-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="27c67-113">此管線包含資料前置處理轉換以及定型的模型。</span><span class="sxs-lookup"><span data-stu-id="27c67-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="27c67-114">下列程式碼片段會從名為 `model.zip` 的檔案載入預測管線。</span><span class="sxs-lookup"><span data-stu-id="27c67-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="27c67-115">單一預測</span><span class="sxs-lookup"><span data-stu-id="27c67-115">Single prediction</span></span>

<span data-ttu-id="27c67-116">若要建立單一預測，請使用載入的預測管線建立 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="27c67-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="27c67-117">然後，使用 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) 方法，並傳入您的輸入資料作為參數。</span><span class="sxs-lookup"><span data-stu-id="27c67-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="27c67-118">請注意，使用 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) 方法不要求輸入成為 [`IDataView`](xref:Microsoft.ML.IDataView))。</span><span class="sxs-lookup"><span data-stu-id="27c67-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="27c67-119">這是因為它方便內化輸入資料類型操作，使您可以傳入輸入資料類型的物件。</span><span class="sxs-lookup"><span data-stu-id="27c67-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="27c67-120">此外，因為 `CurrentPrice` 是您想要使用新資料嘗試預測的目標或標籤，所以假設它目前沒有任何值。</span><span class="sxs-lookup"><span data-stu-id="27c67-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="27c67-121">如果您存取 `prediction` 物件的 `Score` 屬性，您應該取得類似 `150079` 的值。</span><span class="sxs-lookup"><span data-stu-id="27c67-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="27c67-122">多個預測</span><span class="sxs-lookup"><span data-stu-id="27c67-122">Multiple predictions</span></span>

<span data-ttu-id="27c67-123">指定下列資料，將它載入 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="27c67-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="27c67-124">在此案例中，[`IDataView`](xref:Microsoft.ML.IDataView) 的名稱為 `inputData`。</span><span class="sxs-lookup"><span data-stu-id="27c67-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="27c67-125">因為 `CurrentPrice` 是您想要使用新資料嘗試預測的目標或標籤，所以假設它目前沒有任何值。</span><span class="sxs-lookup"><span data-stu-id="27c67-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="27c67-126">然後，使用 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 方法套用資料轉換並產生預測。</span><span class="sxs-lookup"><span data-stu-id="27c67-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="27c67-127">使用 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) 方法檢查預測的值。</span><span class="sxs-lookup"><span data-stu-id="27c67-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="27c67-128">分數資料行中的預測值看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="27c67-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="27c67-129">觀測</span><span class="sxs-lookup"><span data-stu-id="27c67-129">Observation</span></span> | <span data-ttu-id="27c67-130">預測</span><span class="sxs-lookup"><span data-stu-id="27c67-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="27c67-131">1</span><span class="sxs-lookup"><span data-stu-id="27c67-131">1</span></span> | <span data-ttu-id="27c67-132">144638.2</span><span class="sxs-lookup"><span data-stu-id="27c67-132">144638.2</span></span> |
| <span data-ttu-id="27c67-133">2</span><span class="sxs-lookup"><span data-stu-id="27c67-133">2</span></span> | <span data-ttu-id="27c67-134">150079.4</span><span class="sxs-lookup"><span data-stu-id="27c67-134">150079.4</span></span> |
| <span data-ttu-id="27c67-135">3</span><span class="sxs-lookup"><span data-stu-id="27c67-135">3</span></span> | <span data-ttu-id="27c67-136">107789.8</span><span class="sxs-lookup"><span data-stu-id="27c67-136">107789.8</span></span> |
