---
title: 計算計量以評估機器學習模型品質
description: 了解如何使用 ML.NET 計算計量及驗證機器學習模型品質
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975834"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>計算計量以評估機器學習模型品質

> [!NOTE]
> 此主題參考 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請造訪[ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)頁面。

本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。 如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。

在您訓練模型後，如何評估品質？ 每個機器學習工作都會公開計量，以供評估品質。

您可以使用工作的對應「內容」來評估模型，如下列範例所示：

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
