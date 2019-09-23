---
title: 服務網格通訊基礎結構
description: 瞭解服務網格技術如何簡化雲端原生微服務通訊
author: robvet
ms.date: 09/10/2019
ms.openlocfilehash: dc9237197732ea622aad726583140623b0a5a4f4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184782"
---
# <a name="service-mesh-communication-infrastructure"></a>服務網格通訊基礎結構

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在本章中，我們探討了微服務通訊的挑戰。 我們說過，開發小組必須區分後端服務彼此通訊的方式。 在理想的情況下，服務間的通訊越少越好。 不過，不一定可以避免這種情況，因為後端服務通常會依賴另一個來完成作業。

我們探索了不同的方法來執行同步 HTTP 通訊和非同步訊息。 在每個案例中，開發人員都有執行通訊程式碼的負擔。 通訊程式碼既複雜又耗費時間。 不正確的決策可能會導致嚴重的效能問題。

一種更現代化的方法，可微服務通訊中心，這是一項新的快速發展技術，以*服務網格*為依據。 [服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是可設定的基礎結構層，具有內建功能，可處理服務對服務的通訊、復原，以及許多跨領域考慮。 它會將這些顧慮的責任移出微服務和服務網格層。 通訊會從您的微服務中抽象化出來。

服務網格的主要元件是 proxy。 在雲端原生應用程式中，proxy 的實例通常會與每個微服務共存。 當它們在不同的進程中執行時，這兩個會緊密連結，並共用相同的生命週期。 此模式稱為[側車模式](https://docs.microsoft.com/azure/architecture/patterns/sidecar)，如圖4-23 所示。

![具有側車的服務網格](./media/service-mesh-with-side-car.png)

**圖 4-23**： 具有側車的服務網格

請注意，在上圖中，每個微服務一起執行的 proxy 會攔截訊息。 每個 proxy 都可以使用微服務特定的流量規則來設定。 它瞭解訊息，並可在您的服務和外部世界之間路由傳送。 

除了管理服務對服務的通訊，服務網格也提供服務探索和負載平衡的支援。 

設定好之後，服務網格就能發揮高功能。 網格會從服務探索端點抓取對應的實例集區。 它會將要求傳送至特定的服務實例，並記錄結果的延遲和回應類型。 它會根據不同的因素（包括最近要求的觀察延遲），選擇最有可能傳回快速回應的實例。

服務網格會管理應用層級的流量、通訊和網路問題。 它瞭解訊息和要求。 服務網格通常會與容器協調器整合。 Kubernetes 支援可在其中加入服務網格的可擴充架構。

在第6章中，我們深入探討服務網格技術，包括對其架構和可用開放原始碼的整合進行討論。

## <a name="summary"></a>總結

在本章中，我們討論了雲端原生通訊模式。 我們一開始先檢查前端用戶端如何與後端微服務通訊。 在過程中，我們討論了 API 閘道平臺和即時通訊。 接著，我們探討了微服務如何與其他後端服務通訊。 我們探討了同步 HTTP 通訊，以及跨服務的非同步訊息。 我們涵蓋了 gRPC，這是雲端原生世界中即將推出的技術。 最後，我們引進了一項新的、快速發展的技術，其服務網格可簡化微服務通訊。 

特別著重于受控 Azure 服務，可協助您在雲端原生系統中執行通訊：

- [Azure 應用程式閘道](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API 管理](https://azure.microsoft.com/services/api-management/)
- [Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/)
- [Azure 儲存體佇列](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure 事件格線](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure 事件中樞](https://azure.microsoft.com/services/event-hubs/)

接下來，移至雲端原生系統中的分散式資料，以及它所呈現的優點和挑戰。

### <a name="references"></a>reference 

- [.NET 微服務：容器化 .NET 應用程式的架構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)
  
- [設計微服務的服務間通訊](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR Service，這是一種完全受控的服務，可新增即時功能](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)
  
- [Azure API 閘道輸入控制器](https://azure.github.io/application-gateway-kubernetes-ingress/)
  
- [關於 Azure Kubernetes Service 中的輸入（AKS）](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)
 
- [實際 gRPC](https://www.worldcat.org/title/practical-grpc/oclc/1042342319)

- [gRPC 檔](https://grpc.io/docs/guides/)

- [WCF 開發人員的 gRPC](https://bing.com)[Mark's gRPC book]
  
- [比較 gRPC 服務與 HTTP Api](https://docs.microsoft.com/en-us/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

>[!div class="step-by-step"]
>[上一頁](rest-grpc.md)
>[下一頁](distributed-data.md) <!-- Next Chapter -->
