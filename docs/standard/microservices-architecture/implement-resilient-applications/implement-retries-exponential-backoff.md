---
title: "使用指數型輪詢實作重試次數"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |使用指數型輪詢實作重試次數"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8ad8c6363ddff59915efc076161fe6b76074bbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-retries-with-exponential-backoff"></a>使用指數型輪詢實作重試次數

[*使用指數型輪詢重試*](https://docs.microsoft.com/azure/architecture/patterns/retry)是嘗試重試作業，並具有以等比級數增加等候時間，直到達到最大重試計數為止的技術 ([指數型輪詢](https://en.wikipedia.org/wiki/Exponential_backoff)). 這項技術採用雲端資源可能間歇會無法使用超過幾秒鐘，因為任何原因的事實。 例如，orchestrator 可能移動容器以進行負載平衡叢集中的另一個節點。 在這段時間，有些要求可能會失敗。 另一個範例可能是 SQL Azure 資料庫可以移至另一部伺服器的負載平衡，這將導致資料庫至其中幾秒鐘的時間期間，無法像資料庫。

有許多方法可以實作使用指數型輪詢的重試邏輯。


>[!div class="step-by-step"]
[上一個](部分-失敗-strategies.md) [下一步] (implement-resilient-entity-framework-core-sql-connections.md)
