---
title: 實作微服務之間的事件通訊 (整合事件)
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作微服務之間的事件通訊 (整合事件)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 5d8ba76caab39db222c2ceba36a4d67cab3e8a3f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105790"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>實作微服務之間的事件通訊 (整合事件)

如前所述，當您使用事件通訊時，微服務會在發生值得注意的事件時發行事件，例如當它更新商務實體時。 其他微服務會訂閱這些事件。 當微服務收到事件時，它可以更新自己的商務實體，這可能會導致發行更多的事件。 此發行/訂閱系統通常藉由使用事件匯流排實作來執行。 事件匯流排可設計為介面，並具備訂閱及取消訂閱事件以及發行事件所需的 API。 它也可以有一或多個實作以任何處理序間或傳訊通訊為基礎，例如支援非同步通訊和發行/訂閱模型的傳訊佇列或服務匯流排。

您可以使用事件來實作橫跨多個服務的商務交易，這樣將提供這些服務之間的最終一致性。 最終一致的交易是由一系列的分散式動作所組成。 在每個動作中，微服務會更新商務實體，並發行觸發下一個動作的事件。

![](./media/image19.PNG)

**圖 8-18**. 以事件匯流排為基礎的事件驅動通訊

本節描述如何使用一般事件匯流排介面來實作這種類型的 .NET 通訊，如圖 8-18 所示。 有多種可能的實作，每一種都使用不同的技術或基礎結構，例如 RabbitMQ、Azure 服務匯流排，或任何其他第三方開放原始碼或商業服務匯流排。

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>對於生產環境使用訊息代理程式和服務匯流

如架構一節所述，您可以從多種傳訊技術選擇，以便實作抽象事件匯流排。 但是，這些技術都是在不同層級。 例如，RabbitMQ 是傳訊代理程式傳輸，它的層級比例如 Azure 服務匯流排、NServiceBus、MassTransit 或 Brighter 等商業產品低。 大部分的這些產品可以在 RabbitMQ 或 Azure 服務匯流排上工作。 您所選擇的產品取決於您的應用程式需要多少功能和多少現成的延展性。

針對只為您的開發環境實作事件匯流排的概念證明，如同 eShopOnContainers 範例，在執行作為容器的 RabbitMQ 上進行簡單實作可能就足夠了。 但對於需要高延展性的關鍵任務和生產系統，您可能想要評估，並使用 Azure 服務匯流排。

如果您的長時間執行處理序需要高階抽象，以及更豐富的功能，例如 [Sagas](https://docs.particular.net/nservicebus/sagas/)，以便讓分散式開發更容易，則其他商業和開放原始碼的服務匯流排，例如 NServiceBus、MassTransit 和 Brighter 都值得評估。 在此案例中，要使用的抽象和 API 通常會直接由這些高階服務匯流排提供，而不是您自己的抽象 (例如 [eShopOnContainers 所提供的簡單事件匯流排抽象](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs))。 就此而言，您可以研究[使用 NServiceBus 的分支 eShopOnContainers](http://go.particular.net/eShopOnContainers) (Particular Software 所實作的其他衍生範例)

當然，您一律可以在較低階技術 (例如 RabbitMQ 和 Docker) 上建置自己的服務匯流排功能，但是「重新發明車輪」所需的工作對於自訂企業應用程式而言可能成本太高。

## <a name="integration-events"></a>整合事件

整合事件用來讓跨多個微服務或外部系統的領域狀態同步。 這是藉由在微服務以外發行整合事件而達成。 當事件發行到多個接收者微服務時 (微服務的數量為訂閱整合事件的微服務數量)，每個接收者微服務中的適當事件處理常式會處理事件。

整合事件基本上是保存資料的類別，如下列範例所示：

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

整合事件可以在每個微服務的應用程式層級定義，讓它們與其他微服務彼此分離，相當於伺服器和用戶端中的 ViewModel 定義方式。 不建議的作法是跨多個微服務共用通用的整合事件程式庫；這麼做會將這些微服務與單一事件定義資料程式庫結合。 您不會想要這樣做，原因就相同於您不會想要在多個微服務之間共用通用的領域模型：微服務必須是完全自主。

只有幾種程式庫是您應該在微服務之間共用的。 其中一種是最終應用程式區塊的程式庫，例如[事件匯流排用戶端 API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)，如同在 eShopOnContainers 中。 另一種是構成工具的程式庫，它們也可以共用為 NuGet 元件，例如 JSON 序列化程式。

## <a name="the-event-bus"></a>事件匯流排

事件匯流排允許微服務之間的發行/訂閱樣式通訊，而不需要元件明確知道彼此，如圖 8-19 所示。

![](./media/image20.png)

**圖 8-19**. 事件匯流排的發行/訂閱基本概念

事件匯流排與觀察者模式及發行-訂閱模式有關。

### <a name="observer-pattern"></a>觀察者模式

在[觀察者模式](https://en.wikipedia.org/wiki/Observer_pattern)中，您的主要物件 (稱為可預見物件) 會將相關資訊 (事件) 通知其他有興趣的物件 (稱為觀察者)。

### <a name="publish-subscribe-pubsub-pattern"></a>發行-訂閱 (Pub/Sub) 模式 

[Pub/Sub 模式](https://msdn.microsoft.com/library/ff649664.aspx)的目的與觀察者模式相同：您想要在特定事件發生時通知其他服務。 但觀察者和 Pub/Sub 模式之間有一項重要的差異。 在觀察者模式中，廣播是直接從可預見物件對觀察者執行，讓他們「知道」彼此。 但在使用 Pub/Sub 模式時，有一個稱為代理程式或訊息代理程式或事件匯流排的第三個元件，發行者和訂閱者都知道它。 因此，在使用 Pub/Sub 模式時，發行者和訂閱者會因為提及的事件匯流排或訊息代理程式而精確地分離。

### <a name="the-middleman-or-event-bus"></a>中間人或事件匯流排 

您要如何達到發行者和訂閱者之間的匿名？ 簡單的方法是讓中間人負責處理所有通訊。 事件匯流排便是一個這類的中間人。

事件匯流排通常是由兩個部分組成：

-   抽象或介面。

-   一或多個實作。

在圖 8-19 中，您可以看到，從應用程式的觀點而言，事件匯流排只不過是 Pub/Sub 通道。 實作這個非同步通訊的方式可能有所不同。 它可能有多種實作，因此您可以根據環境需求 (例如，生產與開發環境)，在兩者之間交換。

在圖 8-20 中，您可以看到事件匯流排的抽象，且具有根據基礎結構傳訊技術，例如 RabbitMQ、Azure 服務匯流排或其他事件/訊息代理程式的多個實作。 

![](./media/image21.png)

**圖 8- 20.** 事件匯流排的多個實作

不過，如先前所提及，使用您自己的抽象 (事件匯流排介面) 只適合在您必須抽象所支援的基本事件匯流排功能時。 如果您需要更豐富的服務匯流排功能，可能應該使用您慣用的商業服務匯流排所提供的 API 和抽象，而不是自己的抽象。 

### <a name="defining-an-event-bus-interface"></a>定義事件匯流排介面

讓我們從一些事件匯流排介面的實作程式碼，以及探索用途的可能實作開始。 介面應該是泛型且簡單，如同下列介面。

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

`Publish` 方法很直接明瞭。 事件匯流排會將傳遞給它的整合事件，廣播到任何微服務或甚至是訂閱該事件的外部應用程式。 這個方法由發行事件的微服務所使用。

`Subscribe` 方法 (您可以有根據引數而定的數種實作) 是由想要收到事件的微服務所使用。 這個方法有兩個引數。 第一個是要訂閱的整合事件 (`IntegrationEvent`)。 第二個引數是整合事件處理常式 (或回呼方法)，名為 `IIntegrationEventHandler<T>`，且將在接收者微服務取得該整合事件訊息時執行。


>[!div class="step-by-step"]
[上一頁](database-server-container.md)
[下一頁](rabbitmq-event-bus-development-test-environment.md)
