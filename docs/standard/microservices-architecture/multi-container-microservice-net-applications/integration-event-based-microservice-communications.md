---
title: "實作微服務之間的事件通訊 (整合事件)"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 實作微服務之間的事件通訊 (整合事件)"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 50ab0be6b92304eee4bc46643c867ee2827fc805
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a><span data-ttu-id="ac6e6-104">實作微服務之間的事件通訊 (整合事件)</span><span class="sxs-lookup"><span data-stu-id="ac6e6-104">Implementing event-based communication between microservices (integration events)</span></span>

<span data-ttu-id="ac6e6-105">如前所述，當您使用事件通訊時，微服務會在發生值得注意的事件時發行事件，例如當它更新商務實體時。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-105">As described earlier, when you use event-based communication, a microservice publishes an event when something notable happens, such as when it updates a business entity.</span></span> <span data-ttu-id="ac6e6-106">其他微服務會訂閱這些事件。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-106">Other microservices subscribe to those events.</span></span> <span data-ttu-id="ac6e6-107">當微服務收到事件時，它可以更新自己的商務實體，這可能會導致發行更多的事件。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-107">When a microservice receives an event, it can update its own business entities, which might lead to more events being published.</span></span> <span data-ttu-id="ac6e6-108">此發行/訂閱系統通常藉由使用事件匯流排實作來執行。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-108">This publish/subscribe system is usually performed by using an implementation of an event bus.</span></span> <span data-ttu-id="ac6e6-109">事件匯流排可設計為介面，並具備訂閱及取消訂閱事件以及發行事件所需的 API。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-109">The event bus can be designed as an interface with the API needed to subscribe and unsubscribe to events and to publish events.</span></span> <span data-ttu-id="ac6e6-110">它也可以有一或多個實作以任何處理序間或傳訊通訊為基礎，例如支援非同步通訊和發行/訂閱模型的傳訊佇列或服務匯流排。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-110">It can also have one or more implementations based on any inter-process or messaging communication, such as a messaging queue or a service bus that supports asynchronous communication and a publish/subscribe model.</span></span>

<span data-ttu-id="ac6e6-111">您可以使用事件來實作橫跨多個服務的商務交易，這樣將提供這些服務之間的最終一致性。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-111">You can use events to implement business transactions that span multiple services, which gives you eventual consistency between those services.</span></span> <span data-ttu-id="ac6e6-112">最終一致的交易是由一系列的分散式動作所組成。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-112">An eventually consistent transaction consists of a series of distributed actions.</span></span> <span data-ttu-id="ac6e6-113">在每個動作中，微服務會更新商務實體，並發行觸發下一個動作的事件。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-113">At each action, the microservice updates a business entity and publishes an event that triggers the next action.</span></span>

![](./media/image19.PNG)

<span data-ttu-id="ac6e6-114">**圖 8-18**.</span><span class="sxs-lookup"><span data-stu-id="ac6e6-114">**Figure 8-18**.</span></span> <span data-ttu-id="ac6e6-115">以事件匯流排為基礎的事件驅動通訊</span><span class="sxs-lookup"><span data-stu-id="ac6e6-115">Event-driven communication based on an event bus</span></span>

<span data-ttu-id="ac6e6-116">本節描述如何使用一般事件匯流排介面來實作這種類型的 .NET 通訊，如圖 8-18 所示。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-116">This section describes how you can implement this type of communication with .NET by using a generic event bus interface, as shown in Figure 8-18.</span></span> <span data-ttu-id="ac6e6-117">有多種可能的實作，每一種都使用不同的技術或基礎結構，例如 RabbitMQ、Azure 服務匯流排，或任何其他第三方開放原始碼或商業服務匯流排。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-117">There are multiple potential implementations, each using a different technology or infrastructure such as RabbitMQ, Azure Service Bus, or any other third-party open source or commercial service bus.</span></span>

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a><span data-ttu-id="ac6e6-118">對於生產環境使用訊息代理程式和服務匯流</span><span class="sxs-lookup"><span data-stu-id="ac6e6-118">Using message brokers and services buses for production systems</span></span>

<span data-ttu-id="ac6e6-119">如架構一節所述，您可以從多種傳訊技術選擇，以便實作抽象事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-119">As noted in the architecture section, you can choose from multiple messaging technologies for implementing your abstract event bus.</span></span> <span data-ttu-id="ac6e6-120">但是，這些技術都是在不同層級。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-120">But these technologies are at different levels.</span></span> <span data-ttu-id="ac6e6-121">例如，RabbitMQ 是傳訊代理程式傳輸，它的層級比例如 Azure 服務匯流排、NServiceBus、MassTransit 或 Brighter 等商業產品低。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-121">For instance, RabbitMQ, a messaging broker transport, is at a lower level than commercial products like Azure Service Bus, NServiceBus, MassTransit, or Brighter.</span></span> <span data-ttu-id="ac6e6-122">大部分的這些產品可以在 RabbitMQ 或 Azure 服務匯流排上工作。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-122">Most of these products can work on top of either RabbitMQ or Azure Service Bus.</span></span> <span data-ttu-id="ac6e6-123">您所選擇的產品取決於您的應用程式需要多少功能和多少現成的延展性。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-123">Your choice of product depends on how many features and how much out-of-the-box scalability you need for your application.</span></span>

<span data-ttu-id="ac6e6-124">針對只為您的開發環境實作事件匯流排的概念證明，如同 eShopOnContainers 範例，在執行作為容器的 RabbitMQ 上進行簡單實作可能就足夠了。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-124">For implementing just an event bus proof-of-concept for your development environment, as in the eShopOnContainers sample, a simple implementation on top of RabbitMQ running as a container might be enough.</span></span> <span data-ttu-id="ac6e6-125">但對於需要高延展性的關鍵任務和生產系統，您可能想要評估，並使用 Azure 服務匯流排。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-125">But for mission-critical and production systems that need high scalability, you might want to evaluate and use Azure Service Bus.</span></span>

<span data-ttu-id="ac6e6-126">如果您的長時間執行處理序需要高階抽象，以及更豐富的功能，例如 [Sagas](https://docs.particular.net/nservicebus/sagas/)，以便讓分散式開發更容易，則其他商業和開放原始碼的服務匯流排，例如 NServiceBus、MassTransit 和 Brighter 都值得評估。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-126">If you require high-level abstractions and richer features like [Sagas](https://docs.particular.net/nservicebus/sagas/) for long-running processes that make distributed development easier, other commercial and open-source service buses like NServiceBus, MassTransit, and Brighter are worth evaluating.</span></span> <span data-ttu-id="ac6e6-127">在此案例中，要使用的抽象和 API 通常會直接由這些高階服務匯流排提供，而不是您自己的抽象 (例如 [eShopOnContainers 所提供的簡單事件匯流排抽象](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs))。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-127">In this case, the abstractions and API to use would usually be directly the ones provided by those high-level service buses instead of your own abstractions (like the [simple event bus abstractions provided at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)).</span></span> <span data-ttu-id="ac6e6-128">就此而言，您可以研究[使用 NServiceBus 的分支 eShopOnContainers](http://go.particular.net/eShopOnContainers) (Particular Software 所實作的其他衍生範例)</span><span class="sxs-lookup"><span data-stu-id="ac6e6-128">For that matter, you can research the [forked eShopOnContainers using NServiceBus](http://go.particular.net/eShopOnContainers) (additional derived sample implemented by Particular Software)</span></span>

<span data-ttu-id="ac6e6-129">當然，您一律可以在較低階技術 (例如 RabbitMQ 和 Docker) 上建置自己的服務匯流排功能，但是「重新發明車輪」所需的工作對於自訂企業應用程式而言可能成本太高。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-129">Of course, you could always build your own service bus features on top of lower-level technologies like RabbitMQ and Docker, but the work needed to “reinvent the wheel” might be too costly for a custom enterprise application.</span></span>

## <a name="integration-events"></a><span data-ttu-id="ac6e6-130">整合事件</span><span class="sxs-lookup"><span data-stu-id="ac6e6-130">Integration events</span></span>

<span data-ttu-id="ac6e6-131">整合事件用來讓跨多個微服務或外部系統的領域狀態同步。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-131">Integration events are used for bringing domain state in sync across multiple microservices or external systems.</span></span> <span data-ttu-id="ac6e6-132">這是藉由在微服務以外發行整合事件而達成。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-132">This is done by publishing integration events outside the microservice.</span></span> <span data-ttu-id="ac6e6-133">當事件發行到多個接收者微服務時 (微服務的數量為訂閱整合事件的微服務數量)，每個接收者微服務中的適當事件處理常式會處理事件。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-133">When an event is published to multiple receiver microservices (to as many microservices as are subscribed to the integration event), the appropriate event handler in each receiver microservice handles the event.</span></span>

<span data-ttu-id="ac6e6-134">整合事件基本上是保存資料的類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ac6e6-134">An integration event is basically a data-holding class, as in the following example:</span></span>

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

<span data-ttu-id="ac6e6-135">整合事件可以在每個微服務的應用程式層級定義，讓它們與其他微服務彼此分離，相當於伺服器和用戶端中的 ViewModel 定義方式。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-135">The integration events can be defined at the application level of each microservice, so they are decoupled from other microservices, in a way comparable to how ViewModels are defined in the server and client.</span></span> <span data-ttu-id="ac6e6-136">不建議的作法是跨多個微服務共用通用的整合事件程式庫；這麼做會將這些微服務與單一事件定義資料程式庫結合。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-136">What is not recommended is sharing a common integration events library across multiple microservices; doing that would be coupling those microservices with a single event definition data library.</span></span> <span data-ttu-id="ac6e6-137">您不會想要這樣做，原因就相同於您不會想要在多個微服務之間共用通用的領域模型：微服務必須是完全自主。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-137">You do not want to do that for the same reasons that you do not want to share a common domain model across multiple microservices: microservices must be completely autonomous.</span></span>

<span data-ttu-id="ac6e6-138">只有幾種程式庫是您應該在微服務之間共用的。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-138">There are only a few kinds of libraries you should share across microservices.</span></span> <span data-ttu-id="ac6e6-139">其中一種是最終應用程式區塊的程式庫，例如[事件匯流排用戶端 API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)，如同在 eShopOnContainers 中。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-139">One is libraries that are final application blocks, like the [Event Bus client API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), as in eShopOnContainers.</span></span> <span data-ttu-id="ac6e6-140">另一種是構成工具的程式庫，它們也可以共用為 NuGet 元件，例如 JSON 序列化程式。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-140">Another is libraries that constitute tools that could also be shared as NuGet components, like JSON serializers.</span></span>

## <a name="the-event-bus"></a><span data-ttu-id="ac6e6-141">事件匯流排</span><span class="sxs-lookup"><span data-stu-id="ac6e6-141">The event bus</span></span>

<span data-ttu-id="ac6e6-142">事件匯流排允許微服務之間的發行/訂閱樣式通訊，而不需要元件明確知道彼此，如圖 8-19 所示。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-142">An event bus allows publish/subscribe-style communication between microservices without requiring the components to explicitly be aware of each other, as shown in Figure 8-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="ac6e6-143">**圖 8-19**.</span><span class="sxs-lookup"><span data-stu-id="ac6e6-143">**Figure 8-19**.</span></span> <span data-ttu-id="ac6e6-144">事件匯流排的發行/訂閱基本概念</span><span class="sxs-lookup"><span data-stu-id="ac6e6-144">Publish/subscribe basics with an event bus</span></span>

<span data-ttu-id="ac6e6-145">事件匯流排與觀察者模式及發行-訂閱模式有關。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-145">The event bus is related to the Observer pattern and the publish-subscribe pattern.</span></span>

### <a name="observer-pattern"></a><span data-ttu-id="ac6e6-146">觀察者模式</span><span class="sxs-lookup"><span data-stu-id="ac6e6-146">Observer pattern</span></span>

<span data-ttu-id="ac6e6-147">在[觀察者模式](https://en.wikipedia.org/wiki/Observer_pattern)中，您的主要物件 (稱為可預見物件) 會將相關資訊 (事件) 通知其他有興趣的物件 (稱為觀察者)。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-147">In the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern), your primary object (known as the Observable) notifies other interested objects (known as Observers) with relevant information (events).</span></span>

### <a name="publish-subscribe-pubsub-pattern"></a><span data-ttu-id="ac6e6-148">發行-訂閱 (Pub/Sub) 模式</span><span class="sxs-lookup"><span data-stu-id="ac6e6-148">Publish-subscribe (Pub/Sub) pattern</span></span> 

<span data-ttu-id="ac6e6-149">[Pub/Sub 模式](https://msdn.microsoft.com/library/ff649664.aspx)的目的與觀察者模式相同：您想要在特定事件發生時通知其他服務。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-149">The purpose of the [Pub/Sub pattern](https://msdn.microsoft.com/library/ff649664.aspx) is the same as the Observer pattern: you want to notify other services when certain events take place.</span></span> <span data-ttu-id="ac6e6-150">但觀察者和 Pub/Sub 模式之間有一項重要的差異。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-150">But there is an important difference between the Observer and Pub/Sub patterns.</span></span> <span data-ttu-id="ac6e6-151">在觀察者模式中，廣播是直接從可預見物件對觀察者執行，讓他們「知道」彼此。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-151">In the observer pattern, the broadcast is performed directly from the observable to the observers, so they “know” each other.</span></span> <span data-ttu-id="ac6e6-152">但在使用 Pub/Sub 模式時，有一個稱為代理程式或訊息代理程式或事件匯流排的第三個元件，發行者和訂閱者都知道它。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-152">But when using a Pub/Sub pattern, there is a third component, called broker or message broker or event bus, which is known by both the publisher and subscriber.</span></span> <span data-ttu-id="ac6e6-153">因此，在使用 Pub/Sub 模式時，發行者和訂閱者會因為提及的事件匯流排或訊息代理程式而精確地分離。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-153">Therefore, when using the Pub/Sub pattern the publisher and the subscribers are precisely decoupled thanks to the mentioned event bus or message broker.</span></span>

### <a name="the-middleman-or-event-bus"></a><span data-ttu-id="ac6e6-154">中間人或事件匯流排</span><span class="sxs-lookup"><span data-stu-id="ac6e6-154">The middleman or event bus</span></span> 

<span data-ttu-id="ac6e6-155">您要如何達到發行者和訂閱者之間的匿名？</span><span class="sxs-lookup"><span data-stu-id="ac6e6-155">How do you achieve anonymity between publisher and subscriber?</span></span> <span data-ttu-id="ac6e6-156">簡單的方法是讓中間人負責處理所有通訊。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-156">An easy way is let a middleman take care of all the communication.</span></span> <span data-ttu-id="ac6e6-157">事件匯流排便是一個這類的中間人。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-157">An event bus is one such middleman.</span></span>

<span data-ttu-id="ac6e6-158">事件匯流排通常是由兩個部分組成：</span><span class="sxs-lookup"><span data-stu-id="ac6e6-158">An event bus is typically composed of two parts:</span></span>

-   <span data-ttu-id="ac6e6-159">抽象或介面。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-159">The abstraction or interface.</span></span>

-   <span data-ttu-id="ac6e6-160">一或多個實作。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-160">One or more implementations.</span></span>

<span data-ttu-id="ac6e6-161">在圖 8-19 中，您可以看到，從應用程式的觀點而言，事件匯流排只不過是 Pub/Sub 通道。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-161">In Figure 8-19 you can see how, from an application point of view, the event bus is nothing more than a Pub/Sub channel.</span></span> <span data-ttu-id="ac6e6-162">實作這個非同步通訊的方式可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-162">The way you implement this asynchronous communication can vary.</span></span> <span data-ttu-id="ac6e6-163">它可能有多種實作，因此您可以根據環境需求 (例如，生產與開發環境)，在兩者之間交換。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-163">It can have multiple implementations so that you can swap between them, depending on the environment requirements (for example, production versus development environments).</span></span>

<span data-ttu-id="ac6e6-164">在圖 8-20 中，您可以看到事件匯流排的抽象，且具有根據基礎結構傳訊技術，例如 RabbitMQ、Azure 服務匯流排或其他事件/訊息代理程式的多個實作。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-164">In Figure 8-20 you can see an abstraction of an event bus with multiple implementations based on infrastructure messaging technologies like RabbitMQ, Azure Service Bus, or other event/message broker.</span></span> 

![](./media/image21.png)

<span data-ttu-id="ac6e6-165">**圖 8- 20.**</span><span class="sxs-lookup"><span data-stu-id="ac6e6-165">**Figure 8- 20.**</span></span> <span data-ttu-id="ac6e6-166">事件匯流排的多個實作</span><span class="sxs-lookup"><span data-stu-id="ac6e6-166">Multiple implementations of an event bus</span></span>

<span data-ttu-id="ac6e6-167">不過，如先前所提及，使用您自己的抽象 (事件匯流排介面) 只適合在您必須抽象所支援的基本事件匯流排功能時。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-167">However, and as mentioned previously, using your own abstractions (the event bus interface) is good only if you need basic event bus features supported by your abstractions.</span></span> <span data-ttu-id="ac6e6-168">如果您需要更豐富的服務匯流排功能，可能應該使用您慣用的商業服務匯流排所提供的 API 和抽象，而不是自己的抽象。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-168">If you need richer service bus features, you should probably use the API and abstractions provided by your preferred commercial service bus instead of your own abstractions.</span></span> 

### <a name="defining-an-event-bus-interface"></a><span data-ttu-id="ac6e6-169">定義事件匯流排介面</span><span class="sxs-lookup"><span data-stu-id="ac6e6-169">Defining an event bus interface</span></span>

<span data-ttu-id="ac6e6-170">讓我們從一些事件匯流排介面的實作程式碼，以及探索用途的可能實作開始。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-170">Let’s start with some implementation code for the event bus interface and possible implementations for exploration purposes.</span></span> <span data-ttu-id="ac6e6-171">介面應該是泛型且簡單，如同下列介面。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-171">The interface should be generic and straightforward, as in the following interface.</span></span>

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

<span data-ttu-id="ac6e6-172">`Publish` 方法很直接明瞭。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-172">The `Publish` method is straightforward.</span></span> <span data-ttu-id="ac6e6-173">事件匯流排會將傳遞給它的整合事件，廣播到任何微服務或甚至是訂閱該事件的外部應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-173">The event bus will broadcast the integration event passed to it to any microservice, or even an external application, subscribed to that event.</span></span> <span data-ttu-id="ac6e6-174">這個方法由發行事件的微服務所使用。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-174">This method is used by the microservice that is publishing the event.</span></span>

<span data-ttu-id="ac6e6-175">`Subscribe` 方法 (您可以有根據引數而定的數種實作) 是由想要收到事件的微服務所使用。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-175">The `Subscribe` methods (you can have several implementations depending on the arguments) are used by the microservices that want to receive events.</span></span> <span data-ttu-id="ac6e6-176">這個方法有兩個引數。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-176">This method has two arguments.</span></span> <span data-ttu-id="ac6e6-177">第一個是要訂閱的整合事件 (`IntegrationEvent`)。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-177">The first is the integration event to subscribe to (`IntegrationEvent`).</span></span> <span data-ttu-id="ac6e6-178">第二個引數是整合事件處理常式 (或回呼方法)，名為 `IIntegrationEventHandler<T>`，且將在接收者微服務取得該整合事件訊息時執行。</span><span class="sxs-lookup"><span data-stu-id="ac6e6-178">The second argument is the integration event handler (or callback method), named `IIntegrationEventHandler<T>`, to be executed when the receiver microservice gets that integration event message.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ac6e6-179">[上一頁] (database-server-container.md) [下一頁] (rabbitmq-event-bus-development-test-environment.md)</span><span class="sxs-lookup"><span data-stu-id="ac6e6-179">[Previous] (database-server-container.md) [Next] (rabbitmq-event-bus-development-test-environment.md)</span></span>
