---
title: 在 ML.NET 中針對模型可解釋性使用一般化累加模型與圖形函式
description: 在 ML.NET 中針對模型可解釋性使用一般化累加模型與圖形函式
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: c6f30a8cc5c07d97c62ded065f1e18a4f0523617
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093108"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="2a410-103">在 ML.NET 中針對模型可解釋性使用一般化累加模型與圖形函式</span><span class="sxs-lookup"><span data-stu-id="2a410-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

<span data-ttu-id="2a410-104">在建立機器學習模型時，模型通常不足以直接用來進行預測。</span><span class="sxs-lookup"><span data-stu-id="2a410-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="2a410-105">一般來說，機器學習開發人員、決策者，以及受該模型影響的人員需要了解機器學習模型如何做出決策，以及哪些特徵會影響其效能。</span><span class="sxs-lookup"><span data-stu-id="2a410-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="2a410-106">**一般化加法模型 (GAM)** 用於 Microsoft 內部的模型可解釋性，以協助機器學習開發人員建立可由其他人輕鬆解譯的高容量模型。</span><span class="sxs-lookup"><span data-stu-id="2a410-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="2a410-107">GAM 是屬於線性模型的一種**可解譯模型**類別，此項在非線性函數中稱為「形狀函數」的單一變數。</span><span class="sxs-lookup"><span data-stu-id="2a410-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="2a410-108">線性模型可輕鬆地解譯，但因為特徵的模型學習函式取代了單一加權，它們能夠建立比單一線性模型更複雜的關聯性。</span><span class="sxs-lookup"><span data-stu-id="2a410-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="2a410-109">產生的 GAM 預測工具具有截距項，代表訓練集上的平均預測，以及代表與平均預測偏差的形狀函數。</span><span class="sxs-lookup"><span data-stu-id="2a410-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="2a410-110">形狀函數可以直接檢查，來查看針對不同特徵值的模型回應，並視覺化如程式碼範例結尾所建立的下列圖表。</span><span class="sxs-lookup"><span data-stu-id="2a410-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="2a410-111">ML.NET 中的 GAM 訓練工具使用淺層梯度提升決策樹 (例如樹墩) 來學習無母數形狀函數，並且以 Lou、Caruana 和 Gehrke 的[適用於分類和迴歸的可理解模型](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) \(英文\) 中所述的方法為基礎。</span><span class="sxs-lookup"><span data-stu-id="2a410-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the column names from the training set
var columnNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = columnNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetBinEffects(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![一般化加法模型形狀函數圖表](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="2a410-113">如需如何定型 GAM 模型和檢查與解譯結果的範例，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="2a410-113">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
