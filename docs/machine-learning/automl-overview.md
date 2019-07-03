---
title: ML.NET 的自動化機器學習
description: 自動模型選取和定型概觀
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 39e454d67f60280c6a43e3b80d788d873345ab77
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307381"
---
# <a name="automated-machine-learning-with-mlnet"></a>ML.NET 的自動化機器學習

自動化機器學習是 ML.NET 的一項功能，可執行自動模型選取和定型。 您可以指定機器學習工作並提供資料集，而自動化 ML 會選擇具有最佳計量的模型。 它會輸出：
- 可載入預測應用程式的模型檔案
- 進行預測的應用程式程式碼
- 用於特徵選取和模型定型 (以了解模型) 的原始程式碼

> [!NOTE]
> 這項功能目前處於預覽狀態，資料可能會有變更。 

自動化 ML 目前僅限於二元分類、多元分類和迴歸的機器學習[工作](resources/tasks.md)。 未來版本將支援其他機器學習工作。

使用自動化 ML 的方法三種：
1. 在命令列上，使用 [ML.NET CLI](automate-training-with-cli.md)
1. 透過應用程式，使用[自動化 ML API](how-to-guides/how-to-use-the-automl-api.md)
1. 透過圖形化使用者介面，使用 ML.NET 模型產生器
