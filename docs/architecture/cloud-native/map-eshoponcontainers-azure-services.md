---
title: 將 eShopOnContainers 對應至 Azure 服務
description: 將 eShopOnContainers 對應至 Azure 服務，例如 Azure Kubernetes Service、API 閘道和 Azure 服務匯流排。
ms.date: 05/13/2020
ms.openlocfilehash: c4627a4b6d9d8b62737984b507e638019544ab67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400444"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>將 eShopOnContainers 對應至 Azure 服務

雖然並非必要，但 Azure 非常適合用來支援 eShopOnContainers，因為專案已建立為雲端原生應用程式。 應用程式是使用 .NET Core 所建立，因此它可以在 Linux 或 Windows 容器上執行，視 Docker 主機而定。 應用程式是由多個自主微服務所組成，每個都有自己的資料。 不同的微服務展示不同的方法，範圍從簡單的 CRUD 作業，到更複雜的 DDD 和 CQRS 模式。 微服務透過 HTTP 與用戶端通訊，而透過以訊息為基礎的通訊則與用戶端通訊。 應用程式也支援多個平臺供用戶端使用，因為它採用 HTTP 作為標準通訊協定，並包含在 Android、iOS 和 Windows 平臺上執行的 ASP.NET Core 和 Xamarin 行動裝置應用程式。

應用程式的架構顯示在圖2-5 中。 左邊是用戶端應用程式， (SPA) 類別，分成行動、傳統 Web 和 Web 單一頁面應用程式。 右側是組成系統的伺服器端元件，每個元件都可以裝載于 Docker 容器和 Kubernetes 叢集中。 傳統的 web 應用程式是由以黃色顯示 ASP.NET Core MVC 應用程式所支援。 此應用程式和行動和 web SPA 應用程式會透過一或多個 API 閘道與個別微服務通訊。 API 閘道會遵循「前端後端」 (BFF) 模式，這表示每個閘道都是設計來支援指定的前端用戶端。 個別的微服務會列在 API 閘道的右邊，並包含商務邏輯和某種類型的持續性存放區。 不同的服務會利用 SQL Server 資料庫、Redis 快取實例和 MongoDB/CosmosDB 存放區。 最右邊的是系統的事件匯流排，用於微服務之間的通訊。

![eShopOnContainers 架構 ](./media/eshoponcontainers-architecture.png)
 **圖 2-5** 。 EShopOnContainers 架構。

此架構的伺服器端元件全都可輕易地對應至 Azure 服務。

## <a name="container-orchestration-and-clustering"></a>容器協調流程和叢集

應用程式的容器裝載服務（從 ASP.NET Core MVC 應用程式到個別類別目錄和訂購微服務）可以在 Azure Kubernetes Service (AKS) 中託管和管理。 應用程式可以在 Docker 和 Kubernetes 本機上執行，然後將相同的容器部署到裝載于 AKS 的預備環境和生產環境。 您可以依照下一節的說明，將此程式自動化。

AKS 為容器的個別叢集提供管理服務。 應用程式會針對 AKS 叢集中的每個微服務部署個別的容器，如上面的架構圖所示。 這種方法可讓每個個別的服務根據其資源需求獨立進行調整。 每個微服務也可以獨立部署，而且在理想的情況下，這類部署應該會產生零的系統停機時間。

## <a name="api-gateway"></a>API Gateway

EShopOnContainers 應用程式有多個前端用戶端與多個不同的後端服務。 用戶端應用程式和支援它們的微服務之間沒有一對一的對應關係。 在這種情況下，撰寫用戶端軟體時，可能會有很大的複雜性，以安全的方式與各種不同的後端服務進行介面。 每個用戶端都需要自行解決這種複雜性，進而產生重複的情況，以及在執行服務變更或新原則時，要進行更新的許多地方。

Azure API 管理 (APIM) 可協助組織以一致且可管理的方式發佈 Api。 APIM 由三個元件所組成： API 閘道和系統管理入口網站 (Azure 入口網站) 和開發人員入口網站。

API 閘道會接受 API 呼叫，並將其路由傳送至適當的後端 API。 它也可以在不修改程式碼的情況下，即時提供其他服務（例如 API 金鑰或 JWT 權杖和 API 轉換），而不需要修改程式碼 (例如，以容納需要較舊介面) 的用戶端。

Azure 入口網站是您定義 API 架構並將不同的 Api 封裝成產品的位置。 您也可以設定使用者存取、查看報表，以及設定配額或轉換的原則。

開發人員入口網站是開發人員的主要資源。 它可為開發人員提供 API 檔、互動式測試主控台，以及報表的使用方式。 開發人員也會使用入口網站來建立及管理自己的帳戶，包括訂用帳戶和 API 金鑰支援。

使用 APIM，應用程式可以公開數個不同的服務群組，每個群組都提供特定前端用戶端的後端。 針對複雜的案例，建議使用 APIM。 針對較簡單的需求，可以使用輕量 API 閘道 Ocelot。 EShopOnContainers 應用程式會使用 Ocelot，因為它的簡易性很簡單，因為它可以部署到與應用程式本身相同的應用程式環境中。 [深入瞭解 eShopOnContainers、APIM 和 Ocelot。](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#azure-api-management)

如果您的應用程式使用 AKS，另一個選項是將 Azure 閘道輸入控制器部署為 AKS 叢集中的 pod。 這可讓您的叢集與 Azure 應用程式閘道整合，讓閘道能夠對 AKS pod 的流量進行負載平衡。 [深入瞭解適用于 AKS 的 Azure 閘道輸入控制器](https://github.com/Azure/application-gateway-kubernetes-ingress)。

## <a name="data"></a>資料

EShopOnContainers 使用的各種後端服務具有不同的儲存體需求。 SQL Server 資料庫使用數種微服務。 購物籃微服務會利用 Redis 快取來持續保存。 微服務位置需要 MongoDB API 來作為其資料。 Azure 支援這些資料格式。

針對 SQL Server 資料庫支援，Azure 具有適用于單一資料庫的所有專案，最多可高度擴充的 SQL Database 彈性集區。 您可以設定個別微服務，快速且輕鬆地與自己的個別 SQL Server 資料庫進行通訊。 您可以視需要調整這些資料庫，以根據其需求來支援每個個別的微服務。

EShopOnContainers 應用程式會將使用者的目前購物籃儲存在要求之間。 這是由將資料儲存在 Redis 快取中的購物籃微服務所管理。 在開發期間，此快取可以部署在容器中，而在生產環境中，它可以利用 Azure Cache for Redis。 Azure Cache for Redis 是完全受控的服務，可提供高效能和可靠性，而不需要自行部署及管理 Redis 實例或容器。

位置微服務使用 MongoDB NoSQL 資料庫進行持續性。 在開發期間，可以將資料庫部署在自己的容器中，而在生產環境中，服務可以利用 [Azure Cosmos DB 的 MONGODB API](/azure/cosmos-db/mongodb-introduction)。 Azure Cosmos DB 的優點之一，就是能夠利用多種不同的通訊協定，包括 SQL API 和常見的 NoSQL Api，包括 MongoDB、Cassandra、Gremlin 和 Azure 資料表儲存體。 Azure Cosmos DB 提供完全受控且全域散發的資料庫即服務，可進行調整以符合使用它的服務需求。

[第5章](distributed-data.md)會詳細說明雲端原生應用程式中的分散式資料。

## <a name="event-bus"></a>事件匯流排

應用程式會使用事件來傳達不同服務之間的變更。 這項功能可以透過各種不同的執行方式來執行，而且在本機 eShopOnContainers 應用程式會使用 [RabbitMQ](https://www.rabbitmq.com/)。 裝載在 Azure 中時，應用程式會利用 [Azure 服務匯流排](/azure/service-bus/) 進行其訊息處理。 Azure 服務匯流排是完全受控的整合訊息代理程式，可讓應用程式和服務以低耦合、可靠、非同步方式彼此通訊。 Azure 服務匯流排支援個別佇列以及個別的 *主題* ，以支援發行者訂閱者案例。 EShopOnContainers 應用程式會利用 Azure 服務匯流排的主題，以支援將訊息從一個微服務散發到任何其他需要回應指定訊息的微服務。

## <a name="resiliency"></a>災害復原

一旦部署到生產環境之後，eShopOnContainers 應用程式就能夠利用數個可用的 Azure 服務來改善其復原能力。 應用程式會發佈健康狀態檢查，可與 Application Insights 整合，以根據應用程式的可用性提供報告和警示。 Azure 資源也提供診斷記錄，可用來找出並更正錯誤和效能問題。 資源記錄會提供應用程式使用不同 Azure 資源的時間和方式的詳細資訊。 您將在 [第6章](resiliency.md)中深入瞭解雲端原生復原功能。

>[!div class="step-by-step"]
>[上一個](introduce-eshoponcontainers-reference-app.md) 
>[下一步](deploy-eshoponcontainers-azure.md)
