---
title: 前端用戶端通訊
description: 瞭解前端用戶端如何與雲端原生系統通訊
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: 67410bf9b5c76acc472018197bb64aa7662dc439
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183123"
---
# <a name="front-end-client-communication"></a>前端用戶端通訊

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在雲端原生系統中，前端用戶端（行動裝置、web 和桌面應用程式）需要通道，才能與獨立的後端微服務互動。  

選項有哪些？

為了簡單起見，前端用戶端可以直接與後端微服務*通訊*，如圖4-2 所示。

![直接用戶端對服務的通訊](./media/direct-client-to-service-communication.png)

**圖 4-2.** 直接用戶端對服務的通訊

使用此方法時，每個微服務都有一個可由前端用戶端存取的公用端點。 在生產環境中，您會將負載平衡器放在微服務的前方，以按比例路由傳送流量。

雖然簡單的執行，但只有簡單的微服務應用程式可接受直接用戶端通訊。 此模式會將前端用戶端與核心後端服務緊密結合，針對許多問題開啟門，包括：

- 用戶端對後端服務重構的敏感程度。
- 隨著核心後端服務直接公開，會有更大的受攻擊面。
- 每個微服務的跨領域考慮重複。
- 過於複雜的用戶端程式代碼-用戶端必須追蹤多個端點，並以彈性的方式處理失敗。

相反地，廣為接受的雲端設計模式是在前端應用程式與後端服務之間執行[API 閘道服務](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)。 模式如圖4-3 所示。

![API 閘道模式](./media/api-gateway-pattern.png)

**圖4-3。** API 閘道模式

在上圖中，請注意 API 閘道服務如何抽象化後端核心微服務。 實作為 Web API，它會作為*反向 proxy*，將連入流量路由傳送至內部微服務。 

閘道會將用戶端與內部服務分割和重構隔離。 如果您變更後端服務，您可以在閘道上容納它，而不會中斷用戶端。 這也是您跨領域考慮的第一道防線，例如身分識別、快取、復原、計量和節流。 許多跨領域關注都可以從後端核心服務關閉到閘道，簡化後端服務。

請務必小心，讓 API 閘道保持簡單且快速。 一般而言，商務邏輯會保留在閘道外。 複雜的閘道風險成為瓶頸，最後是單體本身。 較大的系統通常會公開多個以用戶端類型（行動、web、桌面）或後端功能分割的 API 閘道。 前端模式的[後端](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends)提供了執行多個閘道的方向。 模式如圖4-4 所示。

![API 閘道模式](./media/backend-for-frontend-pattern.png)

**圖4-4。** 前端模式的後端

請注意，上圖中的連入流量如何根據用戶端類型（web、行動或桌面應用程式）傳送至特定 API 閘道。 這種方法很合理，因為每個裝置的功能在外型規格、效能和顯示限制方面都有顯著的差異。 行動應用程式通常會比瀏覽器或桌面應用程式公開較少的功能。 每個閘道都可以進行優化，以符合對應裝置的功能和功能。

若要開始，您可以建立自己的 API 閘道服務。 GitHub 的快速搜尋將提供許多範例。 不過，有數個架構和商業網關產品可供使用。

## <a name="ocelot-gateway"></a>Ocelot 閘道

針對簡單的 .NET 雲端原生應用程式，您可以考慮[Ocelot 閘道](https://github.com/ThreeMammals/Ocelot)。 Ocelot 是針對 .NET 微服務所建立的開放原始碼 API 閘道，需要在其系統中整合進入點。 它是輕量、快速、可調整的。 

就像任何 API 閘道，其主要功能是將傳入的 HTTP 要求轉送到下游服務。 此外，它也支援可在 .NET Core 中介軟體管線中設定的各種功能。 下表提供其功能集。

|Ocelot 功能  | |
| :-------- | :-------- |
| 路由 | 驗證 |
| 要求匯總 | 授權 |
| 服務探索（使用 Consul 和 Eureka） | 節流 |
| 負載平衡 | 記錄，追蹤 |
| 快取 | 標頭/查詢字串轉換 |
| 相互關聯傳遞 | 自訂中介軟體 |
| 服務品質 | 重試原則 |

每個 Ocelot 閘道都會在 JSON 設定檔中指定上游和下游位址，以及可設定的功能。 用戶端會將 HTTP 要求傳送至 Ocelot 閘道。 一旦收到，Ocelot 會透過其管線將 HttpRequest 物件傳遞至其設定所指定的狀態。 在管線的結尾，Ocelot 會建立新的 HTTPResponseObject，並將它傳遞至下游服務。 針對回應，Ocelot 會反轉管線，並將回應傳回給用戶端。

Ocelot 是以 NuGet 套件的形式提供。 其以 NET Standard 2.0 為目標，使其與 .NET Core 2.0 + 和 .NET Framework 4.6.1 + 執行時間相容。 Ocelot 與在 .NET Core 支援的平臺上說出 HTTP 並執行的任何專案整合：Linux、macOS 和 Windows。 Ocelot 是可擴充的，可支援許多現代化平臺，包括 Docker 容器、Azure Kubernetes Services 或其他公用雲端。  Ocelot 整合了開放原始碼套件，例如[Consul](https://www.consul.io)、 [GraphQL](https://graphql.org)和 Netflix 的[Eureka](https://github.com/Netflix/eureka)。 

針對不需要商用 API 閘道豐富功能集的簡單雲端原生應用程式，請考慮使用 Ocelot。

## <a name="azure-application-gateway"></a>Azure 應用程式閘道

針對簡單的閘道需求，您可以考慮[Azure 應用程式閘道](https://docs.microsoft.com/azure/application-gateway/overview)。 以 Azure [PaaS 服務](https://azure.microsoft.com/overview/what-is-paas/)的形式提供，其中包含基本的閘道功能，例如 URL 路由、SSL 終止和 Web 應用程式防火牆。 此服務支援[第7層負載平衡](https://www.nginx.com/resources/glossary/layer-7-load-balancing/)功能。 有了第7層，您可以根據 HTTP 訊息的實際內容來路由傳送要求，而不只是低層級的 TCP 網路封包。 

在本書中，我們宣導了在[Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html)中裝載雲端原生系統的功能。 容器協調器，Kubernetes 會將容器化工作負載的部署、調整和操作方面的顧慮自動化。 Azure 應用程式閘道可以設定為[Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/)叢集的 API 閘道。

[應用程式閘道輸入控制器](https://azure.github.io/application-gateway-kubernetes-ingress/)可讓 Azure 應用程式閘道直接與[Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/)搭配使用。 圖4.5 顯示架構。

![應用程式閘道輸入控制器](./media/application-gateway-ingress-controller.png)

**圖4-5。** 應用程式閘道輸入控制器

Kubernetes 包含支援 HTTP （層級7）負載平衡的內建功能[，稱為「](https://kubernetes.io/docs/concepts/services-networking/ingress/)輸入」。 輸入會定義一組規則，以說明如何將 AKS 內的微服務實例公開給外部世界。 在上一個映射中，輸入控制器會解讀為叢集設定的輸入規則，並自動設定 Azure 應用程式閘道。 根據這些規則，應用程式閘道會將流量路由傳送至在 AKS 內執行的微服務。 輸入控制器會接聽輸入規則的變更，並對 Azure 應用程式閘道進行適當的變更。

## <a name="azure-api-management"></a>Azure API 管理

針對適中到大規模的雲端原生系統，您可以考慮[AZURE API 管理](https://azure.microsoft.com/services/api-management/)。 這是一種雲端式服務，不僅能解決您的 API 閘道需求，還提供功能完整的開發人員和系統管理體驗。 API 管理如圖4-6 所示。 

![Azure API 管理](./media/azure-api-management.png)

**圖4-6。** Azure API 管理

若要開始，API 管理會公開閘道伺服器，讓您可以根據可設定的規則和原則來控制後端服務的存取權。 這些服務可以在 Azure 雲端、您的內部內部部署資料中心或其他公用雲端中。 API 金鑰和 JWT 權杖會決定誰可以執行哪些動作。 記錄所有流量以供分析之用。 

對於開發人員而言，API 管理提供開發人員入口網站，可讓您存取服務、檔和用來叫用它們的範例程式碼。 開發人員可以使用 Swagger/Open API 來檢查服務端點，並分析其使用方式。 此服務可跨主要開發平臺運作： .NET、JAVA、Golang 等等。 

發行者入口網站會公開管理儀表板，其中系統管理員會公開 Api 並管理其行為。 可以授與服務存取權、監視服務健全狀況，以及收集服務遙測。 系統管理員會將*原則*套用至每個端點，以影響行為。 [原則](https://docs.microsoft.com/azure/api-management/api-management-howto-policies)是預先建立的語句，會針對每個服務呼叫循序執行。  原則會針對輸入呼叫、輸出呼叫或在發生錯誤時叫用。 原則可以套用至不同的服務範圍，以在結合原則時啟用決定性順序。 產品隨附許多預先建立的[原則](https://docs.microsoft.com/azure/api-management/api-management-policies)。 

以下範例說明原則會如何影響您的雲端原生服務的行為：  

- 限制服務存取。
- 強制執行驗證。  
- 視需要從單一來源節流呼叫。
- 啟用快取。
- 封鎖來自特定 IP 位址的呼叫。
- 控制服務的流程。
- 將要求從 SOAP 轉換成 REST，或在不同的資料格式之間（例如從 XML 到 JSON）。

Azure API 管理可以公開裝載于任何位置的後端服務–在雲端或您的資料中心。 針對您可能會在雲端原生系統中公開的舊版服務，它同時支援 REST 和 SOAP Api。 即使是其他 Azure 服務也可以透過 API 管理來公開。 您可以將受控 API 放在 Azure 支援服務上，例如[Azure 服務匯流排](https://azure.microsoft.com/services/service-bus/)或[Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/)。 Azure API 管理不包含內建的負載平衡支援，應與負載平衡服務搭配使用。

Azure API 管理可跨[四個不同層級](https://azure.microsoft.com/pricing/details/api-management/)提供：

- 開發人員
- 基本
- 標準
- 溢價

開發人員層適用于非生產工作負載和評估。 另一層則提供更多的電源、功能和更高的服務等級協定（Sla）。 高階層提供[Azure 虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)和[多區域支援](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region)。 所有層都有每小時固定的價格。 

Microsoft 最近宣佈了 Azure API 管理的[API 管理無伺服器層](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/)。 所謂的「取用」*定價層*，服務是以無伺服器運算模型為中心設計之 API 管理的變異。 不同于先前所顯示的「預先配置」定價層，取用層提供立即布建和按動作付費的定價。

它會啟用下列使用案例的 API 閘道功能：

- 微服務使用無伺服器技術（例如[Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)和[Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/)）來實行。
- Azure 支援的服務資源，例如服務匯流排佇列和主題、Azure 儲存體等。
- 微服務，其中的流量偶爾會發生大量的尖峰，但大部分的時間都保持不變。 

取用層會使用相同的基礎服務 API 管理元件，但是會根據動態配置的資源來採用完全不同的架構。 它完美地配合無伺服器運算模型：

- 沒有可管理的基礎結構。
- 沒有閒置容量。
- 高可用性。
- 自動調整。
- 成本是以實際使用量為基礎。 
  
新的耗用量層是雲端原生系統的絕佳選擇，會將無伺服器資源公開為 Api。 

> 在撰寫本文時，取用層會在 Azure 雲端中處於預覽狀態。

## <a name="real-time-communication"></a>即時通訊

對於透過 HTTP 與後端雲端原生系統進行通訊的前端應用程式，即時或推播是另一個選項。 應用程式（例如，金融部門、線上教育、遊戲和作業進度更新）需要來自後端的瞬間、即時回應。 使用一般 HTTP 通訊時，用戶端無法得知何時可以使用新資料。 用戶端必須持續*輪詢*或傳送要求到伺服器。 使用*即時*通訊時，伺服器可以隨時將新資料推送至用戶端。 

即時系統通常是以高頻率的資料流程和大量的並行用戶端連線為特色。 手動執行即時連線可能很快就會變得複雜，而需要非一般的基礎結構，以確保連線用戶端的擴充性和可靠的訊息。 您可以自行管理 Azure Redis 快取的實例，以及一組以用戶端親和性的粘滯會話設定的負載平衡器。 

[Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/)是完全受控的 Azure 服務，可為您的雲端原生應用程式簡化即時通訊。 如容量布建、調整和持續連線等技術執行詳細資料，將會被抽象化。 系統會為您處理 99.9% 服務等級協定。 您將焦點放在應用程式功能，而不是基礎結構的管道。 

啟用之後，雲端式 HTTP 服務就可以直接將內容更新推送至連線的用戶端，包括瀏覽器、行動和桌面應用程式。 用戶端會在不需要輪詢伺服器的情況下進行更新。 Azure SignalR 會將建立即時連線的傳輸技術抽象化，包括 Websocket、伺服器端事件和長時間輪詢。 開發人員著重于將訊息傳送至已連線用戶端的所有或特定子集。

圖4-7 顯示一組 HTTP 用戶端，其連線至已啟用 Azure SignalR 的雲端原生應用程式。

![Azure SignalR](./media/azure-signalr-service.png)

**圖4-7。** Azure SignalR

Azure SignalR Service 的另一個優點是執行無伺服器雲端原生服務。 您的程式碼可能會隨 Azure Functions 的觸發程式隨選執行。 此案例可能會很棘手，因為您的程式碼不會維護與用戶端的長時間連接。 Azure SignalR Service 可以處理這種情況，因為服務已經為您管理連接。

Azure SignalR Service 與其他 Azure 服務（例如 Azure SQL Database、服務匯流排或 Redis 快取）緊密整合，為您的雲端原生應用程式開啟許多可能性。

>[!div class="step-by-step"]
>[上一頁](communication-patterns.md)
>[下一頁](service-to-service-communication.md)
