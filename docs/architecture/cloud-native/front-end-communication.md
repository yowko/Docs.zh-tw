---
title: 前端用戶端通訊
description: 瞭解前端用戶端如何與雲端原生系統通訊
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 147adb3d0375f8bf5dadf14e1237aa93e9e42908
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158106"
---
# <a name="front-end-client-communication"></a>前端用戶端通訊

在雲端原生系統中，前端用戶端 (行動裝置、web 和桌面應用程式) 需要通道與獨立的後端微服務互動。  

請問有哪些選項？

為了簡單起見，前端用戶端可以直接與後端微服務 *通訊* ，如圖4-2 所示。

![直接用戶端對服務的通訊](./media/direct-client-to-service-communication.png)

**圖4-2。** 直接用戶端對服務的通訊

使用此方法時，每個微服務都有前端用戶端可存取的公用端點。 在生產環境中，您會將負載平衡器放在微服務前面，並依比例路由傳送流量。

雖然簡單明瞭，但只有簡單的微服務應用程式可以接受直接用戶端通訊。 此模式會將前端用戶端緊密結合到核心後端服務，為一些問題開啟大門，包括：

- 對後端服務重構的用戶端敏感。
- 因為核心後端服務會直接公開，所以會有更廣泛的攻擊面。
- 跨每個微服務的跨領域考慮重複。
- 過於複雜的用戶端程式代碼-用戶端必須持續追蹤多個端點，並以彈性的方式處理失敗。

相反地，廣泛接受的雲端設計模式是在前端應用程式與後端服務之間執行 [API 閘道服務](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) 。 圖4-3 顯示此模式。

![API 閘道模式](./media/api-gateway-pattern.png)

**圖4-3。** API 閘道模式

在上圖中，請注意 API 閘道服務如何抽象化後端核心微服務。 會實作為 web API，作為 *反向 proxy*，將連入流量路由傳送至內部微服務。

閘道會將用戶端與內部服務資料分割和重構隔離。 如果您變更後端服務，您就可以在閘道中容納它，而不會中斷用戶端。 這也是您的第一道防線，可進行跨領域考慮，例如身分識別、快取、復原、計量和節流。 許多這些跨領域考慮都可以從後端核心服務關閉到閘道，簡化後端服務。

務必小心讓 API 閘道保持簡單且快速。 一般而言，商務邏輯會保留在閘道之外。 複雜的閘道會造成瓶頸，最後成為單體本身的風險。 較大型的系統通常會公開多個 API 閘道，並依用戶端類型 (行動、web、桌面) 或後端功能來分割。 前端模式的 [後端](/azure/architecture/patterns/backends-for-frontends) 提供執行多個閘道的方向。 圖4-4 顯示此模式。

![API 閘道模式](./media/backend-for-frontend-pattern.png)

**圖4-4。** 前端模式的後端

請注意，在上圖中，連入流量會根據用戶端類型傳送至特定的 API 閘道： web、行動或桌面應用程式。 這種方法的意義在於每個裝置的功能在外型規格、效能和顯示限制之間有顯著的差異。 行動應用程式通常會公開比瀏覽器或桌面應用程式更少的功能。 每個閘道都可以進行優化，以符合對應裝置的功能和功能。

若要開始，您可以建立自己的 API 閘道服務。 GitHub 的快速搜尋將提供許多範例。 不過，有數個架構和商用閘道產品可供使用。

## <a name="ocelot-gateway"></a>Ocelot 閘道

針對簡單的 .NET 雲端原生應用程式，您可以考慮 [Ocelot 閘道](https://github.com/ThreeMammals/Ocelot)。 Ocelot 是針對 .NET 微服務所建立的開放原始碼 API 閘道，其系統需要統一的進入點。 它是輕量、快速、可擴充的。

如同任何 API 閘道，其主要功能是將傳入的 HTTP 要求轉送到下游服務。 此外，它支援各種可在 .NET Core 中介軟體管線中設定的功能。 下表提供其功能集。

|Ocelot 功能  | |
| :-------- | :-------- |
| 路由 | 驗證 |
| 要求匯總 | 授權 |
| 使用 Consul 和 Eureka) 的服務探索 ( | 節流 |
| 負載平衡 | 記錄，追蹤 |
| Caching | 標頭/查詢字串轉換 |
| 相互關聯傳遞 | 自訂中介軟體 |
| 服務品質 | 重試原則 |

每個 Ocelot 閘道會指定 JSON 設定檔中的上游和下游位址，以及可設定的功能。 用戶端會將 HTTP 要求傳送至 Ocelot 閘道。 收到後，Ocelot 會透過其管線傳遞 HttpRequest 物件，並將它操作為其設定所指定的狀態。 在管線結束時，Ocelot 會建立新的 HTTPResponseObject，並將它傳遞至下游服務。 針對回應，Ocelot 會反轉管線，並將回應傳回給用戶端。

Ocelot 是以 NuGet 套件的形式提供。 它以 NET Standard 2.0 為目標，使其與 .NET Core 2.0 + 和 .NET Framework 4.6.1 + 執行時間相容。 Ocelot 與在 .NET Core 支援的平臺（Linux、macOS 和 Windows）上演講的任何內容整合。 Ocelot 可延伸，並支援許多新式平臺，包括 Docker 容器、Azure Kubernetes 服務或其他公用雲端。  Ocelot 與 [Consul](https://www.consul.io)、 [GraphQL](https://graphql.org)和 Netflix [Eureka](https://github.com/Netflix/eureka)等開放原始碼套件整合。

針對不需要商用 API 閘道豐富功能集的簡單雲端原生應用程式，請考慮 Ocelot。

## <a name="azure-application-gateway"></a>Azure 應用程式閘道

針對簡單的閘道需求，您可以考慮 [Azure 應用程式閘道](/azure/application-gateway/overview)。 以 Azure [PaaS 服務](https://azure.microsoft.com/overview/what-is-paas/)的形式提供，包括 URL 路由、SSL 終止及 Web 應用程式防火牆等基本閘道功能。 此服務支援 [第7層負載平衡](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) 功能。 使用第7層時，您可以根據 HTTP 訊息的實際內容（而不只是低層級的 TCP 網路封包）來路由傳送要求。

在本書中，我們宣導將雲端原生系統裝載于 [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html)中。 容器協調器 Kubernetes 可將容器化工作負載的部署、規模調整和操作考慮自動化。 Azure 應用程式閘道可設定為 [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) 叢集的 API 閘道。

[應用程式閘道輸入控制器](https://azure.github.io/application-gateway-kubernetes-ingress/)可讓 Azure 應用程式閘道直接使用[Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/)。 圖4.5 顯示架構。

![應用程式閘道輸入控制器](./media/application-gateway-ingress-controller.png)

**圖4-5。** 應用程式閘道輸入控制器

Kubernetes 包含內建功能，可支援 HTTP (層級 7) 負載平衡 [，稱為輸入](https://kubernetes.io/docs/concepts/services-networking/ingress/)。 輸入會定義一組規則，以說明如何將 AKS 內的微服務實例公開給外界。 在上圖中，輸入控制器會解讀針對叢集所設定的輸入規則，並自動設定 Azure 應用程式閘道。 應用程式閘道會根據這些規則，將流量路由傳送至在 AKS 內執行的微服務。 輸入控制器會接聽輸入規則的變更，並對 Azure 應用程式閘道進行適當的變更。

## <a name="azure-api-management"></a>Azure API 管理

針對適中到大規模的雲端原生系統，您可以考慮 [AZURE API 管理](https://azure.microsoft.com/services/api-management/)。 它是一種雲端式服務，不僅可解決您的 API 閘道需求，還提供功能完整的開發人員和系統管理體驗。 [圖 4-6] 顯示 API 管理。

![Azure API 管理](./media/azure-api-management.png)

**圖4-6。** Azure API 管理

若要開始，API 管理會根據可設定的規則和原則，公開允許對後端服務進行控制存取的閘道伺服器。 這些服務可以位於 Azure 雲端、您的內部內部部署資料中心或其他公用雲端。 API 金鑰和 JWT 權杖可決定誰可以做什麼。 記錄所有流量，以供分析之用。

針對開發人員，API 管理提供開發人員入口網站，可讓您存取服務、檔和叫用的範例程式碼。 開發人員可以使用 Swagger/Open API 來檢查服務端點並分析其使用方式。 此服務可跨主要開發平臺運作： .NET、JAVA、Golang 等等。

發行者入口網站會公開管理儀表板，讓系統管理員公開 Api 並管理其行為。 您可以授與服務存取、監視服務健康狀態，以及收集服務遙測。 系統管理員會將 *原則* 套用至每個端點，以影響行為。 [原則](/azure/api-management/api-management-howto-policies) 是針對每個服務呼叫循序執行的預先建立語句。  原則會針對輸入呼叫、輸出呼叫，或在發生錯誤時叫用。 原則可以套用至不同的服務範圍，以在結合原則時啟用決定性的排序。 產品隨附許多預先建立的 [原則](/azure/api-management/api-management-policies)。

以下是原則如何影響您的雲端原生服務行為的範例：  

- 限制服務存取。
- 強制執行驗證。  
- 如有必要，將來自單一來源的呼叫節流。
- 啟用快取。
- 封鎖來自特定 IP 位址的呼叫。
- 控制服務的流程。
- 將要求從 SOAP 轉換成 REST 或不同的資料格式，例如從 XML 轉換成 JSON。

Azure API 管理可以公開裝載于任何位置的後端服務，無論是在雲端或您的資料中心。 針對您可能會在雲端原生系統中公開的舊版服務，它同時支援 REST 和 SOAP Api。 即使是其他 Azure 服務也可以透過 API 管理來公開。 您可以將受控 API 放在 Azure 支援服務的最上層，例如 [Azure 服務匯流排](https://azure.microsoft.com/services/service-bus/) 或 [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/)。 Azure API 管理不包含內建的負載平衡支援，而且應該搭配負載平衡服務使用。

Azure API 管理可跨 [四個不同的層級](https://azure.microsoft.com/pricing/details/api-management/)使用：

- 開發人員
- 基本
- 標準
- Premium

開發人員層適用于非生產工作負載和評估。 另一層提供更多的電源、功能及更高的服務等級協定， (Sla) 。 Premium 層提供 [Azure 虛擬網路](/azure/virtual-network/virtual-networks-overview) 和 [多區域支援](/azure/api-management/api-management-howto-deploy-multi-region)。 所有層都有固定的每小時價格。

Azure 雲端也提供 Azure API 管理的 [無伺服器層](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) 。 這項服務稱為 *耗用量定價層*，其為以無伺服器運算模型為目的而設計的 API 管理變異。 與先前所顯示的「預先配置」定價層不同的是，使用量層提供立即布建和依動作付費的定價。

它會針對下列使用案例啟用 API 閘道功能：

- 微服務使用無伺服器技術（例如 [Azure Functions](/azure/azure-functions/functions-overview) 和 [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/)）來執行。
- Azure 支援服務資源，例如服務匯流排佇列和主題、Azure 儲存體和其他資源。
- 微服務，其中的流量偶爾會有大量尖峰，但在大部分的時間都保持不變。

使用量層會使用相同的基礎服務 API 管理元件，但會根據動態配置的資源來採用完全不同的架構。 它完美地與無伺服器運算模型一致：

- 沒有可管理的基礎結構。
- 無閒置容量。
- 高可用性。
- 自動調整。
- 成本是根據實際的使用量。
  
新的耗用量層對於將無伺服器資源公開為 Api 的雲端原生系統而言，是絕佳的選擇。

## <a name="real-time-communication"></a>即時通訊

即時或推播的通訊是前端應用程式的另一個選項，可透過 HTTP 與後端雲端原生系統進行通訊。 應用程式（例如財務、線上教育、遊戲和作業進度更新）需要來自後端的即時回應。 使用一般 HTTP 通訊時，用戶端無法知道有新資料可用的時機。 用戶端必須持續 *輪詢* 或將要求傳送至伺服器。 使用 *即時* 通訊，伺服器隨時都可以將新資料推送至用戶端。

即時系統通常是以高頻率的資料流程，以及大量的並行用戶端連接來表徵。 手動執行即時連線可能很快就會變得很複雜，需要非一般的基礎結構，以確保可調整規模且可靠地傳遞至連線的用戶端。 您可以找到自己管理 Azure Redis 快取實例，以及一組針對用戶端親和性會話設定的負載平衡器。

[Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/) 是完全受控的 Azure 服務，可簡化雲端原生應用程式的即時通訊。 容量布建、調整和持續連線等技術實行詳細資料會被抽象化。 系統會為您處理99.9% 服務等級協定的程式。 您將焦點放在應用程式功能，而不是基礎結構切換。

啟用之後，雲端式 HTTP 服務可以將內容更新直接推送至連線的用戶端，包括瀏覽器、行動裝置和桌面應用程式。 用戶端會在不需要輪詢伺服器的情況下進行更新。 Azure SignalR 會將建立即時連接的傳輸技術抽象化，包括 Websocket、伺服器端事件和長時間輪詢。 開發人員著重于將訊息傳送至所有或特定的連線用戶端子集。

圖4-7 顯示一組 HTTP 用戶端，連接到已啟用 Azure SignalR 的雲端原生應用程式。

![Azure SignalR](./media/azure-signalr-service.png)

**圖4-7。** Azure SignalR

Azure SignalR Service 的另一個優點是執行無伺服器的雲端原生服務。 或許您的程式碼會隨 Azure Functions 觸發程式隨選執行。 這種情況可能很棘手，因為您的程式碼不會維持與用戶端的長時間連接。 Azure SignalR 服務可以處理這種情況，因為該服務已經為您管理連線。

Azure SignalR Service 緊密整合其他 Azure 服務（例如 Azure SQL Database、服務匯流排或 Redis 快取），可為您的雲端原生應用程式開啟許多可能性。

>[!div class="step-by-step"]
>[上一個](communication-patterns.md) 
>[下一步](service-to-service-communication.md)
