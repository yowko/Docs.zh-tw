---
title: "在微服務架構中的通訊"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |微服務架構架構中的通訊"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8d38095a151b7568619b17340d768eff684d3271
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="communication-in-a-microservice-architecture"></a>在微服務架構中的通訊

在整合的應用程式，在單一處理序上執行，元件叫用另一個使用語言層級方法或函式呼叫。 這些可以強結合如果您使用程式碼建立物件 (例如， `new ClassName()`)，可以予以解除解合的方式呼叫，如果您正在使用相依性插入參考的抽象概念，而不是具象的物件執行個體。 無論如何，相同的程序內執行的物件。 變更從 microservices 架構的應用程式整合的應用程式時，最大的挑戰在於變更的溝通機制。 直接轉換成服務的 RPC 呼叫的同處理序的方法呼叫從會導致多對話，並不會也在執行的通訊效率不分散式環境。 正確設計分散式的系統的挑戰夠好已知還有稱為 canon[分散式運算 fallacies](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)其中列出開發人員通常會從移動時的假設分散式設計整合。

沒有不一種解決方案，但是數個。 一個解決方法包括隔離商務 microservices 盡量。 然後使用內部 microservices 之間的非同步通訊，並取代一般的粗粒通訊物件之間的內部處理序通訊的更細緻通訊。 您可以分組為呼叫，並藉由傳回彙總結果的多個內部呼叫，用戶端的資料。

Microservices 為基礎的應用程式是在多個處理程序或服務，通常甚至跨多個伺服器或主機上執行的分散式的系統。 每個服務執行個體通常是處理程序。 因此，服務必須使用的處理序間的通訊協定，例如 HTTP、 AMQP 或例如 TCP、 根據每個服務的本質的二進位通訊協定互動。

微服務社群升級的原理"[智慧型端點和無聲管道](http://simplicable.com/new/smart-endpoints-and-dumb-pipes)。 」 此標語鼓勵為分離盡可能之間 microservices，且為結合盡可能在單一的微服務內的設計。 如前所述，每個微服務擁有它自己的資料和它自己網域的邏輯。 但 microservices 撰寫的端對端應用程式通常只會經過使用 REST 通訊，而不是複雜的通訊協定，例如 WS-\*與彈性事件導向的通訊，而不是集中式商務程序 orchestrators。

兩個常用的通訊協定為 HTTP 要求/回應與資源應用程式開發介面 （查詢最重要的是） 時，和跨多個 microservices 輕量型非同步傳訊通訊時更新。 這些會在下列各節中詳細說明。

## <a name="communication-types"></a>通訊類型

用戶端和服務可以透過許多不同類型的通訊，以不同的案例與目標為目標的每個進行通訊。 一開始，這些類型的通訊可以分類在兩個軸。

如果同步或非同步通訊協定，定義的第一個軸：

-   同步通訊協定。 HTTP 是同步的通訊協定。 用戶端傳送要求，並等候來自服務的回應。 這是獨立用戶端程式碼執行，可能是同步的 （封鎖的執行緒） 或非同步 （不封鎖執行緒，和回應會最後到達回呼）。 此處的重點是通訊協定 (HTTP/HTTPS) 是同步，並收到 HTTP 伺服器回應時，用戶端程式碼才可以繼續其工作。

-   非同步通訊協定。 其他通訊協定，如 AMQP （許多作業系統和雲端環境所支援的通訊協定） 使用非同步的訊息。 用戶端程式碼或訊息寄件者通常不會等待回應。 傳送訊息給 RabbitMQ 佇列或任何其他訊息代理程式時，它只會傳送訊息。

第二個軸定義為單一接收者或多個接收者通訊是否：

-   單一接收者。 每個要求必須剛好只有一個收件者或服務所處理。 舉例來說，此通訊是[命令模式](https://en.wikipedia.org/wiki/Command_pattern)。

-   多個接收者。 每個要求可以處理除以零到多個接收者。 這種類型必須是通訊的非同步的。 範例是[發佈/訂閱](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern)類似的模式中使用的機制[事件驅動的架構](http://microservices.io/patterns/data/event-driven-architecture.html)。 這根據事件匯流排的介面或訊息代理程式時傳播事件，透過多個 microservices 之間的資料更新它通常透過 service bus 或類似的成品，例如實作[Azure 服務匯流排](https://azure.microsoft.com/services/service-bus/)使用[主題和訂閱](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)。

微服務為基礎的應用程式通常會使用這些通訊樣式的組合。 叫用一般的 Web API HTTP 服務時，最常見的類型會是單一接收者同步的通訊協定，例如 HTTP/HTTPS 通訊。 Microservices 通常也會使用訊息通訊協定 microservices 之間的非同步通訊。

這些軸適合知道，以便清楚說明對可能的通訊機制，但它們不是建置 microservices 時重要的考量。 整合 microservices 時，所選通訊協定的用戶端執行緒執行甚至非同步本質的非同步本質是重點。 什麼*是*重要能夠整合您 microservices 以非同步方式同時維護的獨立性 microservices 下, 一節中所述。

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>非同步的微服務整合會強制微服務的自主性

如所述，建置 microservices 為基礎的應用程式時很重要的一點是您整合您 microservices 的方式。 在理想情況下，您應該嘗試最小化內部 microservices 之間的通訊。 較少之間的通訊 microservices，愈好。 但是，在許多情況下您必須以某種方式整合 microservices。 當您需要執行此作業時，重要的規則是 microservices 之間的通訊，應該是非同步。 這不代表您必須使用特定的通訊協定 （例如，非同步訊息與同步 HTTP）。 它只是表示應該只由以非同步方式將資料傳播 microservices 之間的通訊，但不是嘗試相依於其他內部 microservices，做為初始服務的 HTTP 要求/回應作業的一部分。

可能的話，請永遠不會相依於多個 microservices，甚至不能用於查詢之間的同步通訊 （要求/回應）。 每個微服務的目標是希望自發並可供用戶端取用者，即使的端對端應用程式一部分的其他服務都關機或狀況不良。 如果您認為您需要進行其他 microservices （例如，執行 HTTP 要求的資料查詢） 從一個微服務呼叫中，以便能夠提供回應給用戶端應用程式，您必須將無法復原某些架構microservices 失敗。

此外，具有 HTTP microservices 的圖 4-15 中的第一個部分中所示，使用 HTTP 要求/回應循環建立長時要求鏈結，例如之間的相依性不只會使您 microservices 不自發，但其效能也是影響，因為其中一個該鏈結中的服務未在順利執行。 

您增加 microservices，例如查詢要求之間的同步相依性，更糟的整體回應時間取得用戶端應用程式。

![](./media/image15.png)

**圖 4-15**。 反向模式和 microservices 之間的通訊模式

如果您的微服務需要引發另一個的微服務的其他動作，可能的話，不要執行該動作以同步和做為原始的微服務要求與回覆作業的一部分。 請改為以非同步方式執行 （使用非同步傳訊或整合事件、 佇列，等）。 但是，盡可能，不會叫用的動作，以同步方式做為原始的同步要求與回覆作業的一部分。

最後再 （而且這是建置 microservices 時的大部份問題會發生），如果您初始的微服務需要原本由其他 microservices 所擁有的資料時，請勿依賴提出同步要求，該資料。 相反地，複製或資料 （只有您所需的屬性） 傳播到起始服務的資料庫，最終一致性 （通常使用透過整合事件幾節中所述）。

如前文所述的區段中[識別每個微服務的網域模型界限](#identifying-domain-model-boundaries-for-each-microservice)，在數個 microservices 之間複製某些資料不是設計不正確，相反地，當您可以將資料轉譯到特定語言或其他網域或繫結內容的條款。 例如，在[eShopOnContainers](http://aka.ms/MicroservicesArchitecture)應用程式具有名為具有名為使用者的實體，負責大部分的使用者資料的 identity.api 微服務。 不過，當您需要儲存訂購微服務中使用者相關資料，您將它儲存為不同的實體，名為買方。 買方實體與原始使用者實體中，共用相同的識別，但它可能只有幾個屬性所需的訂購網域，並不完整的使用者設定檔。

您可以使用任何通訊協定來進行通訊，並散佈資料以非同步方式 microservices 才能擁有最終一致性。 如前所述，您可以使用整合事件使用事件匯流排或 broker，或甚至還可以使用 HTTP 透過改用輪詢其他服務的訊息。 並不重要。 重要的規則，就會建立同步您 microservices 之間的相依性。

下列各節說明您可以考慮在微服務應用程式中使用多個通訊樣式。

## <a name="communication-styles"></a>通訊樣式

有許多通訊協定和通訊，視您想要使用的通訊類型而定，您可以使用的選項。 如果您使用的同步要求/回應為基礎的通訊機制，通訊協定，例如 HTTP 和 REST 的方式是最常見的特別是當您發行您的 Docker 主機 」 或 「 微服務叢集外的服務。 如果您在內部 （在您的 Docker 主機或 microservices 叢集） 的服務之間通訊您也可以使用二進位格式 （例如 Service Fabric 遠端服務或 WCF 使用 TCP 和二進位格式） 的通訊機制。 或者，您可以使用以訊息為基礎的非同步通訊機制，例如 AMQP。

也有多個訊息格式，如 JSON 或 XML 或甚至二進位格式，可能會更有效率。 如果您選擇的二進位格式不是一種標準，可能不是個不錯的主意公開發行您的服務使用該格式。 您可以在您 microservices 之間的內部通訊使用非標準格式。 Microservices Docker 主機 」 或 「 微服務叢集 （Docker orchestrators 或 Azure Service Fabric） 內或向 microservices 的專屬的用戶端應用程式之間進行通訊時，您可以這樣做。

### <a name="requestresponse-communication-with-http-and-rest"></a>透過 HTTP 和 REST 要求/回應通訊 

當用戶端會使用要求/回應通訊時，它會將要求傳送至服務，然後服務處理程序要求，並將回應傳回。 要求/回應通訊非常特別適合從用戶端應用程式的即時 UI （即時的使用者介面） 的查詢資料。 因此，在微服務架構中您可能會使用此通訊機制對於大部分查詢而言示圖 4-16。

![](./media/image16.png)

**圖 4-16**。 使用 HTTP 要求/回應通訊 （同步或非同步）

當用戶端會使用要求/回應通訊時，它會假設，回應會到達一段時間，通常少於一秒或幾秒鐘的時間最多。 對於回應延遲，您需要實作基礎的非同步通訊[傳訊模式](https://docs.microsoft.com/azure/architecture/patterns/category/messaging)和[傳訊技術](https://en.wikipedia.org/wiki/Message-oriented_middleware)，這是我們在下一節說明不同的方法。

要求/回應通訊的熱門架構樣式是[REST](https://en.wikipedia.org/wiki/Representational_state_transfer)。 這種方法為基礎，而緊密結合， [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)通訊協定，採用 HTTP 動詞命令，例如 GET、 POST 和 PUT。 建立服務時，其餘部分會是最常用架構的通訊方法。 當您開發 ASP.NET Core Web API 服務時，您可以實作 REST 服務。

為您的介面定義語言中使用 HTTP 的 REST 服務時，沒有其他的值。 比方說，如果您使用[Swagger 中繼資料](http://swagger.io/)來描述服務 API，您可以使用工具，可產生用戶端 stub，可以直接探索及取用您的服務。

### <a name="additional-resources"></a>其他資源

-   **Martin Fowler：Richardson Maturity Model。** 其他模型的描述。
    [*http://martinfowler.com/articles/richardsonMaturityModel.html*](http://martinfowler.com/articles/richardsonMaturityModel.html)

-   **Swagger。** 官方網站。
    [*http://swagger.io/*](http://swagger.io/)

### <a name="push-and-real-time-communication-based-on-http"></a>發送和 HTTP 為基礎的通訊

（通常是供不同比其餘部分） 的另一個可能性是較高層級架構與即時和一對多通訊例如[ASP.NET SignalR](https://www.asp.net/signalr)和通訊協定例如[WebSockets](https://en.wikipedia.org/wiki/WebSocket)。

如圖 4-17 所示，即時 HTTP 訊息表示您可以將內容推送至連線的用戶端，當資料可用，而不是需要等候用戶端要求新的資料在伺服器的伺服端程式碼。

![](./media/image17.png)

**圖 4-17**。 一對一即時的非同步訊息通訊

由於即時通訊，用戶端應用程式幾乎會立即顯示變更。 這通常被處理通訊協定，例如 WebSockets，使用許多 Websocket 連線 （用戶端每一個）。 典型的範例時，同時服務通訊的許多用戶端 web 應用程式在運動遊戲的分數中相符的變更。


>[!div class="step-by-step"]
[上一個](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) [下一步] (非同步的訊息為基礎-communication.md)
