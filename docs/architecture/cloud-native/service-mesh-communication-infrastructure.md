---
title: 服務網格通訊基礎結構
description: 瞭解服務網格技術如何簡化雲端原生微服務通訊
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 39dc1ded06eb0b92a2a1b40cfe981d9bd49bf381
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165945"
---
# <a name="service-mesh-communication-infrastructure"></a>服務網格通訊基礎結構

在本章節中，我們探討了微服務通訊的挑戰。 我們說過，開發小組必須區分後端服務與彼此通訊的方式。 在理想情況下，服務間通訊越少越好。 不過，因為後端服務通常會依賴另一個來完成作業，所以不一定可以避免。

我們探討了各種不同的方法來執行同步 HTTP 通訊和非同步訊息處理。 在每個案例中，開發人員會負擔執行通訊程式碼。 通訊程式碼很複雜，而且需要大量時間。 不正確的決策可能會導致明顯的效能問題。

更新式的方法，微服務通訊中心圍繞著全新且快速發展的技術，以提供 *服務網格*。 [服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是可設定的基礎結構層，具有內建功能可處理服務對服務的通訊、復原能力，以及許多跨領域考慮。 它會將這些疑慮的責任移出微服務和服務網格層。 從您的微服務抽離通訊。

服務網格的主要元件是 proxy。 在雲端原生應用程式中，proxy 的實例通常會與每個微服務共存。 當它們在不同的進程中執行時，兩者會緊密連結並共用相同的生命週期。 這種模式也稱為 [側車模式](/azure/architecture/patterns/sidecar)，如 [圖 4-24] 所示。

![具有側面汽車的服務網格](./media/service-mesh-with-side-car.png)

**圖 4-24**： 具有側面汽車的服務網格

在上圖中，請注意，在每個微服務旁執行的 proxy 會攔截訊息。 每個 proxy 都可以使用微服務特定的流量規則來設定。 它瞭解訊息，並且可以將訊息路由傳送到您的服務和外界。

除了管理服務對服務的通訊之外，服務網狀也提供服務探索和負載平衡的支援。

一旦設定之後，服務網格會具有高功能。 網格會從服務探索端點抓取對應的實例集區。 它會將要求傳送至特定的服務實例，並記錄結果的延遲和回應類型。 它會根據不同的因素，選擇最可能傳回快速回應的實例，包括最近要求的觀察延遲。

服務網格會管理應用層級的流量、通訊和網路考慮。 它瞭解訊息和要求。 服務網格通常會與容器協調器整合。 Kubernetes 支援可延伸的架構，可在其中新增服務網格。

在第6章中，我們將深入探討服務網格技術，包括對其架構和可用開放原始碼執行的討論。

## <a name="summary"></a>摘要

在本章中，我們討論了雲端原生通訊模式。 我們一開始先檢查前端用戶端與後端微服務通訊的方式。 過程中，我們討論了 API 閘道平臺和即時通訊。 我們接著探討了微服務如何與其他後端服務進行通訊。 我們探討了同步的 HTTP 通訊和跨服務的非同步訊息。 我們討論了 gRPC，這是雲端原生世界中即將推出的技術。 最後，我們推出了一項全新且快速發展的技術，其可簡化微服務通訊的服務網格。

特別著重于受控 Azure 服務，可協助在雲端原生系統中執行通訊：

- [Azure 應用程式閘道](/azure/application-gateway/overview)
- [Azure API 管理](https://azure.microsoft.com/services/api-management/)
- [Azure SignalR 服務](https://azure.microsoft.com/services/signalr-service/)
- [Azure 儲存體佇列](/azure/storage/queues/storage-queues-introduction)
- [Azure 服務匯流排](/azure/service-bus-messaging/service-bus-messaging-overview)
- [事件格線](/azure/event-grid/overview)
- [Azure 事件中樞](https://azure.microsoft.com/services/event-hubs/)

接下來我們將移至雲端原生系統中的分散式資料，以及其所提供的優點和挑戰。

### <a name="references"></a>參考資料

- [.NET 微服務：容器化 .NET 應用程式的架構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [設計微服務的服務間通訊](/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR Service 是完全受控的服務，可新增即時功能](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Azure API 閘道輸入控制器](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [關於 Azure Kubernetes Service (AKS 中的輸入) ](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [gRPC 檔](https://grpc.io/docs/guides/)

- [適用於 WCF 開發人員的 gRPC](../grpc-for-wcf-developers/index.md)

- [比較 gRPC 服務與 HTTP Api](/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [使用 .NET 建立 gRPC 服務影片](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[上一個](grpc.md) 
>[下一步](distributed-data.md)
