---
title: 重新定型模型
description: 了解如何在 ML.NET 中重新定型模型
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 1628d0669d8a9e677ff39b5869d3802d89d96410
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397707"
---
# <a name="re-train-a-model"></a><span data-ttu-id="801b7-103">重新定型模型</span><span class="sxs-lookup"><span data-stu-id="801b7-103">Re-train a model</span></span>

<span data-ttu-id="801b7-104">了解如何在 ML.NET 中重新定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="801b7-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="801b7-105">世界和其周圍的資料都會不斷地改變。</span><span class="sxs-lookup"><span data-stu-id="801b7-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="801b7-106">因此，模型也需要變更和更新。</span><span class="sxs-lookup"><span data-stu-id="801b7-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="801b7-107">ML.NET 提供使用學習模型的參數作為起點來重新定型模行的功能，以繼續根據先前的經驗進行建置，而非每次都從頭開始。</span><span class="sxs-lookup"><span data-stu-id="801b7-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>  

<span data-ttu-id="801b7-108">下列演算法在 ML.NET 中可重新定型：</span><span class="sxs-lookup"><span data-stu-id="801b7-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="801b7-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="801b7-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="801b7-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="801b7-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="801b7-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="801b7-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="801b7-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="801b7-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="801b7-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="801b7-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="801b7-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="801b7-119">載入預先定型的模型</span><span class="sxs-lookup"><span data-stu-id="801b7-119">Load pre-trained model</span></span>

<span data-ttu-id="801b7-120">首先，將預先定型的模型載入應用程式。</span><span class="sxs-lookup"><span data-stu-id="801b7-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="801b7-121">若要深入了解載入定型管線和模型，請參閱相關的[操作說明文章](./consuming-model-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="801b7-121">To learn more about loading training pipelines and models, see the related [how-to article](./consuming-model-ml-net.md).</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="801b7-122">擷取預先定型的模型參數</span><span class="sxs-lookup"><span data-stu-id="801b7-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="801b7-123">載入模型後，透過存取預先定型模型之 [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) 屬性來擷取學習模型的參數。</span><span class="sxs-lookup"><span data-stu-id="801b7-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="801b7-124">預先定型的模型原先是使用線性迴歸模型 [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) 所定型，該模型會建立一個 [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601)，其會輸出 [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)。</span><span class="sxs-lookup"><span data-stu-id="801b7-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="801b7-125">這些線性迴歸模型參數包含學習到的偏差和權重，或是模型的相關係數。</span><span class="sxs-lookup"><span data-stu-id="801b7-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="801b7-126">這些值將會用來作為新重新定型模型的起點。</span><span class="sxs-lookup"><span data-stu-id="801b7-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="801b7-127">重新定型模型</span><span class="sxs-lookup"><span data-stu-id="801b7-127">Re-train model</span></span>

<span data-ttu-id="801b7-128">重新定型模型的流程與定型模型的流程沒什麼不同。</span><span class="sxs-lookup"><span data-stu-id="801b7-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="801b7-129">唯一的差別在於，除了資料外，[`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) 方法也會接受輸入原始定型模型的參數，並用它們作為重新定型流程的起點。</span><span class="sxs-lookup"><span data-stu-id="801b7-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>  

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel = 
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a><span data-ttu-id="801b7-130">比較模型參數</span><span class="sxs-lookup"><span data-stu-id="801b7-130">Compare model parameters</span></span>

<span data-ttu-id="801b7-131">如何了解實際上已發生重新定型？</span><span class="sxs-lookup"><span data-stu-id="801b7-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="801b7-132">其中一種方式是比較重新定型模型的參數是否和原始模型參數不同。</span><span class="sxs-lookup"><span data-stu-id="801b7-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="801b7-133">以下程式碼範例會比較原始及重新定型模型的權重，並將它們輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="801b7-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs = 
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

<span data-ttu-id="801b7-134">下表顯示輸出可能呈現的結果。</span><span class="sxs-lookup"><span data-stu-id="801b7-134">The table below shows what the output might look like.</span></span> 

|<span data-ttu-id="801b7-135">原始</span><span class="sxs-lookup"><span data-stu-id="801b7-135">Original</span></span> | <span data-ttu-id="801b7-136">重新定型</span><span class="sxs-lookup"><span data-stu-id="801b7-136">Retrained</span></span> | <span data-ttu-id="801b7-137">差異</span><span class="sxs-lookup"><span data-stu-id="801b7-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="801b7-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="801b7-138">33039.86</span></span> | <span data-ttu-id="801b7-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="801b7-139">56293.76</span></span> | <span data-ttu-id="801b7-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="801b7-140">-23253.9</span></span> |
| <span data-ttu-id="801b7-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="801b7-141">29099.14</span></span> | <span data-ttu-id="801b7-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="801b7-142">49586.03</span></span> | <span data-ttu-id="801b7-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="801b7-143">-20486.89</span></span> |
| <span data-ttu-id="801b7-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="801b7-144">28938.38</span></span> | <span data-ttu-id="801b7-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="801b7-145">48609.23</span></span> | <span data-ttu-id="801b7-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="801b7-146">-19670.85</span></span> |
| <span data-ttu-id="801b7-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="801b7-147">30484.02</span></span> | <span data-ttu-id="801b7-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="801b7-148">53745.43</span></span> | <span data-ttu-id="801b7-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="801b7-149">-23261.41</span></span> |
