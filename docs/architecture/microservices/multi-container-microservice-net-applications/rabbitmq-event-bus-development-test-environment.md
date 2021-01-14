---
title: 針對開發或測試環境使用 RabbitMQ 實作事件匯流排
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對開發或測試環境使用 RabbitMQ 實作整合事件的事件匯流排傳訊。
ms.date: 01/13/2021
ms.openlocfilehash: a1e7d11e376080a03269f202fa6ae24ffeb0f4d2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188077"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="64114-103">針對開發或測試環境使用 RabbitMQ 實作事件匯流排</span><span class="sxs-lookup"><span data-stu-id="64114-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="64114-104">首先您應該知道，如果您根據容器中所執行的 RabbitMQ 來建立自訂事件匯流排 (如同 eShopOnContainers 應用程式的做法)，則只能用於開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="64114-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="64114-105">請勿將它用於生產環境，除非您在生產環境就緒的服務匯流排中建立它。</span><span class="sxs-lookup"><span data-stu-id="64114-105">Don't use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="64114-106">簡單的自訂事件匯流排可能會遺失許多商業服務匯流排所具備並可供生產環境使用的重要功能。</span><span class="sxs-lookup"><span data-stu-id="64114-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="64114-107">EShopOnContainers 中的其中一個事件匯流排自訂實施基本上是使用 RabbitMQ API 的程式庫。</span><span class="sxs-lookup"><span data-stu-id="64114-107">One of the event bus custom implementations in eShopOnContainers is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="64114-108"> (還有另一個以 Azure 服務匯流排為基礎的執行。 ) </span><span class="sxs-lookup"><span data-stu-id="64114-108">(There's another implementation based on Azure Service Bus.)</span></span>

<span data-ttu-id="64114-109">使用 RabbitMQ 實作事件匯流排可讓微服務訂閱事件、發行事件和接收事件，如圖 6-21 所示。</span><span class="sxs-lookup"><span data-stu-id="64114-109">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![顯示訊息寄件者和訊息接收者之間 RabbitMQ 的圖表。](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="64114-111">**圖 6-12。**</span><span class="sxs-lookup"><span data-stu-id="64114-111">**Figure 6-21.**</span></span> <span data-ttu-id="64114-112">事件匯流排的 RabbitMQ 實作</span><span class="sxs-lookup"><span data-stu-id="64114-112">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="64114-113">RabbitMQ 的功能是訊息發行者與訂閱者之間的媒介，用來處理散發。</span><span class="sxs-lookup"><span data-stu-id="64114-113">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="64114-114">在程式碼中，EventBusRabbitMQ 類別會實作泛型 IEventBus 介面。</span><span class="sxs-lookup"><span data-stu-id="64114-114">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="64114-115">這項實行是以相依性插入為基礎，因此您可以從這個開發/測試版本切換至實際執行版本。</span><span class="sxs-lookup"><span data-stu-id="64114-115">This implementation is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="64114-116">範例開發/測試事件匯流排的 RabbitMQ 實作是未定案程式碼。</span><span class="sxs-lookup"><span data-stu-id="64114-116">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="64114-117">它必須處理 RabbitMQ 伺服器的連接，並提供程式碼將訊息事件發行到佇列。</span><span class="sxs-lookup"><span data-stu-id="64114-117">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="64114-118">它也必須實作每個事件類型之整合事件處理常式集合的字典，這些事件類型對每個接收者微服務的具現化和訂閱可能都不同，如圖 6-21 所示。</span><span class="sxs-lookup"><span data-stu-id="64114-118">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="64114-119">使用 RabbitMQ 實作簡單的發行方法</span><span class="sxs-lookup"><span data-stu-id="64114-119">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="64114-120">下列程式碼是適用于 RabbitMQ 的事件匯流排實作為的 *_簡化_* 版，以展示整個案例。</span><span class="sxs-lookup"><span data-stu-id="64114-120">The following code is a \**_simplified_* _ version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="64114-121">您並不會真的這樣處理連線。</span><span class="sxs-lookup"><span data-stu-id="64114-121">You don't really handle the connection this way.</span></span> <span data-ttu-id="64114-122">若要查看完整的實作，請參閱 [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) 存放庫中的實際程式碼。</span><span class="sxs-lookup"><span data-stu-id="64114-122">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

<span data-ttu-id="64114-123">您可以使用[Polly](https://github.com/App-vNext/Polly)重試原則來改善 eShopOnContainers 應用程式中發佈方法的[實際程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)，這會在 RabbitMQ 容器未就緒時，一次重試工作。</span><span class="sxs-lookup"><span data-stu-id="64114-123">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task some times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="64114-124">當 docker 撰寫正在啟動容器時，就會發生此情況;例如，RabbitMQ 容器的啟動速度可能會比其他容器更慢。</span><span class="sxs-lookup"><span data-stu-id="64114-124">This scenario can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="64114-125">如前所述，RabbitMQ 中有許多可能的組態，因此這段程式碼只應該用於開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="64114-125">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="64114-126">使用 RabbitMQ API 實作訂閱程式碼</span><span class="sxs-lookup"><span data-stu-id="64114-126">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="64114-127">如同發行程式碼，下列程式碼是 RabbitMQ 之事件匯流排實作的一部分簡化。</span><span class="sxs-lookup"><span data-stu-id="64114-127">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="64114-128">同樣地，除非您想要改進，否則您通常不需要將它變更。</span><span class="sxs-lookup"><span data-stu-id="64114-128">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();

        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

<span data-ttu-id="64114-129">每個事件類型會有相關的通道以從 RabbitMQ 取得事件。</span><span class="sxs-lookup"><span data-stu-id="64114-129">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="64114-130">之後，您可以視需要針對每個通道和事件類型，擁有許多事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="64114-130">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="64114-131">Subscribe 方法接受 IIntegrationEventHandler 物件，就像是目前微服務及其相關 IntegrationEvent 物件中的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="64114-131">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="64114-132">此程式碼接著會將該事件處理常式新增至事件處理常式清單，每個整合事件類型可根據每個用戶端微服務擁有這些事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="64114-132">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="64114-133">如果用戶端程式碼尚未訂閱事件，程式碼會建立事件類型的通道，以便在從任何其他服務發行該事件時，可從 RabbitMQ 接收推送樣式的事件。</span><span class="sxs-lookup"><span data-stu-id="64114-133">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="64114-134">如上所述，在 eShopOnContainers 中實作為的事件匯流排只有和教育用途，因為它只會處理主要案例，因此尚未準備好用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="64114-134">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="64114-135">針對生產案例，請檢查下列其他資源（特定于 RabbitMQ），以及在 [微服務區段之間執行以事件為基礎的通訊](./integration-event-based-microservice-communications.md#additional-resources) 。</span><span class="sxs-lookup"><span data-stu-id="64114-135">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="64114-136">其他資源</span><span class="sxs-lookup"><span data-stu-id="64114-136">Additional resources</span></span>

<span data-ttu-id="64114-137">具有 RabbitMQ 支援的生產環境就緒解決方案。</span><span class="sxs-lookup"><span data-stu-id="64114-137">A production-ready solution with support for RabbitMQ.</span></span>

- <span data-ttu-id="64114-138">_ \*EasyNetQ\*\*-RabbitMQ 的開放原始碼 .net API 用戶端</span><span class="sxs-lookup"><span data-stu-id="64114-138">_ *EasyNetQ*\* - Open Source .NET API client for RabbitMQ \</span></span>
  <https://easynetq.com/>

- <span data-ttu-id="64114-139">**MassTransit** </span><span class="sxs-lookup"><span data-stu-id="64114-139">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> <span data-ttu-id="64114-140">[上一個](integration-event-based-microservice-communications.md) 
> [下一步](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="64114-140">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
