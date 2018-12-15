---
title: 讓定型機器學習模型能在應用程式中運作 - ML.NET
description: 探索如何使用 ML.NET 取用應用程式中的定型和評估機器學習模型
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ff3f0a8856382d020129693bcf722f572fd87606
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131642"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>讓定型機器學習模型能在應用程式中運作 - ML.NET

當您滿意模型計量時，就可以讓模型「運作」。 您建置的 `model` 物件可以在不同環境中取用、保存及重複使用，並且會套用它在定型期間「學習」的相同步驟。

若要將模型儲存至檔案並載入 (可能是在不同內容中)，請使用下列範例：

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
