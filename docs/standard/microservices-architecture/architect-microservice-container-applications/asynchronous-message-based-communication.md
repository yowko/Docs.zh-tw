---
title: 非同步訊息通訊
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 非同步訊息通訊
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: bee9a6215d2952f6c7f71607b1c4b1f44d1c0faf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-message-based-communication"></a>非同步訊息通訊

將變更傳播跨多個微服務和其相關的領域模型時，非同步傳訊和事件驅動通訊非常重要。 如微服務和繫結內容 (BC) 的討論中稍早所提及，模型 (使用者、客戶、產品、帳戶等) 對不同的微服務或 BC 可能代表不同的項目。 這表示發生變更時，您需要某種方式來協調不同模型之間的變更。 解決方案是最終一致性和根據非同步傳訊的事件驅動通訊。

當使用傳訊時，處理序會以非同步的方式交換訊息來進行通訊。 用戶端藉由傳送訊息給服務來對它提出命令或要求。 如果服務需要回覆，它會傳送不同的訊息回去給用戶端。 因為它是以訊息為基礎的通訊，用戶端假設不會立即收到回覆，而且可能完全沒有任何回應。

訊息由標頭 (例如識別或安全性資訊的中繼資料) 和主體所組成。 通常會透過像是 AMQP 的非同步通訊協定來傳送訊息。

在微服務社群中，這種通訊的慣用基礎結構是輕量級訊息代理程式，它不同於 SOA 中使用的大型訊息代理程式和協調器。 在輕量級訊息代理程式中，基礎結構通常「無聲」，僅當作訊息代理程式，並具有例如 RabbitMQ 的簡單實作，或是例如 Azure 服務匯流排的雲端可擴充服務匯流排。 在此案例中，大部分的「智慧型」思考仍存在於產生和取用訊息的端點，也就是微服務中。

另一項您應該盡可能嘗試遵循的規則，是在內部服務之間只使用非同步傳訊，而只有在從用戶端應用程式到前端服務 (API 閘道加上第一層的微服務) 使用同步通訊 (例如 HTTP)。

有兩種類型的非同步傳訊通訊：單一接收者訊息式通訊及多個接收者訊息式通訊。 在下面各節中，我們提供其詳細資料。

## <a name="single-receiver-message-based-communication"></a>單一接收者訊息式通訊 

與單一接收者的訊息式非同步通訊，表示有點對點通訊，將訊息傳遞至從通道讀取的取用者其中恰好一個，並且訊息只會處理一次。 不過，有特殊的情況。 例如，在嘗試自動從失敗復原的雲端系統中，相同的訊息可能會傳送多次。 由於網路或其他失敗，用戶端必須能夠重試傳送訊息，且伺服器必須將作業實作為等冪，以便只處理一次特定訊息。

單一接收者訊息式通訊特別適合從一個微服務傳送非同步命令到另一個微服務，如示範這個方法的圖 4-18 所示。

一旦您開始傳送訊息型通訊 (不論是透過命令或事件)，您應該避免混用訊息式通訊與同步 HTTP 通訊。

![](./media/image18.PNG)

**圖 4-18**. 接收非同步訊息的單一微服務

請注意，當命令來自用戶端應用程式時，它們可以實作為 HTTP 同步命令。 當您需要更高的延展性，或當您已經訊息式商務程序中時，您應該使用訊息式命令。

## <a name="multiple-receivers-message-based-communication"></a>多個接收者訊息式通訊 

作為更有彈性的方法，您也可以使用發行/訂閱機制，以便來自寄件者的通訊可供其他訂閱者微服務或外部應用程式使用。 因此，它可協助您遵循傳送服務中的[開啟/關閉準則 (Open/closed principle)](https://en.wikipedia.org/wiki/Open/closed_principle)。 這樣一來，未來不需要修改寄件者服務即可新增其他訂閱者。

當您使用發行/訂閱通訊時，您可能使用事件匯流排介面來將事件發行至任何訂閱者。

## <a name="asynchronous-event-driven-communication"></a>非同步事件驅動通訊

使用非同步事件驅動通訊時，微服務會在其領域中發生事情，而另一個微服務必須注意它時，發行整合事件，例如產品類別目錄微服務中的價格變更。 其他微服務會訂閱事件，因此它們可以用非同步方式收到事件。 發生這種情況時，接收者可能會更新他們自己的領域實體，這可能會造成有更多的整合事件要發行。 此發行/訂閱系統通常藉由使用事件匯流排實作來執行。 事件匯流排可設計為抽象或介面，並具備訂閱或取消訂閱事件以及發行事件所需的 API。 事件匯流排也可以有一或多個實作以任何處理序間及傳訊代理程式為基礎，例如支援非同步通訊和發行/訂閱模型的傳訊佇列或服務匯流排。

如果系統會使用由整合事件驅動的最終一致性，建議您讓終端使用者完全清楚這種方法。 系統不應該使用模擬整合事件的方法，例如 SignalR 或從用戶端輪詢系統。 終端使用者和企業擁有者必須明確擁抱系統中的最終一致性，並了解在許多情況下，企業使用這個方法時，只要它明確便不會有任何問題。

如同在[分散式資料管理的挑戰和解決方案](#challenges-and-solutions-for-distributed-data-management)小節中稍早所提，您可以使用整合事件來實作跨越多個微服務的商務工作。 因此，您在這些服務之間會有最終一致性。 最終一致的交易是由分散式動作的集合所組成。 在每個動作中，相關的微服務會更新領域實體，並發行另一個整合事件，在相同的端對端商務工作內引發下一個動作。

很重要的一點是，您可能想要傳達給訂閱相同事件訂閱的多個微服務。 若要這樣做，您可以根據事件驅動通訊，使用發行/訂閱傳訊，如圖 4-19 所示。 這個發行/訂閱機制不是微服務架構所獨有。 它是類似 DDD 中的[繫結內容](https://martinfowler.com/bliki/BoundedContext.html)的通訊方式，或是[命令和查詢責任隔離 (CQRS)](https://martinfowler.com/bliki/CQRS.html)架構模式中，您將更新寫入資料庫傳播到讀取資料庫的方式。 目標是在分散式系統的多個資料來源之間有最終一致性。

![](./media/image19.png)

**圖 4-19**. 非同步事件驅動訊息通訊

您的實作會決定要用於事件驅動、訊息式通訊的通訊協定。 [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) 可以協助達成可靠的佇列通訊。

當您使用事件匯流排時，可能會想要使用抽象層級 (例如事件匯流排介面)，其根據類別中的相關實作，且程式碼使用來自像是 [RabbitMQ](https://www.rabbitmq.com/) 之訊息代理程式的 API，或使用像是 [Azure 服務匯流排與主題](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)的服務匯流排。 或者，您也可以使用較高層級的服務匯流排，像是 NServiceBus、MassTransit 或 Brighter 來相互連貫事件匯流排和發佈/訂閱系統。

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>關於生產系統傳訊技術的附註

適用於實作抽象事件匯流排的傳訊技術是在不同層級。 例如，像是 RabbitMQ (一種傳訊訊息代理程式傳輸) 和 Azure 服務匯流排的產品，所在的層級便比其他產品低，例如 NServiceBus、MassTransit 或 Brighter，它們可以在 RabbitMQ 和 Azure 服務匯流排之上運作。 您的選擇取決於您的應用程式需要多少功能和現成的延展性。 針對只為您的開發環境實作概念證明事件匯流排，如同我們在 eShopOnContainers 範例所做的事，在 Docker 容器上執行的 RabbitMQ 上進行簡單實作可能就足夠了。

但對於需要高延展性的關鍵任務和生產系統，您可能想要評估 Azure 服務匯流排。 對於可讓您更輕鬆地開發分散式應用程式的高階抽象和功能，我們建議您評估其他商業和開放原始碼服務匯流排，例如 NServiceBus、 MassTransit 和 Brighter。 當然，您可以在像是 RabbitMQ 和 Docker 的較低層級技術之上自行建立服務匯流排功能。 但是，那樣的配管工作對於自訂企業應用程式而言成本可能太高。

## <a name="resiliently-publishing-to-the-event-bus"></a>彈性地發行到事件匯流排

跨多個微服務實作事件驅動架構時，有一項挑戰是如何以不可分割方式更新原始微服務的狀態，同時以某種方式，根據交易彈性地將其相關整合事件發行到事件匯流排。 以下幾種方式可以達成此目的，雖然可能也有其他的方法。

-   使用像昃 MSMQ 的交易式 (DTC 型) 佇列。 (不過，這是傳統方法。)

-   使用[交易記錄採礦](https://www.scoop.it/t/sql-server-transaction-log-mining)。

-   使用完整的[事件溯源模式](https://msdn.microsoft.com/library/dn589792.aspx)。

-   使用[寄件匣模式](http://gistlabs.com/2014/05/the-outbox/)：交易式資料庫資料表作為訊息佇列，而訊息佇列將是事件建立者元件的基礎，會建立事件加以發行。

使用非同步通訊時要考慮的其他主題還有訊息等冪及訊息重複資料刪除。 這些主題將在本指南稍後的[實作微服務之間的事件通訊 (整合事件)](#implementing_event_based_comms_microserv)小節討論。

## <a name="additional-resources"></a>其他資源

-   **事件驅動訊息**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **發佈/訂閱頻道**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Udi Dahan.已釐清的 CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **命令與查詢職責分離 (CQRS)**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **已繫結內容之間的通訊**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **最終一致性**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard：重構朝向彈性：評估結合程度**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[上一頁] (communication-in-microservice-architecture.md) [下一頁] (maintain-microservice-apis.md)
