---
title: 將 eShopOnContainers 對應至 Azure 服務
description: 將 eShopOnContainers 對應至 Azure 服務，例如 Azure Kubernetes Service、API 閘道和 Azure 服務匯流排。
ms.date: 06/30/2019
ms.openlocfilehash: feb6d8f5ca05ab55ce4695d1200766a18b8f744a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182815"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>將 eShopOnContainers 對應至 Azure 服務

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雖然並非必要，但 Azure 非常適合支援 eShopOnContainers，因為專案已建立為雲端原生應用程式。 應用程式是以 .NET Core 為基礎，因此它可以在 Linux 或 Windows 容器上執行，視 Docker 主機而定。 應用程式是由多個自發微服務所組成，每個都有自己的資料。 不同的微服務展示不同的方法，範圍從簡單的 CRUD 作業到更複雜的 DDD 和 CQRS 模式。 微服務透過 HTTP 與用戶端通訊，透過以訊息為基礎的通訊彼此。 應用程式也支援多個用戶端平臺，因為它採用 HTTP 作為標準通訊協定，並包含在 Android、iOS 和 Windows 平臺上執行的 ASP.NET Core 和 Xamarin 行動應用程式。

應用程式的架構如圖2-5 所示。 左側是用戶端應用程式，分成行動、傳統 Web 和 Web 單頁應用程式（SPA）等。 右側是組成系統的伺服器端元件，每一個都可以裝載于 Docker 容器和 Kubernetes 叢集。 傳統的 web 應用程式由以黃色顯示的 ASP.NET Core MVC 應用程式提供技術支援。 此應用程式和行動和 web SPA 應用程式會透過一或多個 API 閘道與個別微服務通訊。 API 閘道會遵循「前端的後端」（BFF）模式，這表示每個閘道都是設計來支援指定的前端用戶端。 個別的微服務會列在 API 閘道的右邊，同時包含商務邏輯和某種類型的持續性存放區。 不同的服務會利用 SQL Server 資料庫、Redis 快取實例和 MongoDB/CosmosDB 存放區。 最右側的是系統的事件匯流排，用於微服務之間的通訊。

![eShopOnContainers 架構](./media/eshoponcontainers-architecture.png)
**圖 2-5**。 EShopOnContainers 架構。

此架構的伺服器端元件可輕鬆地對應至 Azure 服務。

## <a name="container-orchestration-and-clustering"></a>容器協調流程和叢集

應用程式的容器裝載服務（從 ASP.NET Core MVC 應用程式到個別目錄和排序微服務）可以在 Azure Kubernetes Service （AKS）中進行裝載和管理。 應用程式可以在 Docker 和 Kubernetes 本機上執行，然後將相同的容器部署至裝載于 AKS 中的預備和生產環境。 此程式可以自動化，如我們在下一節中所見。

AKS 為個別的容器叢集提供管理服務。 應用程式會為上述架構圖中顯示的每個微服務部署個別的 AKS 叢集。 這種方法可讓每個個別服務根據其資源需求各自獨立。 每個微服務也可以獨立部署，而且在理想的情況下，這類部署應該會產生零的系統停機時間。

## <a name="api-gateway"></a>API 閘道

EShopOnContainers 應用程式有多個前端用戶端和多個不同的後端服務。 用戶端應用程式與支援它們的微服務之間不會有一對一的對應關係。 在這種情況下，以安全的方式撰寫用戶端軟體以與各種後端服務互動時，可能會有很大的複雜性。 每個用戶端都需要自行解決這項複雜性，因而導致重複，以及在服務變更或新原則執行時進行更新的許多位置。

Azure API 管理（APIM）可協助組織以一致且易於管理的方式發佈 Api。 APIM 是由三個元件所組成： API 閘道和系統管理入口網站（Azure 入口網站），以及開發人員入口網站。

API 閘道會接受 API 呼叫，並將其路由傳送至適當的後端 API。 它也可以在不修改程式碼的情況下，提供額外的服務（例如 API 金鑰或 JWT 權杖和 API 轉換），而不需修改程式碼（例如，為了配合需要較舊介面的用戶端）。

Azure 入口網站，您可以在其中定義 API 架構，並將不同的 Api 封裝到產品中。 您也可以設定使用者存取、查看報告，以及設定配額或轉換的原則。

開發人員入口網站作為開發人員的主要資源。 它會為開發人員提供 API 檔、互動式測試主控台，並報告自己的使用方式。 開發人員也可以使用入口網站來建立及管理自己的帳戶，包括訂用帳戶和 API 金鑰支援。

使用 APIM，應用程式可以公開數個不同的服務群組，每個都提供特定前端用戶端的後端。 針對複雜的案例，建議使用 APIM。 為了簡化需求，可以使用輕量 API 閘道 Ocelot。 EShopOnContainers 應用程式會使用 Ocelot，因為它是簡單的，而且可以部署到與應用程式本身相同的應用程式環境中。 [深入瞭解 eShopOnContainers、APIM 和 Ocelot。](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern#azure-api-management)

如果您的應用程式使用 AKS，另一個選項是將 Azure 閘道輸入控制器部署為 AKS 叢集中的 pod。 這可讓您的叢集與 Azure 應用程式閘道整合，讓閘道能夠對 AKS pod 的流量進行負載平衡。 [深入瞭解適用于 AKS 的 Azure 閘道輸入控制器](https://github.com/Azure/application-gateway-kubernetes-ingress)。

## <a name="data"></a>資料

EShopOnContainers 所使用的各種後端服務會有不同的儲存需求。 有數個微服務使用 SQL Server 資料庫。 購物籃微服務會利用 Redis 快取來保存其持續性。 位置微服務需要 MongoDB API 來取得其資料。 Azure 支援每種資料格式。

針對 SQL Server 資料庫支援，Azure 提供從單一資料庫到可高度擴充 SQL Database 彈性集區之所有專案的產品。 您可以設定個別的微服務，以便快速且輕鬆地與自己的個別 SQL Server 資料庫進行通訊。 這些資料庫可以視需要調整，以根據其需求來支援每個不同的微服務。

EShopOnContainers 應用程式會將使用者目前的購物籃儲存在要求之間。 這是由將資料儲存在 Redis 快取中的購物籃微服務所管理。 在開發中，此快取可以部署在容器中，而在生產環境中，它可以使用 Azure Cache for Redis。 Azure Cache for Redis 是完全受控的服務，可提供高效能和可靠性，而不需要自行部署和管理 Redis 實例或容器。

[位置] 微服務會使用 MongoDB NoSQL 資料庫來保存其持續性。 在開發期間，資料庫可以部署在自己的容器中，而在生產環境中，服務可以利用[Azure Cosmos DB 適用于 MongoDB 的 API](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)。 Azure Cosmos DB 的優點之一，就是能夠利用多個不同的通訊協定，包括 SQL API 和常見的 NoSQL Api，包括 MongoDB、Cassandra、Gremlin 和 Azure 表格儲存體。 Azure Cosmos DB 提供完全受控且全域散發的資料庫即服務，可進行調整以符合使用它的服務需求。

[第5章](distributed-data.md)會詳細說明雲端原生應用程式中的分散式資料。

## <a name="event-bus"></a>事件匯流排

應用程式會使用事件來傳達不同服務之間的變更。 這項功能可以使用各種不同的實作為實作為，而在本機 eShopOnContainers 應用程式會使用[RabbitMQ](https://www.rabbitmq.com/)。 在 Azure 中裝載時，應用程式會利用[Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus/)來進行訊息處理。 Azure 服務匯流排是完全受控的整合訊息代理人，可讓應用程式和服務以分離、可靠且非同步方式彼此通訊。 Azure 服務匯流排支援個別的佇列，以及不同的*主題*來支援「發行者」訂閱者案例。 EShopOnContainers 應用程式會利用 Azure 服務匯流排的主題來支援將訊息從一個微服務散發到任何其他需要回應指定訊息的微服務。

## <a name="resiliency"></a>恢復

一旦部署到生產環境後，eShopOnContainers 應用程式就能夠利用數個可用的 Azure 服務來改善其復原能力。 應用程式會發佈健康情況檢查，其可與 Application Insights 整合，以根據應用程式的可用性提供報告和警示。 Azure 資源也會提供診斷記錄，以用來識別及更正錯誤和效能問題。 資源記錄會提供應用程式使用不同 Azure 資源的時機和方式的詳細資訊。 您將在[第6章](resiliency.md)深入瞭解雲端原生復原功能。

## <a name="references"></a>reference

- [EShopOnContainers 架構](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [協調微服務和多容器應用程式的高延展性和可用性](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [Azure API 管理](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [Azure SQL Database 總覽](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Azure Cache for Redis](https://azure.microsoft.com/services/cache/)
- [Azure Cosmos DB 適用于 MongoDB 的 API](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure 監視器總覽](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[上一頁](introduce-eshoponcontainers-reference-app.md)
>[下一頁](deploy-eshoponcontainers-azure.md)
