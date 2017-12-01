---
title: "非同步訊息架構通訊"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |非同步訊息架構通訊"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df39771295d12e122edbe27e91cd899e3318e301
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="asynchronous-message-based-communication"></a>非同步訊息架構通訊

將變更傳播跨多個 microservices 和其相關的網域模型時，非同步傳訊和事件導向通訊非常重要。 如稍早討論 microservices 和繫結的內容 (BCs) 中所述，（使用者、 客戶、 產品、 帳戶等） 的模型可能代表不同 microservices 或 BCs 不同的項目。 這表示發生變更時，您需要某種方式來協調不同的模型之間的變更。 解決方案是最終一致性和事件導向的通訊，根據非同步訊息。

當使用訊息，處理序進行通訊所交換訊息，以非同步的方式。 用戶端命令或為要求的服務傳送訊息。 如果服務需要回覆，它會傳送回用戶端不同的訊息。 因為它是以訊息為基礎的通訊，用戶端會假設不會在立即收到回覆，而且可能會有任何回應完全。

訊息的組成方式 （例如識別或安全性資訊的中繼資料） 的標頭和主體。 通常會透過 AMQP 像非同步通訊協定來傳送訊息。

慣用的基礎結構，這種類型的 microservices 社群中是通訊的輕量級的訊息仲介，不同於大型仲介和 orchestrators SOA 中使用。 輕量級的訊息代理人在基礎結構是通常"無聲，「 僅當做訊息仲介，與簡單的實作，例如 RabbitMQ 或可擴充服務匯流排等 Azure 服務匯流排雲端。 在此案例中，大部分的 「 智慧型 」 思考仍存留在所產生和取用訊息的端點，也就是 microservices 中。

您應該嘗試執行，盡可能，另一項規則會使用唯一的非同步訊息之間的內部服務，以及使用同步通訊 （例如 HTTP) 只會從用戶端應用程式 （API 閘道加上第一層的前端服務microservices)。

有兩種類型的訊息的非同步通訊： 單一接收者訊息架構通訊及多個接收者訊息架構通訊。 下列各節中，我們會提供其相關詳細資料。

## <a name="single-receiver-message-based-communication"></a>單一接收者訊息架構通訊 

訊息架構與單一接收者的非同步通訊表示將訊息傳遞至其中一個，會讀取通道中，和一次處理訊息的取用者的點對點通訊。 不過，有特殊的情況。 例如，嘗試自動從失敗復原的雲端系統，相同的訊息無法多次傳送。 由於網路或其他失敗，用戶端必須能夠重試傳送訊息，且伺服器實作為等冪，才能處理特定訊息就可以一次作業。

單一接收者訊息架構通訊特別適合從一個微服務的非同步命令傳送到另一個顯示在圖 4-18，將示範這個方法。

一旦您開始傳送訊息型通訊 （不論是透過命令或事件），您應該避免混用訊息為基礎的同步 HTTP 通訊的通訊。

![](./media/image18.PNG)

**圖 4-18**。 單一的微服務，接收非同步的訊息

請注意，當命令來自用戶端應用程式，它們可以實作為 HTTP 同步命令。 當您需要更高的延展性，或當您已經在處理訊息為基礎的商務程序，您應該使用訊息為基礎的命令。

## <a name="multiple-receivers-message-based-communication"></a>多個接收者訊息架構通訊 

為更有彈性的方法，您也可以使用的發佈/訂閱機制，以便您寄件者的通訊可使用其他訂閱者 microservices 或外部應用程式。 因此，它可協助您遵循[開啟/關閉原則](https://en.wikipedia.org/wiki/Open/closed_principle)中傳送的服務。 這樣一來，而不需要修改寄件者服務未來可以加入其他 「 訂閱者 」。

當您使用發行/訂閱的通訊時，您可能使用事件匯流排介面發行至任何訂閱者的事件。

## <a name="asynchronous-event-driven-communication"></a>事件驅動的非同步通訊

使用事件驅動的非同步通訊，微服務會發行整合時的事件發生在其網域中，因此必須注意，例如產品類別目錄微服務的價格變更另一個的微服務。 其他 microservices 訂閱事件，讓它們以非同步方式接收。 當發生這種情況時，接收者可能會更新他們自己網域的實體，而造成更多的整合事件發行。 此發行/訂閱系統通常會執行所使用的事件匯流排實作。 事件匯流排都可以設計成做為抽象或介面，以訂閱或取消訂閱事件並發行事件所需的 API。 事件匯流排也可以有一個或多個實作根據任何處理序間和傳訊的 broker，像是訊息佇列或服務匯流排支援非同步通訊和發佈/訂閱模型。

如果系統會使用由整合事件驅動的最終一致性，建議您使用這種方法進行完全清除終端使用者。 系統不應該使用的模擬整合事件，例如 SignalR 或從用戶端的輪詢系統的方法。 終端使用者，而業務擁有者必須明確面向系統中的最終一致性，並請注意，在許多情況下企業不需要使用這個方法時，任何問題，只要明確。

如同稍早在所註明[挑戰和解決方案的分散式資料管理](#challenges-and-solutions-for-distributed-data-management) 區段中，您可以使用整合事件來實作跨越多個 microservices 商務工作。 因此，您會有這些服務之間的最終一致性。 最終一致性的交易是由分散式的動作集合所組成。 在每個動作中，相關的微服務會更新網域實體，並將發佈中相同的端對端商務工作的下一個動作所引發的另一個整合事件。

很重要的一點是您可能想要傳達給相同的事件訂閱的多個 microservices。 若要這樣做，您可以使用發行/訂閱傳訊根據事件導向的通訊，如圖 4-19 所示。 這個發行/訂閱機制不是獨占微服務架構的。 它是類似的方式[繫結內容](http://martinfowler.com/bliki/BoundedContext.html)中應該要能傳達 DDD，或您將傳播的方式寫入資料庫中的讀取資料庫的更新[命令和查詢責任隔離 (CQRS)](http://martinfowler.com/bliki/CQRS.html)架構模式。 目標是透過分散式系統的多個資料來源之間有最終一致性。

![](./media/image19.png)

**圖 4-19**。 非同步事件驅動的訊息通訊

您的實作會決定要用於事件導向、 訊息架構通訊的通訊協定。 [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)可以協助您達成可靠的佇列的通訊。

當您使用事件匯流排時，可能會想要使用的抽象層級 （例如事件匯流排介面） 根據具有所使用的訊息代理程式，例如從 API 的程式碼的相關類別中實作[RabbitMQ](https://www.rabbitmq.com/)或服務匯流排像[Azure 服務匯流排主題](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)。 或者，您可以使用較高層級的服務匯流排，像是 NServiceBus、 MassTransit 或 Brighter 表達事件匯流排和發佈/訂閱系統。

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>關於訊息對生產系統技術附註

適用於實作抽象事件匯流排傳訊的技術是在不同層級。 例如，產品，例如 RabbitMQ （傳訊 broker 傳輸） 和 Azure Service Bus 坐比其他產品，例如、 NServiceBus、 MassTransit 或 Brighter RabbitMQ 和 Azure 服務匯流排可以處理較低層級。 您的選擇取決於應用程式層級和應用程式所需的方塊超出延展性多少豐富的功能。 實作只針對您的開發環境的概念證明事件匯流排，我們已經在 eShopOnContainers 範例中，在 Docker 容器上執行的 RabbitMQ 之上的簡單實作可能會不夠。

不過，對於關鍵任務和實際執行系統上需要 hyper-v 延展性，您可能想要評估 Azure 服務匯流排。 高階的抽象概念和功能，可讓您更輕鬆的分散式應用程式開發，我們建議您評估其他商業和開放原始碼的服務匯流排，例如 NServiceBus、 MassTransit 和 Brighter。 當然，您可以建立服務匯流排功能，在這類 RabbitMQ 和 Docker 的較低層級技術之上。 但是，該配管工作可能成本太多自訂企業應用程式。

## <a name="resiliently-publishing-to-the-event-bus"></a>事件匯流排照顧發佈

跨多個 microservices 實作的事件驅動的架構時，一項挑戰是如何以不可分割方式更新，同時照顧在其相關的整合事件發佈至事件匯流排，以某種方式根據原始的微服務中的狀態交易。 如下幾種方式可以達成此目的，雖然可能會有額外的方法。

-   使用 MSMQ 類似交易 （DTC 型） 佇列。 （不過，這是傳統方法）。

-   使用[交易記錄採礦](http://www.scoop.it/t/sql-server-transaction-log-mining)。

-   使用完整[事件來源](https://msdn.microsoft.com/en-us/library/dn589792.aspx)模式。

-   使用[寄件匣模式](http://gistlabs.com/2014/05/the-outbox/)： 將會建立事件，並將它發行的事件建立者元件的基底的訊息佇列為交易式資料庫資料表。

使用非同步通訊時要考慮的其他主題是訊息等冪及訊息重複資料刪除。 這些主題的章節將討論[實作事件架構 microservices （整合事件） 之間的通訊](#implementing_event_based_comms_microserv)本指南稍後的。

## <a name="additional-resources"></a>其他資源

-   **事件驅動訊息**
    [*http://soapatterns.org/design\_模式/事件\_驅動\_傳訊*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **發佈/訂閱通道**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Udi Dahan。已釐清 CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **命令和查詢責任隔離 (CQRS)**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **之間通訊的繫結內容**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **最終一致性**
    [*https://en.wikipedia.org/wiki/Eventual\_一致性*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard：重構朝向彈性： 評估結合**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[上一個](通訊層中的微服務-architecture.md) [下一步] (維護的微服務-apis.md)
