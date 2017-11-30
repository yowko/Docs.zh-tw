---
title: "實作事件架構 microservices （整合事件） 之間的通訊"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作事件架構 microservices （整合事件） 之間的通訊"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e438607ab3549d63b89bef6af64c6723a4cac950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>實作事件架構 microservices （整合事件） 之間的通訊

如前所述，當您使用以事件為基礎的通訊時，微服務會發行事件時值得注意的項目，例如，它會更新的商務實體。 其他 microservices 訂閱這些事件。 當微服務收到事件時，它可以更新自己商務實體，可能會導致更多的事件發行。 此發行/訂閱系統通常會執行所使用的事件匯流排實作。 事件匯流排可設計為介面訂閱及取消訂閱事件，並將事件發行所需的 API。 它也可以有任何處理序間或郵件通訊，例如訊息佇列或服務匯流排支援非同步通訊和發佈/訂閱模型為基礎的一或多個實作。

您可以使用事件來實作商務交易橫跨多個服務，它將提供這些服務之間的最終一致性。 最終一致性的交易是由一系列的分散式動作所組成。 每個動作，在微服務更新的商務實體，並發行事件的觸發程序的下一個動作。

![](./media/image19.PNG)

**圖 8-18**。 事件導向的通訊，根據事件匯流排

本章節描述如何實作這種類型的.NET 與通訊，以及在使用一般事件匯流排介面，如圖 8-18 所示。 有多個可能的實作，每個使用不同的技術或基礎結構，例如 RabbitMQ、 Azure 服務匯流排，或任何其他第三方開放原始碼或商業服務匯流排。

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>訊息仲介和服務匯流排用於生產系統

架構 > 一節所述，您可以選擇從多個訊息的技術，實作抽象事件匯流排。 但是，這些技術都是在不同層級。 例如，RabbitMQ，訊息的 broker 傳輸，會比等 Azure 服務匯流排、 NServiceBus、 MassTransit 或 Brighter 商業產品的較低層級。 大部分的這些產品可以 RabbitMQ 或 Azure 服務匯流排的最上方工作。 您所選擇的產品取決於如何許多功能和多少--現成的延展性，您需要應用程式。

實作只事件匯流排的概念證明您的開發環境，如同 eShopOnContainers 範例中，執行做為容器 RabbitMQ 之上的簡單實作可能會就足夠了。 但為關鍵任務而且需要高延展性的生產系統，您可能想要評估，並使用 Azure Service Fabric。 如果您需要高階的抽象概念，而且更豐富的功能類似[sagas](https://docs.particular.net/nservicebus/sagas/)長時間執行之處理序的更簡單、 商業和開放原始碼的服務匯流排 NServiceBus，MassTransit，例如，讓分散式的開發和Brighter 是值得評估。 當然，您一律可以建置自己 RabbitMQ 和 Docker，這類的較低層級技術的服務匯流排功能，但造所需的工作可能是自訂的企業應用程式的成本太高。

重申： 範例事件匯流排的抽象概念，其中顯示 eShopOnContainers 範例中的實作適用於僅做概念證明。 一旦您決定您想要有非同步處理和事件導向通訊，本節所述，您應該選擇最符合您需求的服務匯流排產品。

## <a name="integration-events"></a>整合事件

整合事件用來將跨多個 microservices 或外部系統的網域狀態同步。 這是發行整合事件以外的微服務。 當事件發佈到多個接收者 microservices （若要盡可能 microservices 會整合事件訂閱) 時，每個接收者微服務中的適當的事件處理常式會處理事件。

整合事件基本上是保存資料之類別，如下列範例所示：

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

整合事件類別可以很簡單;例如，它可能包含 GUID 的識別碼

整合事件可以定義應用程式層級的每個微服務，讓它們彼此分離其他 microservices，相當於 ViewModels 中伺服器和用戶端的定義方式的方式。 不建議跨多個 microservices; 共用通用的整合事件程式庫這麼做可就會結合這些 microservices 與單一事件定義資料程式庫。 您不想要這樣做，基於相同理由，您不想在多個 microservices 之間共用通用的網域模型： microservices 必須是完全自主。

有只有幾種不同的程式庫，您應該在 microservices 共用。 其中一個是程式庫最終的應用程式區塊，例如[事件匯流排用戶端 API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)，而在 eShopOnContainers 中。 另一個是程式庫的構成也無法共用為 NuGet 元件，例如 JSON 序列化程式的工具。

## <a name="the-event-bus"></a>事件匯流排

事件匯流排 」 可讓發行/訂閱樣式 microservices 而不需要明確留意，如圖 8-19 所示的元件之間的通訊。

![](./media/image20.png)

**圖 8-19**。 發佈/訂閱與事件匯流排的基本概念

事件匯流排與觀察器模式及發行-訂閱模式。

### <a name="observer-pattern"></a>觀察器模式

在[觀察器模式](https://en.wikipedia.org/wiki/Observer_pattern)，主要物件 （稱為 Observable） （事件） 的相關資訊通知其他想要的物件 （稱為 「 觀察者而定）。

### <a name="publish-subscribe-pubsub-pattern"></a>發行-訂閱 (Pub/Sub) 模式 

目的[Pub/Sub 模式](https://msdn.microsoft.com/en-us/library/ff649664.aspx)觀察器模式與相同： 您想要特定事件發生時通知其他服務。 但有一項重要之間的觀察者和 Pub/Sub 模式語意差異。 Pub/Sub 模式中，重點是在將訊息廣播。 相反地，在觀察器模式中，Observable 不知道誰事件會移至，就是這已經出。換句話說，可觀察 （發行者） 不知道屬於觀察者 （「 訂閱者 」）。

### <a name="the-middleman-or-event-bus"></a>Middleman 或事件匯流排 

您要如何達到發行者和訂閱者之間的匿名？ 簡單的方法是讓 middleman，負責處理的所有通訊。 事件匯流排是一個這類 middleman。

事件匯流排通常是由兩個部分組成：

-   抽象或介面。

-   一或多個實作。

圖 8-19 您可以查看如何從應用程式的觀點，事件匯流排只不過是 Pub/Sub 通道。 實作這個非同步通訊的方式而有所不同。 因此，您可以根據環境需求 （例如，開發環境與生產） 而定的兩者之間交換，它可能有多個實作。

圖 8-20 您可以看到事件匯流排的抽象概念，以根據傳訊 RabbitMQ、 Azure 服務匯流排或其他的服務匯流排類似 NServiceBus、 MassTransit 等這類技術的基礎結構的多個實作。

![](./media/image21.png)

**圖 8-20。** 事件匯流排的多個實作

不過，以反白顯示之前，使用 （事件匯流排介面） 的抽象概念是可能只有在必須支援您的抽象概念的基本事件匯流排功能。 如果您需要更豐富的服務匯流排功能，您應該使用您慣用的服務匯流排，而不是您自己的抽象提供的 API。

### <a name="defining-an-event-bus-interface"></a>定義事件匯流排介面

讓我們開始某些事件匯流排介面的實作程式碼與可能的實作進行探索。 泛型和簡單，如同下列介面，應該是介面。

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);
    void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T: IntegrationEvent;

    void Unsubscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent;
}
```

發行方法相當簡單。 事件匯流排會廣播整合事件傳遞給它，該事件訂閱任何微服務。 這個方法會使用此事件發行微服務。

Subscribe 方法會使用 microservices 想要接收事件。 這個方法有兩個部分。 第一個是整合的事件訂閱 (IntegrationEvent)。 第二個部分是整合事件處理常式 （或回呼方法） 呼叫 (IIntegrationEventHandler&lt;T&gt;) 當微服務收到事件訊息的整合。


>[!div class="step-by-step"]
[上一個](資料庫的伺服器-container.md) [下一步] (rabbitmq-event-bus-development-test-environment.md)
