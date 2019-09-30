---
title: 微服務可定址性和服務登錄
description: 了解容器映像登錄在微服務架構中的角色。
ms.date: 09/20/2018
ms.openlocfilehash: d72ba399f3da730f0e57c44c5ec01c1cc9f5fc05
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674045"
---
# <a name="microservices-addressability-and-the-service-registry"></a>微服務可定址性和服務登錄

每個微服務都有用來解析其位置的唯一名稱 (URL)。 只要您的微服務正在執行，就必須是可定址的。 如果您必須想一下正在執行特定微服務的電腦為何，問題可能會急遽惡化。 就像是 DNS 將 URL 解析為特定電腦，您的微服務也必須具有唯一名稱，才能探索其目前位置。 微服務需要可定址的名稱，以獨立於其執行所在的基礎結構。 這表示服務的部署方式與探索方式之間會有互動，因為需要有[服務登錄](https://microservices.io/patterns/service-registry.html)。 同樣地，當電腦失敗時，登錄服務必須能夠指出服務現在正在執行的位置。

[服務登錄模式](https://microservices.io/patterns/service-registry.html)是服務探索的主要部分。 登錄是包含服務執行個體之網路位置的資料庫。 服務登錄必須高度可用且處於最新狀態。 用戶端可以快取從服務登錄取得的網路位置。 不過，該資訊最終會過期，此時用戶端將無法再探索服務執行個體。 因此，服務登錄是由伺服器叢集所組成，這些伺服器使用複寫通訊協定來維護一致性。

在某些微服務部署環境中 (稱為叢集，本節稍後將會討論)，服務探索是內建的。 例如，Azure Container Service with Kubernetes (AKS) 環境可以處理服務執行個體註冊和取消註冊。 它也會在扮演伺服器端探索路由器角色的每部叢集主機上執行 Proxy。

## <a name="additional-resources"></a>其他資源

- **Chris Richardson：模式：Service registry** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0：服務登錄** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker：服務探索** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[上一頁](maintain-microservice-apis.md)
>[下一頁](microservice-based-composite-ui-shape-layout.md)
