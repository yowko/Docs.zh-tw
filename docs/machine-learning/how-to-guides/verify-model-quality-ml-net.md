---
title: 計算計量以評估機器學習模型品質 - ML.NET
description: 了解如何使用 ML.NET 計算計量及驗證機器學習模型品質
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149519"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="fa967-103">計算計量以評估機器學習模型品質 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="fa967-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

<span data-ttu-id="fa967-104">在您訓練模型後，如何評估品質？</span><span class="sxs-lookup"><span data-stu-id="fa967-104">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="fa967-105">每個機器學習工作都會公開計量，以供評估品質。</span><span class="sxs-lookup"><span data-stu-id="fa967-105">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="fa967-106">您可以使用工作的對應「內容」來評估模型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fa967-106">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```