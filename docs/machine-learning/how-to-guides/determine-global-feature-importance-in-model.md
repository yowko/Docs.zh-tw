---
title: 在 ML.NET 中使用 Permutation Feature Importance 判斷模型的特徵重要性
description: 在 ML.NET 中使用 Permutation Feature Importance 了解模型的功能重要性
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b0457bc07168579403e5a00383864c5612e1d17f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675546"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a><span data-ttu-id="58824-103">在 ML.NET 中使用 Permutation Feature Importance 判斷模型的特徵重要性</span><span class="sxs-lookup"><span data-stu-id="58824-103">Determine the feature importance of models with Permutation Feature Importance in ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="58824-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="58824-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="58824-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="58824-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="58824-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="58824-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="58824-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="58824-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="58824-108">在建立機器學習模型時，模型通常不足以直接用來進行預測。</span><span class="sxs-lookup"><span data-stu-id="58824-108">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="58824-109">一般來說，機器學習開發人員、決策者，以及受該模型影響的人員需要了解機器學習模型如何做出決策，以及哪些特徵會影響其效能。</span><span class="sxs-lookup"><span data-stu-id="58824-109">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="58824-110">`Permutation Feature Importance` (PFI) 是在 Microsoft 內部使用的模型可解釋性工具，可協助機器學習開發人員更了解模型的特徵重要性。</span><span class="sxs-lookup"><span data-stu-id="58824-110">`Permutation Feature Importance` (PFI) is a model explainability tool that is used internally at Microsoft to help machine learning developers better understand the feature importance of models.</span></span>

<span data-ttu-id="58824-111">PFI 是在定型機器學習中用來判斷**全域特徵重要性**的技術，此技術是由 Breiman 的[《隨機樹系》論文第 10 小節](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) \(英文\) 啟發。</span><span class="sxs-lookup"><span data-stu-id="58824-111">PFI is a technique to determine **global feature importance** in a trained machine learning model, motivated by Breiman in the ["Random Forests" paper, section 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span></span> <span data-ttu-id="58824-112">PFI 測量特徵重要性所依據的問題是「如果將某個特徵的值設定為隨機\* 值，對模型會有何影響？」。</span><span class="sxs-lookup"><span data-stu-id="58824-112">PFI measures feature importance by asking the question, "What would the effect on the model be if the values for a feature were set to a random\* value?".</span></span> <span data-ttu-id="58824-113">PFI 方法的優點是它與模型無關 (可用於任何能評估的模型)，而且它能使用任何資料集 (不僅是定型集合) 來計算特徵重要性。</span><span class="sxs-lookup"><span data-stu-id="58824-113">The advantage of the PFI method is that it is model agnostic — it works with any model that can be evaluated — and it can use any dataset, not just the training set, to compute feature importance.</span></span> <span data-ttu-id="58824-114">您可以按照此方法來產生如下的特徵重要性圖表：</span><span class="sxs-lookup"><span data-stu-id="58824-114">You can use PFI like so to produce feature importances like this graph:</span></span>

![Permutation Feature Importance 圖表](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model.LastTransformer, model.Transform(data), "MedianHomeValue");

// Get the feature names from the training set
var featureNames =
    data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Write out the feature names and their importance to the model's Mean R-squared value
for (int i = 0; i < featureNames.Length;i++)
{
    Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].RSquared.Mean:G4}");
}
```

<span data-ttu-id="58824-116">如需使用 PFI 來分析模型特徵重要性的範例，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance)。</span><span class="sxs-lookup"><span data-stu-id="58824-116">For a sample using PFI to analyze the feature importance of a model, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).</span></span>

<span data-ttu-id="58824-117">\* 並非完全隨機，而是在整組範例中排列。</span><span class="sxs-lookup"><span data-stu-id="58824-117">/\* Well, not random exactly, but permuted across the set of examples.</span></span>
