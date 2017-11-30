---
title: "處理部分失敗的策略"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |處理部分失敗的策略"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ff3bed530b13a9b1822c7cccf5a4d47df6fc6239
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="strategies-for-handling-partial-failure"></a>處理部分失敗的策略

部分失敗的處理策略包括下列各項。

**使用非同步通訊 （例如，訊息為基礎的通訊） 跨內部 microservices**。 時，強烈建議建立跨內部 microservices 長的鏈結的同步 HTTP 呼叫，因為該錯誤的設計最後會變得不正確的潛在性中斷問題的主要原因。 相反地，除了用戶端應用程式與 microservices 或更細緻的 API 閘道的第一個層級之間的前端通訊，最好是使用只非同步 （訊息） 通訊的初始要求過去的一次 /回應循環，跨內部 microservices。 最終一致性和事件驅動的架構將有助於減少漣漪效果。 這些方法會強制執行較高層級的微服務自主性，以及因此防止此註明的問題。

**重試使用指數型輪詢**。 這項技術有助於避免簡短，並藉由執行呼叫斷斷續續地發生失敗重試特定數目的時間，以防服務不是僅供一小段時間。 這可能是因為間歇性的網路問題或微服務/容器會移至叢集中不同節點。 不過，如果這些重試設計不是正確斷路器，它可以 aggravate 漣漪，最終甚至導致[阻絕服務 (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)。

**因應措施網路逾時**。 一般情況下，用戶端應該正確不無限期地封鎖和等候回應時，一律使用逾時。 使用逾時，可確保，資源會永遠不會繫結起來，無限期。

**使用斷路器模式**。 這種方法，用戶端處理序會追蹤失敗要求數目。 如果錯誤速率超過設定的限制時，「 斷路器 」 往返，以便進一步嘗試就會立即失敗。 （如果大量的要求失敗，這就表示服務無法使用，傳送要求，則不必。）逾時期限之後用戶端應該再試一次，如果新的要求成功，關閉斷路器。

**提供後援**。 這種方法，用戶端處理序時，執行後援邏輯要求失敗，例如傳回快取的資料還是預設值。 這是一種方法適用於查詢，而且更複雜的更新或命令。

**限制的佇列要求數目**。 用戶端應該也會造成未處理的用戶端微服務可以傳送給特定服務的要求數目上限。 如果已達到限制，它是提出其他要求，可能毫無意義，而且每次嘗試應該會立即失敗。 方面的實作，Polly[艙隔離](https://github.com/App-vNext/Polly/wiki/Bulkhead)原則可用來達到此需求。 這種方法是基本上與平行處理節流[SemaphoreSlim](https://docs.microsoft.com/dotnet/api/system.threading.semaphoreslim?view=netcore-1.1)做為實作。 它也允許艙以外的 「 佇列 」。 您可以主動剖析之前執行過多的負載，（比方說，因為容量會被視為完整）。 這可讓某些失敗情況下的其回應速度快過為斷路器，因為斷路器等候失敗。 Polly BulkheadPolicy 物件會公開多滿艙和佇列，以及提供事件發生溢位因此也可用來自動化的水平延展的磁碟機。

## <a name="additional-resources"></a>其他資源

-   **恢復模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **新增恢復功能和最佳化效能**
    [*https://msdn.microsoft.com/en-us/library/jj591574.aspx*](https://msdn.microsoft.com/en-us/library/jj591574.aspx)

-   **艙。** GitHub 儲存機制。 Polly 原則的實作。 \
    [*https://github.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   **設計 Azure 的應用程式彈性**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)

-   **暫時性錯誤處理**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults>


>[!div class="step-by-step"]
[上一個](控制代碼的部分-failure.md) [下一步] (實作-重試-指數-backoff.md)
