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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>計算計量以評估機器學習模型品質 

> [!NOTE]
> 本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。

本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。 如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。

在您訓練模型後，如何評估品質？ 每個機器學習工作都會公開計量，以供評估品質。

您可以使用工作的對應「內容」來評估模型，如下列範例所示：

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
