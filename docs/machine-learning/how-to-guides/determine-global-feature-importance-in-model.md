---
title: 在 ML.NET 中使用 Permutation Feature Importance 判斷模型的特徵重要性
description: 在 ML.NET 中使用 Permutation Feature Importance 了解模型的功能重要性
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 4b93e085dbb99e7f6f5a0a839b863aad1c69c7ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156566"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a>在 ML.NET 中使用 Permutation Feature Importance 判斷模型的特徵重要性

在建立機器學習模型時，模型通常不足以直接用來進行預測。 一般來說，機器學習開發人員、決策者，以及受該模型影響的人員需要了解機器學習模型如何做出決策，以及哪些特徵會影響其效能。 `Permutation Feature Importance` (PFI) 是在 Microsoft 內部使用的模型可解釋性工具，可協助機器學習開發人員更了解模型的特徵重要性。

PFI 是在定型機器學習中用來判斷**全域特徵重要性**的技術，此技術是由 Breiman 的[《隨機樹系》論文第 10 小節](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) \(英文\) 啟發。 PFI 測量特徵重要性所依據的問題是「如果將某個特徵的值設定為隨機\* 值，對模型會有何影響？」。 PFI 方法的優點是它與模型無關 (可用於任何能評估的模型)，而且它能使用任何資料集 (不僅是定型集合) 來計算特徵重要性。 您可以按照此方法來產生如下的特徵重要性圖表：

![Permutation Feature Importance 圖表](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model, data);
 
// Get the feature names from the training set
var featureNames = data.Schema.GetColumns()
                .Select(tuple => tuple.column.Name) // Get the column names
                .Where(name => name != labelName) // Drop the Label
                .ToArray();
 
// Write out the feature names and their importance to the model's R-squared value
for (int i = 0; i < featureNames.Length; i++)
  Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].rSquared:G4}");
```

如需使用 PFI 來分析模型特徵重要性的範例，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance.cs)。

\* 並非完全隨機，而是在整組範例中排列。
