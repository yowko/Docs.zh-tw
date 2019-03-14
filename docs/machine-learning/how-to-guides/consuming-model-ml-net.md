---
title: 讓定型機器學習模型能在應用程式中運作 - ML.NET
description: 探索如何使用 ML.NET 取用應用程式中的定型和評估機器學習模型
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675130"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="974ab-103">讓定型機器學習模型能在應用程式中運作 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="974ab-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="974ab-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="974ab-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="974ab-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="974ab-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="974ab-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="974ab-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="974ab-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊</span><span class="sxs-lookup"><span data-stu-id="974ab-107">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="974ab-108">當您滿意模型計量時，就可以讓模型「運作」。</span><span class="sxs-lookup"><span data-stu-id="974ab-108">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="974ab-109">您建置的 `model` 物件可以在不同環境中取用、保存及重複使用，並且會套用它在定型期間「學習」的相同步驟。</span><span class="sxs-lookup"><span data-stu-id="974ab-109">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="974ab-110">若要將模型儲存至檔案並載入 (可能是在不同內容中)，請使用下列範例：</span><span class="sxs-lookup"><span data-stu-id="974ab-110">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

```csharp
using (var stream = File.Create(modelPath))
{
    // Saving and loading happens to 'dynamic' models.
    mlContext.Model.Save(model, stream);
}

// Potentially, the lines below can be in a different process altogether.

// When you load the model, it's a transformer.
ITransformer loadedModel;
using (var stream = File.OpenRead(modelPath))
    loadedModel = mlContext.Model.Load(stream);
```
