---
title: "Microservices 可定址性與在服務登錄"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Microservices 可定址性與在服務登錄"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 19a0200dadfb90a455de690d880f4eeae4772ed7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a>Microservices 可定址性與在服務登錄

每個微服務有唯一的名稱 (URL)，用來解析其位置。 您的微服務必須是可定址，只要它正在執行。 如果您有想想執行特定的微服務相關的電腦，可能發生錯誤快速。 DNS 解析 URL，特定電腦的相同方式，在您的微服務需要有唯一的名稱，使其目前位置是可探索。 Microservices 需要可定址的名稱，因此獨立於基礎結構上執行。 這暗示會如何部署您的服務和其探索的方式之間的互動因為需要有[服務登錄](http://microservices.io/patterns/service-registry.html)。 同樣地，在電腦失敗時，登錄服務必須能夠指出現在正在服務執行。

[服務登錄模式](http://microservices.io/patterns/service-registry.html)服務探索的主要部分。 登錄是包含的服務執行個體的網路位置的資料庫。 服務登錄，就必須是高度可用且最新狀態。 用戶端可以快取取得從服務登錄的網路位置。 不過，該資訊最終會過期，而且用戶端不會再找出服務執行個體。 因此，服務登錄使用複寫通訊協定，以維護一致性的伺服器叢集所組成。

有些微服務部署在環境中 （稱為群集，以在稍後的章節中討論），服務探索是內建。 例如，在 Azure 容器服務環境中，Kubernetes DC/OS 與馬拉松可以處理服務執行個體登錄和解除登錄。 它們也扮演的角色的伺服器端探索路由器每一部叢集主機上執行的 proxy。 另一個例子是 Azure Service Fabric，它也會提供它的方塊外命名服務透過服務登錄。

請注意，某些服務登錄和 API 閘道模式，可協助解決此問題也之間的重疊。 例如， [Service Fabric 反向 Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)是一種 API 閘道服務 Fabrice 命名服務為基礎和以協助解析位址解析為內部服務實作。

## <a name="additional-resources"></a>其他資源

-   **Chris Richardson。模式： 服務登錄**
    *http://microservices.io/patterns/service-registry.html*

-   **Auth0。服務登錄**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker。服務探索**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[上一個](維護的微服務-apis.md) [下一步] (microservice-based-composite-ui-shape-layout.md)
