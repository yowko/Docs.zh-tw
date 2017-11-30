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
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a><span data-ttu-id="8312f-104">實作事件架構 microservices （整合事件） 之間的通訊</span><span class="sxs-lookup"><span data-stu-id="8312f-104">Implementing event-based communication between microservices (integration events)</span></span>

<span data-ttu-id="8312f-105">如前所述，當您使用以事件為基礎的通訊時，微服務會發行事件時值得注意的項目，例如，它會更新的商務實體。</span><span class="sxs-lookup"><span data-stu-id="8312f-105">As described earlier, when you use event-based communication, a microservice publishes an event when something notable happens, such as when it updates a business entity.</span></span> <span data-ttu-id="8312f-106">其他 microservices 訂閱這些事件。</span><span class="sxs-lookup"><span data-stu-id="8312f-106">Other microservices subscribe to those events.</span></span> <span data-ttu-id="8312f-107">當微服務收到事件時，它可以更新自己商務實體，可能會導致更多的事件發行。</span><span class="sxs-lookup"><span data-stu-id="8312f-107">When a microservice receives an event, it can update its own business entities, which might lead to more events being published.</span></span> <span data-ttu-id="8312f-108">此發行/訂閱系統通常會執行所使用的事件匯流排實作。</span><span class="sxs-lookup"><span data-stu-id="8312f-108">This publish/subscribe system is usually performed by using an implementation of an event bus.</span></span> <span data-ttu-id="8312f-109">事件匯流排可設計為介面訂閱及取消訂閱事件，並將事件發行所需的 API。</span><span class="sxs-lookup"><span data-stu-id="8312f-109">The event bus can be designed as an interface with the API needed to subscribe and unsubscribe to events and to publish events.</span></span> <span data-ttu-id="8312f-110">它也可以有任何處理序間或郵件通訊，例如訊息佇列或服務匯流排支援非同步通訊和發佈/訂閱模型為基礎的一或多個實作。</span><span class="sxs-lookup"><span data-stu-id="8312f-110">It can also have one or more implementations based on any inter-process or messaging communication, such as a messaging queue or a service bus that supports asynchronous communication and a publish/subscribe model.</span></span>

<span data-ttu-id="8312f-111">您可以使用事件來實作商務交易橫跨多個服務，它將提供這些服務之間的最終一致性。</span><span class="sxs-lookup"><span data-stu-id="8312f-111">You can use events to implement business transactions that span multiple services, which gives you eventual consistency between those services.</span></span> <span data-ttu-id="8312f-112">最終一致性的交易是由一系列的分散式動作所組成。</span><span class="sxs-lookup"><span data-stu-id="8312f-112">An eventually consistent transaction consists of a series of distributed actions.</span></span> <span data-ttu-id="8312f-113">每個動作，在微服務更新的商務實體，並發行事件的觸發程序的下一個動作。</span><span class="sxs-lookup"><span data-stu-id="8312f-113">At each action, the microservice updates a business entity and publishes an event that triggers the next action.</span></span>

![](./media/image19.PNG)

<span data-ttu-id="8312f-114">**圖 8-18**。</span><span class="sxs-lookup"><span data-stu-id="8312f-114">**Figure 8-18**.</span></span> <span data-ttu-id="8312f-115">事件導向的通訊，根據事件匯流排</span><span class="sxs-lookup"><span data-stu-id="8312f-115">Event-driven communication based on an event bus</span></span>

<span data-ttu-id="8312f-116">本章節描述如何實作這種類型的.NET 與通訊，以及在使用一般事件匯流排介面，如圖 8-18 所示。</span><span class="sxs-lookup"><span data-stu-id="8312f-116">This section describes how you can implement this type of communication with .NET by using a generic event bus interface, as shown in Figure 8-18.</span></span> <span data-ttu-id="8312f-117">有多個可能的實作，每個使用不同的技術或基礎結構，例如 RabbitMQ、 Azure 服務匯流排，或任何其他第三方開放原始碼或商業服務匯流排。</span><span class="sxs-lookup"><span data-stu-id="8312f-117">There are multiple potential implementations, each using a different technology or infrastructure such as RabbitMQ, Azure Service Bus, or any other third-party open source or commercial service bus.</span></span>

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a><span data-ttu-id="8312f-118">訊息仲介和服務匯流排用於生產系統</span><span class="sxs-lookup"><span data-stu-id="8312f-118">Using message brokers and services buses for production systems</span></span>

<span data-ttu-id="8312f-119">架構 > 一節所述，您可以選擇從多個訊息的技術，實作抽象事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="8312f-119">As noted in the architecture section, you can choose from multiple messaging technologies for implementing your abstract event bus.</span></span> <span data-ttu-id="8312f-120">但是，這些技術都是在不同層級。</span><span class="sxs-lookup"><span data-stu-id="8312f-120">But these technologies are at different levels.</span></span> <span data-ttu-id="8312f-121">例如，RabbitMQ，訊息的 broker 傳輸，會比等 Azure 服務匯流排、 NServiceBus、 MassTransit 或 Brighter 商業產品的較低層級。</span><span class="sxs-lookup"><span data-stu-id="8312f-121">For instance, RabbitMQ, a messaging broker transport, is at a lower level than commercial products like Azure Service Bus, NServiceBus, MassTransit, or Brighter.</span></span> <span data-ttu-id="8312f-122">大部分的這些產品可以 RabbitMQ 或 Azure 服務匯流排的最上方工作。</span><span class="sxs-lookup"><span data-stu-id="8312f-122">Most of these products can work on top of either RabbitMQ or Azure Service Bus.</span></span> <span data-ttu-id="8312f-123">您所選擇的產品取決於如何許多功能和多少--現成的延展性，您需要應用程式。</span><span class="sxs-lookup"><span data-stu-id="8312f-123">Your choice of product depends on how many features and how much out-of-the-box scalability you need for your application.</span></span>

<span data-ttu-id="8312f-124">實作只事件匯流排的概念證明您的開發環境，如同 eShopOnContainers 範例中，執行做為容器 RabbitMQ 之上的簡單實作可能會就足夠了。</span><span class="sxs-lookup"><span data-stu-id="8312f-124">For implementing just an event bus proof-of-concept for your development environment, as in the eShopOnContainers sample, a simple implementation on top of RabbitMQ running as a container might be enough.</span></span> <span data-ttu-id="8312f-125">但為關鍵任務而且需要高延展性的生產系統，您可能想要評估，並使用 Azure Service Fabric。</span><span class="sxs-lookup"><span data-stu-id="8312f-125">But for mission-critical and production systems that need high scalability, you might want to evaluate and use Azure Service Fabric.</span></span> <span data-ttu-id="8312f-126">如果您需要高階的抽象概念，而且更豐富的功能類似[sagas](https://docs.particular.net/nservicebus/sagas/)長時間執行之處理序的更簡單、 商業和開放原始碼的服務匯流排 NServiceBus，MassTransit，例如，讓分散式的開發和Brighter 是值得評估。</span><span class="sxs-lookup"><span data-stu-id="8312f-126">If you require high-level abstractions and richer features like [sagas](https://docs.particular.net/nservicebus/sagas/) for long-running processes that make distributed development easier, other commercial and open-source service buses like NServiceBus, MassTransit, and Brighter are worth evaluating.</span></span> <span data-ttu-id="8312f-127">當然，您一律可以建置自己 RabbitMQ 和 Docker，這類的較低層級技術的服務匯流排功能，但造所需的工作可能是自訂的企業應用程式的成本太高。</span><span class="sxs-lookup"><span data-stu-id="8312f-127">Of course, you could always build your own service bus features on top of lower-level technologies like RabbitMQ and Docker, but the work needed to reinvent the wheel might be too costly for a custom enterprise application.</span></span>

<span data-ttu-id="8312f-128">重申： 範例事件匯流排的抽象概念，其中顯示 eShopOnContainers 範例中的實作適用於僅做概念證明。</span><span class="sxs-lookup"><span data-stu-id="8312f-128">To reiterate: the sample event bus abstractions and implementation showcased in the eShopOnContainers sample are intended to be used only as a proof of concept.</span></span> <span data-ttu-id="8312f-129">一旦您決定您想要有非同步處理和事件導向通訊，本節所述，您應該選擇最符合您需求的服務匯流排產品。</span><span class="sxs-lookup"><span data-stu-id="8312f-129">Once you have decided that you want to have asynchronous and event-driven communication, as explained in the current section, you should choose the service bus product that best fits your needs.</span></span>

## <a name="integration-events"></a><span data-ttu-id="8312f-130">整合事件</span><span class="sxs-lookup"><span data-stu-id="8312f-130">Integration events</span></span>

<span data-ttu-id="8312f-131">整合事件用來將跨多個 microservices 或外部系統的網域狀態同步。</span><span class="sxs-lookup"><span data-stu-id="8312f-131">Integration events are used for bringing domain state in sync across multiple microservices or external systems.</span></span> <span data-ttu-id="8312f-132">這是發行整合事件以外的微服務。</span><span class="sxs-lookup"><span data-stu-id="8312f-132">This is done by publishing integration events outside the microservice.</span></span> <span data-ttu-id="8312f-133">當事件發佈到多個接收者 microservices （若要盡可能 microservices 會整合事件訂閱) 時，每個接收者微服務中的適當的事件處理常式會處理事件。</span><span class="sxs-lookup"><span data-stu-id="8312f-133">When an event is published to multiple receiver microservices (to as many microservices as are subscribed to the integration event), the appropriate event handler in each receiver microservice handles the event.</span></span>

<span data-ttu-id="8312f-134">整合事件基本上是保存資料之類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8312f-134">An integration event is basically a data-holding class, as in the following example:</span></span>

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

<span data-ttu-id="8312f-135">整合事件類別可以很簡單;例如，它可能包含 GUID 的識別碼</span><span class="sxs-lookup"><span data-stu-id="8312f-135">The integration event class can be simple; for example, it might contain a GUID for its ID.</span></span>

<span data-ttu-id="8312f-136">整合事件可以定義應用程式層級的每個微服務，讓它們彼此分離其他 microservices，相當於 ViewModels 中伺服器和用戶端的定義方式的方式。</span><span class="sxs-lookup"><span data-stu-id="8312f-136">The integration events can be defined at the application level of each microservice, so they are decoupled from other microservices, in a way comparable to how ViewModels are defined in the server and client.</span></span> <span data-ttu-id="8312f-137">不建議跨多個 microservices; 共用通用的整合事件程式庫這麼做可就會結合這些 microservices 與單一事件定義資料程式庫。</span><span class="sxs-lookup"><span data-stu-id="8312f-137">What is not recommended is sharing a common integration events library across multiple microservices; doing that would be coupling those microservices with a single event definition data library.</span></span> <span data-ttu-id="8312f-138">您不想要這樣做，基於相同理由，您不想在多個 microservices 之間共用通用的網域模型： microservices 必須是完全自主。</span><span class="sxs-lookup"><span data-stu-id="8312f-138">You do not want to do that for the same reasons that you do not want to share a common domain model across multiple microservices: microservices must be completely autonomous.</span></span>

<span data-ttu-id="8312f-139">有只有幾種不同的程式庫，您應該在 microservices 共用。</span><span class="sxs-lookup"><span data-stu-id="8312f-139">There are only a few kinds of libraries you should share across microservices.</span></span> <span data-ttu-id="8312f-140">其中一個是程式庫最終的應用程式區塊，例如[事件匯流排用戶端 API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)，而在 eShopOnContainers 中。</span><span class="sxs-lookup"><span data-stu-id="8312f-140">One is libraries that are final application blocks, like the [Event Bus client API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), as in eShopOnContainers.</span></span> <span data-ttu-id="8312f-141">另一個是程式庫的構成也無法共用為 NuGet 元件，例如 JSON 序列化程式的工具。</span><span class="sxs-lookup"><span data-stu-id="8312f-141">Another is libraries that constitute tools that could also be shared as NuGet components, like JSON serializers.</span></span>

## <a name="the-event-bus"></a><span data-ttu-id="8312f-142">事件匯流排</span><span class="sxs-lookup"><span data-stu-id="8312f-142">The event bus</span></span>

<span data-ttu-id="8312f-143">事件匯流排 」 可讓發行/訂閱樣式 microservices 而不需要明確留意，如圖 8-19 所示的元件之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="8312f-143">An event bus allows publish/subscribe-style communication between microservices without requiring the components to explicitly be aware of each other, as shown in Figure 8-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="8312f-144">**圖 8-19**。</span><span class="sxs-lookup"><span data-stu-id="8312f-144">**Figure 8-19**.</span></span> <span data-ttu-id="8312f-145">發佈/訂閱與事件匯流排的基本概念</span><span class="sxs-lookup"><span data-stu-id="8312f-145">Publish/subscribe basics with an event bus</span></span>

<span data-ttu-id="8312f-146">事件匯流排與觀察器模式及發行-訂閱模式。</span><span class="sxs-lookup"><span data-stu-id="8312f-146">The event bus is related to the Observer pattern and the publish-subscribe pattern.</span></span>

### <a name="observer-pattern"></a><span data-ttu-id="8312f-147">觀察器模式</span><span class="sxs-lookup"><span data-stu-id="8312f-147">Observer pattern</span></span>

<span data-ttu-id="8312f-148">在[觀察器模式](https://en.wikipedia.org/wiki/Observer_pattern)，主要物件 （稱為 Observable） （事件） 的相關資訊通知其他想要的物件 （稱為 「 觀察者而定）。</span><span class="sxs-lookup"><span data-stu-id="8312f-148">In the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern), your primary object (known as the Observable) notifies other interested objects (known as Observers) with relevant information (events).</span></span>

### <a name="publish-subscribe-pubsub-pattern"></a><span data-ttu-id="8312f-149">發行-訂閱 (Pub/Sub) 模式</span><span class="sxs-lookup"><span data-stu-id="8312f-149">Publish-subscribe (Pub/Sub) pattern</span></span> 

<span data-ttu-id="8312f-150">目的[Pub/Sub 模式](https://msdn.microsoft.com/en-us/library/ff649664.aspx)觀察器模式與相同： 您想要特定事件發生時通知其他服務。</span><span class="sxs-lookup"><span data-stu-id="8312f-150">The purpose of the [Pub/Sub pattern](https://msdn.microsoft.com/en-us/library/ff649664.aspx) is the same as the Observer pattern: you want to notify other services when certain events take place.</span></span> <span data-ttu-id="8312f-151">但有一項重要之間的觀察者和 Pub/Sub 模式語意差異。</span><span class="sxs-lookup"><span data-stu-id="8312f-151">But there is an important semantic difference between the Observer and Pub/Sub patterns.</span></span> <span data-ttu-id="8312f-152">Pub/Sub 模式中，重點是在將訊息廣播。</span><span class="sxs-lookup"><span data-stu-id="8312f-152">In the Pub/Sub pattern, the focus is on broadcasting messages.</span></span> <span data-ttu-id="8312f-153">相反地，在觀察器模式中，Observable 不知道誰事件會移至，就是這已經出。換句話說，可觀察 （發行者） 不知道屬於觀察者 （「 訂閱者 」）。</span><span class="sxs-lookup"><span data-stu-id="8312f-153">In contrast, in the Observer pattern, the Observable does not know who the events are going to, just that they have gone out. In other words, the Observable (the publisher) does not know who the Observers (the subscribers) are.</span></span>

### <a name="the-middleman-or-event-bus"></a><span data-ttu-id="8312f-154">Middleman 或事件匯流排</span><span class="sxs-lookup"><span data-stu-id="8312f-154">The middleman or event bus</span></span> 

<span data-ttu-id="8312f-155">您要如何達到發行者和訂閱者之間的匿名？</span><span class="sxs-lookup"><span data-stu-id="8312f-155">How do you achieve anonymity between publisher and subscriber?</span></span> <span data-ttu-id="8312f-156">簡單的方法是讓 middleman，負責處理的所有通訊。</span><span class="sxs-lookup"><span data-stu-id="8312f-156">An easy way is let a middleman take care of all the communication.</span></span> <span data-ttu-id="8312f-157">事件匯流排是一個這類 middleman。</span><span class="sxs-lookup"><span data-stu-id="8312f-157">An event bus is one such middleman.</span></span>

<span data-ttu-id="8312f-158">事件匯流排通常是由兩個部分組成：</span><span class="sxs-lookup"><span data-stu-id="8312f-158">An event bus is typically composed of two parts:</span></span>

-   <span data-ttu-id="8312f-159">抽象或介面。</span><span class="sxs-lookup"><span data-stu-id="8312f-159">The abstraction or interface.</span></span>

-   <span data-ttu-id="8312f-160">一或多個實作。</span><span class="sxs-lookup"><span data-stu-id="8312f-160">One or more implementations.</span></span>

<span data-ttu-id="8312f-161">圖 8-19 您可以查看如何從應用程式的觀點，事件匯流排只不過是 Pub/Sub 通道。</span><span class="sxs-lookup"><span data-stu-id="8312f-161">In Figure 8-19 you can see how, from an application point of view, the event bus is nothing more than a Pub/Sub channel.</span></span> <span data-ttu-id="8312f-162">實作這個非同步通訊的方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8312f-162">The way you implement this asynchronous communication can vary.</span></span> <span data-ttu-id="8312f-163">因此，您可以根據環境需求 （例如，開發環境與生產） 而定的兩者之間交換，它可能有多個實作。</span><span class="sxs-lookup"><span data-stu-id="8312f-163">It can have multiple implementations so that you can swap between them, depending on the environment requirements (for example, production versus development environments).</span></span>

<span data-ttu-id="8312f-164">圖 8-20 您可以看到事件匯流排的抽象概念，以根據傳訊 RabbitMQ、 Azure 服務匯流排或其他的服務匯流排類似 NServiceBus、 MassTransit 等這類技術的基礎結構的多個實作。</span><span class="sxs-lookup"><span data-stu-id="8312f-164">In Figure 8-20 you can see an abstraction of an event bus with multiple implementations based on infrastructure messaging technologies like RabbitMQ, Azure Service Bus, or other service buses like NServiceBus, MassTransit, etc.</span></span>

![](./media/image21.png)

<span data-ttu-id="8312f-165">**圖 8-20。**</span><span class="sxs-lookup"><span data-stu-id="8312f-165">**Figure 8- 20.**</span></span> <span data-ttu-id="8312f-166">事件匯流排的多個實作</span><span class="sxs-lookup"><span data-stu-id="8312f-166">Multiple implementations of an event bus</span></span>

<span data-ttu-id="8312f-167">不過，以反白顯示之前，使用 （事件匯流排介面） 的抽象概念是可能只有在必須支援您的抽象概念的基本事件匯流排功能。</span><span class="sxs-lookup"><span data-stu-id="8312f-167">However, as highlighted previously, using abstractions (the event bus interface) is possible only if you need basic event bus features supported by your abstractions.</span></span> <span data-ttu-id="8312f-168">如果您需要更豐富的服務匯流排功能，您應該使用您慣用的服務匯流排，而不是您自己的抽象提供的 API。</span><span class="sxs-lookup"><span data-stu-id="8312f-168">If you need richer service bus features, you should probably use the API provided by your preferred service bus instead of your own abstractions.</span></span>

### <a name="defining-an-event-bus-interface"></a><span data-ttu-id="8312f-169">定義事件匯流排介面</span><span class="sxs-lookup"><span data-stu-id="8312f-169">Defining an event bus interface</span></span>

<span data-ttu-id="8312f-170">讓我們開始某些事件匯流排介面的實作程式碼與可能的實作進行探索。</span><span class="sxs-lookup"><span data-stu-id="8312f-170">Let’s start with some implementation code for the event bus interface and possible implementations for exploration purposes.</span></span> <span data-ttu-id="8312f-171">泛型和簡單，如同下列介面，應該是介面。</span><span class="sxs-lookup"><span data-stu-id="8312f-171">The interface should be generic and straightforward, as in the following interface.</span></span>

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

<span data-ttu-id="8312f-172">發行方法相當簡單。</span><span class="sxs-lookup"><span data-stu-id="8312f-172">The Publish method is straightforward.</span></span> <span data-ttu-id="8312f-173">事件匯流排會廣播整合事件傳遞給它，該事件訂閱任何微服務。</span><span class="sxs-lookup"><span data-stu-id="8312f-173">The event bus will broadcast the integration event passed to it to any microservice subscribed to that event.</span></span> <span data-ttu-id="8312f-174">這個方法會使用此事件發行微服務。</span><span class="sxs-lookup"><span data-stu-id="8312f-174">This method is used by the microservice that is publishing the event.</span></span>

<span data-ttu-id="8312f-175">Subscribe 方法會使用 microservices 想要接收事件。</span><span class="sxs-lookup"><span data-stu-id="8312f-175">The Subscribe method is used by the microservices that want to receive events.</span></span> <span data-ttu-id="8312f-176">這個方法有兩個部分。</span><span class="sxs-lookup"><span data-stu-id="8312f-176">This method has two parts.</span></span> <span data-ttu-id="8312f-177">第一個是整合的事件訂閱 (IntegrationEvent)。</span><span class="sxs-lookup"><span data-stu-id="8312f-177">The first is the integration event to subscribe to (IntegrationEvent).</span></span> <span data-ttu-id="8312f-178">第二個部分是整合事件處理常式 （或回呼方法） 呼叫 (IIntegrationEventHandler&lt;T&gt;) 當微服務收到事件訊息的整合。</span><span class="sxs-lookup"><span data-stu-id="8312f-178">The second part is the integration event handler (or callback method) to be called (IIntegrationEventHandler&lt;T&gt;) when the microservice receives that integration event message.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8312f-179">[上一個](資料庫的伺服器-container.md) [下一步] (rabbitmq-event-bus-development-test-environment.md)</span><span class="sxs-lookup"><span data-stu-id="8312f-179">[Previous] (database-server-container.md) [Next] (rabbitmq-event-bus-development-test-environment.md)</span></span>
