---
title: 計算計量以評估機器學習模型品質
description: 了解如何使用 ML.NET 計算計量及驗證機器學習模型品質
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2c7749205b862a42f42b857972057c441ab84364
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641100"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="c8bcf-103">計算計量以評估機器學習模型品質</span><span class="sxs-lookup"><span data-stu-id="c8bcf-103">Calculate metrics to evaluate machine learning model quality</span></span> 

> [!NOTE]
> <span data-ttu-id="c8bcf-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="c8bcf-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="c8bcf-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="c8bcf-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="c8bcf-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="c8bcf-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="c8bcf-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c8bcf-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="c8bcf-108">在您訓練模型後，如何評估品質？</span><span class="sxs-lookup"><span data-stu-id="c8bcf-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="c8bcf-109">每個機器學習工作都會公開計量，以供評估品質。</span><span class="sxs-lookup"><span data-stu-id="c8bcf-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="c8bcf-110">您可以使用工作的對應「內容」來評估模型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c8bcf-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
