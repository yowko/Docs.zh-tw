---
title: 使用 PredictionFunction 一次進行一個預測 - ML.NET
description: 了解如何使用 ML.NET PredictionFunction 一次進行一個預測
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 9e34c1357e5ac241abd628289cd694bcd6b9cbb1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131662"
---
# <a name="use-the-predictionfunction-to-make-one-prediction-at-a-time---mlnet"></a><span data-ttu-id="14b6b-103">使用 PredictionFunction 一次進行一個預測 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="14b6b-103">Use the PredictionFunction to make one prediction at a time - ML.NET</span></span> 

<span data-ttu-id="14b6b-104">由於任何 ML.NET 模型都是轉換器，因此您會使用 `model.Transform`，將模型套用至 `DataView` 以進行預測。</span><span class="sxs-lookup"><span data-stu-id="14b6b-104">Since any ML.NET model is a transformer, you use `model.Transform` to apply the model to the `DataView` to make predictions.</span></span> 

<span data-ttu-id="14b6b-105">不過，更典型的案例是，您沒有要預測的「資料集」，而是一次接收到一個範例。</span><span class="sxs-lookup"><span data-stu-id="14b6b-105">A more typical case, though, is when there is no 'dataset' that you want to predict on, but instead you receive one example at a time.</span></span> <span data-ttu-id="14b6b-106">例如，您將模型作為 ASP.NET 網站的一部分來執行，且需要對傳入的 HTTP 要求進行預測。</span><span class="sxs-lookup"><span data-stu-id="14b6b-106">For instance, you run the model as part of your ASP.NET website, and need to make a prediction for an incoming HTTP request.</span></span>

<span data-ttu-id="14b6b-107">`PredictionFunction` 透過預測管線一次執行一個範例。</span><span class="sxs-lookup"><span data-stu-id="14b6b-107">The `PredictionFunction` runs one example at a time through the prediction pipeline.</span></span>

<span data-ttu-id="14b6b-108">使用預先建置的 Iris 預測資料集模型的完整範例如下：</span><span class="sxs-lookup"><span data-stu-id="14b6b-108">Here is the full example using a prebuilt Iris prediction dataset model:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        new TextLoader.Column("SepalLength", DataKind.R4, 0),
        new TextLoader.Column("SepalWidth", DataKind.R4, 1),
        new TextLoader.Column("PetalLength", DataKind.R4, 2),
        new TextLoader.Column("PetalWidth", DataKind.R4, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    // Default separator is tab, but the dataset has comma.
    Separator = ","
});

// Retrieve the training data.
var trainData = reader.Read(irisDataPath);

// Build the training pipeline.
var pipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Categorical.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent())
    // Apply the inverse conversion from 'PredictedLabel' column back to string value.
    .Append(mlContext.Transforms.Conversion.MapKeyToValue(("PredictedLabel", "Data")));

// Train the model.
var model = pipeline.Fit(trainData);
```

<span data-ttu-id="14b6b-109">若要將[結構描述理解](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) \(英文\) 用於預測，請定義一組類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="14b6b-109">To use [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) for prediction, define a pair of classes like the following:</span></span>

```csharp
private class IrisInput
{
    // Unfortunately, we still need the dummy 'Label' column to be present.
    [ColumnName("Label")]
    public string IgnoredLabel { get; set; }
    public float SepalLength { get; set; }
    public float SepalWidth { get; set; }
    public float PetalLength { get; set; }
    public float PetalWidth { get; set; }
}

private class IrisPrediction
{
    [ColumnName("Data")]
    public string PredictedClass { get; set; }
}
```

<span data-ttu-id="14b6b-110">預測程式碼現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="14b6b-110">The prediction code now looks as follows:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Use the model for one-time prediction.
// Make the prediction function object. Note that, on average, this call takes around 200x longer
// than one prediction, so you might want to cache and reuse the prediction function, instead of
// creating one per prediction.
var predictionFunc = model.MakePredictionFunction<IrisInput, IrisPrediction>(mlContext);

// Obtain the prediction. Remember that 'Predict' is not reentrant. If you want to use multiple threads
// for simultaneous prediction, make sure each thread is using its own PredictionFunction.
var prediction = predictionFunc.Predict(new IrisInput
{
    SepalLength = 4.1f,
    SepalWidth = 0.1f,
    PetalLength = 3.2f,
    PetalWidth = 1.4f
});
```
