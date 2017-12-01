---
title: "建立、 發展，以及版本控制的微服務應用程式開發介面和合約"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |建立、 發展，以及版本控制的微服務應用程式開發介面和合約"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 433711c3479eafd52bf9f5d53faf8e5707c6c624
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>建立、 發展，以及版本控制的微服務應用程式開發介面和合約

應用程式開發介面的微服務是服務與其用戶端之間的合約。 您可以獨立進行微服務，才不會中斷其 API 合約，合約是很重要的原因。 如果您變更合約時，它會影響用戶端應用程式或您應用程式開發介面的閘道。

API 定義的性質取決於您所使用的通訊協定。 比方說，如果您使用的訊息 (像是[AMQP](https://www.amqp.org/))，應用程式開發介面所組成的訊息類型。 如果您使用 HTTP 和 RESTful 服務，應用程式開發介面包含和要求和回應的 JSON 格式的 Url。

不過，即使您即將仔細考量您初始的合約，服務 API 必須隨著時間而變更。 當發生這種情況，特別是如果您的 API 是由多個用戶端應用程式的公用 API — 通常無法強制升級到新的 API 合約的所有用戶端。 您通常需要以累加方式部署新版本的服務，同時執行的服務合約的舊的和新版本的方式。 因此，就一定要有您的服務版本控制的策略。

很小，如果屬性或新增參數到您的 API 類似的應用程式開發介面變更時，使用較舊的 API 的用戶端應該切換，並使用新版本的服務。 您可以提供預設值是必要的任何遺漏的屬性，而且用戶端可能無法略過任何額外的回應屬性。

不過，有時候您需要對服務 API 的主要和不相容的變更。 因為您不可能強制立即升級為新版本的用戶端應用程式或服務，服務必須支援舊版的 API 段。 如果您使用以 HTTP 為基礎的機制，例如 REST，其中一個方法是內嵌的應用程式開發介面版本號碼，在 URL 或 HTTP 標頭。 然後您可以決定實作這兩個版本的服務同時在相同的服務執行個體，或部署每個處理的 API 版本的不同執行個體之間。 很好的方法，這個[暫留處理器模式](https://en.wikipedia.org/wiki/Mediator_pattern)(例如， [MediatR 文件庫](https://github.com/jbogard/MediatR)) 獨立的處理常式分離的不同實作版本。

最後，如果您使用 REST 架構[超](https://www.infoq.com/articles/mark-baker-hypermedia)是最佳的解決方案進行版本控制您的服務，並允許 evolvable 應用程式開發介面。

## <a name="additional-resources"></a>其他資源

-   **Scott Hanselman。ASP.NET Core RESTful Web API 版本設定輕鬆**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **版本控制 RESTful web API**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **伊 Fielding。版本控制、 超和 REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[上一個](非同步的訊息為基礎-communication.md) [下一步] (microservices-可定址性-服務-registry.md)
