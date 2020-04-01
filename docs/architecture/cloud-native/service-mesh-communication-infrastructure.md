---
title: 服務網格通訊基礎結構
description: 瞭解服務網格技術如何簡化雲原生微服務通信
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 6b177ef33b804ec35f3acb919539a97683e5a487
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523525"
---
# <a name="service-mesh-communication-infrastructure"></a>服務網格通訊基礎結構

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在本章中,我們探討了微服務通信的挑戰。 我們說過,開發團隊需要對後端服務如何相互溝通敏感。 理想情況下,服務間通信越少越好。 但是,由於後端服務通常相互依賴來完成操作,因此並非始終能夠避免。

我們探討了實現同步 HTTP 通信和非同步訊息傳遞的不同方法。 在每種情況下,開發人員都肩負著實現通信代碼的負擔。 通信代碼複雜且耗時。 不正確的決策可能會導致嚴重的性能問題。

一種更現代的微服務通信方法圍繞一種名為 *「服務網格*」的新的、快速發展的技術。 [服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是一個可配置的基礎結構層,具有處理服務到服務的通信、恢復能力和許多交叉問題的能力。 它將這些問題的責任從微服務轉移到服務網格層中。 通信從微服務中抽象出來。

服務網格的關鍵元件是代理。 在雲本機應用程式中,代理的實例通常與每個微服務共存。 當它們在單獨的進程中執行時,兩者是緊密相連的,並且共用相同的生命週期。 此模式稱為[側車模式](https://docs.microsoft.com/azure/architecture/patterns/sidecar),如圖 4-24 所示。

![帶側車的服務網](./media/service-mesh-with-side-car.png)

**圖 4-24**： 帶側車的服務網

請注意,在上圖中,與每個微服務一起運行的代理如何截獲消息。 每個代理都可以配置特定於微服務的流量規則。 它瞭解消息,並可以路由它們跨越您的服務和外部世界。

除了管理服務到服務的通信外,服務網格還提供對服務發現和負載平衡的支援。

配置後,服務網格功能極致。 網格從服務發現終結點檢索相應的實例池。 它將請求發送到特定的服務實例,記錄結果的延遲和回應類型。 它根據不同因素(包括最近請求的觀察延遲)選擇最有可能返回快速回應的實例。

服務網格在應用程式級別管理流量、通信和網路問題。 它瞭解消息和請求。 服務網格通常與容器協調器集成。 Kubernetes 支援一種可擴展的體系結構,可以在其中添加服務網格。

在第 6 章中,我們深入探討了服務網格技術,包括討論其體系結構和可用的開源實現。

## <a name="summary"></a>摘要

在本章中,我們討論了雲原生通信模式。 我們首先研究前端用戶端如何與後端微服務通信。 在此過程中,我們討論了 API 閘道平臺和即時通信。 然後,我們研究了微服務如何與其他後端服務通信。 我們研究了同步 HTTP 通信和跨服務的非同步訊息傳遞。 我們介紹了 gRPC,這是雲原生世界中即將推出的技術。 最後,我們推出了一種名為"服務網格"的快速發展的新技術,該技術可以簡化微服務通信。

特別強調託管 Azure 服務,這些服務可説明在雲本機系統中實現通信:

- [Azure 應用程式閘道](https://docs.microsoft.com/azure/application-gateway/overview)
- [Azure API 管理](https://azure.microsoft.com/services/api-management/)
- [Azure SignalR 服務](https://azure.microsoft.com/services/signalr-service/)
- [Azure 儲存體佇列](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure 事件網格](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure 事件中心](https://azure.microsoft.com/services/event-hubs/)

接下來,我們將轉向雲原生系統中的分散式數據及其帶來的益處和挑戰。

### <a name="references"></a>參考

- [.NET 微服務:容器化 .NET 應用程式的體系結構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [為微服務設計服務間通訊](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR 服務,一個完全託管的服務,用於新增即時功能](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Azure API 閘道閘道控制器](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [關於 Azure 庫伯內斯服務 (AKS) 中的入口](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [gRPC 文件](https://grpc.io/docs/guides/)

- [適用於 WCF 開發人員的 gRPC](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [將 gRPC 服務與 HTTP API 進行比較](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [使用 .NET 視訊建構 gRPC 服務](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[前一個](grpc.md)
>[下一個](Database-per-microservice.md)
