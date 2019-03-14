---
title: 計算計量以評估機器學習模型品質 - ML.NET
description: 了解如何使用 ML.NET 計算計量及驗證機器學習模型品質
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: ad71f7da6981ac370e60725f88d3c70b1d5c5237
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679212"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="1d606-103">計算計量以評估機器學習模型品質 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="1d606-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="1d606-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="1d606-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="1d606-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="1d606-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="1d606-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="1d606-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="1d606-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="1d606-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="1d606-108">在您訓練模型後，如何評估品質？</span><span class="sxs-lookup"><span data-stu-id="1d606-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="1d606-109">每個機器學習工作都會公開計量，以供評估品質。</span><span class="sxs-lookup"><span data-stu-id="1d606-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="1d606-110">您可以使用工作的對應「內容」來評估模型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1d606-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```