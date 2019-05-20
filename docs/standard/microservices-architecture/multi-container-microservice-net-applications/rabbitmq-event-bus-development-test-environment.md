---
title: 針對開發或測試環境使用 RabbitMQ 實作事件匯流排
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對開發或測試環境使用 RabbitMQ 實作整合事件的事件匯流排傳訊。
ms.date: 10/02/2018
ms.openlocfilehash: af02208bb9e680403a04377ccb740a8b15be29bc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644442"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="1ac40-103">針對開發或測試環境使用 RabbitMQ 實作事件匯流排</span><span class="sxs-lookup"><span data-stu-id="1ac40-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="1ac40-104">首先您應該知道，如果您根據容器中所執行的 RabbitMQ 來建立自訂事件匯流排 (如同 eShopOnContainers 應用程式的做法)，則只能用於開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="1ac40-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="1ac40-105">除非您將它當做準備好用於生產環境之服務匯流排的一部分來建置，否則不應該用於生產環境中。</span><span class="sxs-lookup"><span data-stu-id="1ac40-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="1ac40-106">簡單的自訂事件匯流排可能會遺失許多商業服務匯流排所具備並可供生產環境使用的重要功能。</span><span class="sxs-lookup"><span data-stu-id="1ac40-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="1ac40-107">eShopOnContainers 的其中一個事件匯流排自訂實作基本上是使用 RabbitMQ API 的程式庫 (另一個實作是以 Azure 服務匯流排為依據)。</span><span class="sxs-lookup"><span data-stu-id="1ac40-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="1ac40-108">使用 RabbitMQ 實作事件匯流排可讓微服務訂閱事件、發行事件和接收事件，如圖 6-21 所示。</span><span class="sxs-lookup"><span data-stu-id="1ac40-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![RabbitMQ 的功能是訊息發行者與訂閱者之間的媒介，用來處理散發。](./media/image22.png)

<span data-ttu-id="1ac40-110">**圖 6-12。**</span><span class="sxs-lookup"><span data-stu-id="1ac40-110">**Figure 6-21.**</span></span> <span data-ttu-id="1ac40-111">事件匯流排的 RabbitMQ 實作</span><span class="sxs-lookup"><span data-stu-id="1ac40-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="1ac40-112">在程式碼中，EventBusRabbitMQ 類別會實作泛型 IEventBus 介面。</span><span class="sxs-lookup"><span data-stu-id="1ac40-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="1ac40-113">這是以相依性插入為基礎，因此您可以從此開發/測試版本切換至生產版本。</span><span class="sxs-lookup"><span data-stu-id="1ac40-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="1ac40-114">範例開發/測試事件匯流排的 RabbitMQ 實作是未定案程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ac40-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="1ac40-115">它必須處理 RabbitMQ 伺服器的連接，並提供程式碼將訊息事件發行到佇列。</span><span class="sxs-lookup"><span data-stu-id="1ac40-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="1ac40-116">它也必須實作每個事件類型之整合事件處理常式集合的字典，這些事件類型對每個接收者微服務的具現化和訂閱可能都不同，如圖 6-21 所示。</span><span class="sxs-lookup"><span data-stu-id="1ac40-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="1ac40-117">使用 RabbitMQ 實作簡單的發行方法</span><span class="sxs-lookup"><span data-stu-id="1ac40-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="1ac40-118">下列程式碼是簡化版本的 RabbitMQ 事件匯流排實作，目的是展示整個情節。</span><span class="sxs-lookup"><span data-stu-id="1ac40-118">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="1ac40-119">您並不會真的這樣處理連線。</span><span class="sxs-lookup"><span data-stu-id="1ac40-119">You don't really handle the connection this way.</span></span> <span data-ttu-id="1ac40-120">若要查看完整的實作，請參閱 [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) 存放庫中的實際程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ac40-120">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span> 

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

<span data-ttu-id="1ac40-121">eShopOnContainers 應用程式中發行方法的[實際程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)可透過使用 [Polly](https://github.com/App-vNext/Polly) 重試原則來改進，該原則會在 RabbitMQ 容器未就緒時，重試工作特定次數。</span><span class="sxs-lookup"><span data-stu-id="1ac40-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="1ac40-122">當 docker-compose 正在啟動容器時，就會發生此情況；例如，RabbitMQ 容器可能會比其他容器更慢啟動。</span><span class="sxs-lookup"><span data-stu-id="1ac40-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="1ac40-123">如前所述，RabbitMQ 中有許多可能的組態，因此這段程式碼只應該用於開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="1ac40-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="1ac40-124">使用 RabbitMQ API 實作訂閱程式碼</span><span class="sxs-lookup"><span data-stu-id="1ac40-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="1ac40-125">如同發行程式碼，下列程式碼是 RabbitMQ 之事件匯流排實作的一部分簡化。</span><span class="sxs-lookup"><span data-stu-id="1ac40-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="1ac40-126">同樣地，除非您想要改進，否則您通常不需要將它變更。</span><span class="sxs-lookup"><span data-stu-id="1ac40-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="1ac40-127">每個事件類型會有相關的通道以從 RabbitMQ 取得事件。</span><span class="sxs-lookup"><span data-stu-id="1ac40-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="1ac40-128">之後，您可以視需要針對每個通道和事件類型，擁有許多事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1ac40-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="1ac40-129">Subscribe 方法接受 IIntegrationEventHandler 物件，就像是目前微服務及其相關 IntegrationEvent 物件中的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="1ac40-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="1ac40-130">此程式碼接著會將該事件處理常式新增至事件處理常式清單，每個整合事件類型可根據每個用戶端微服務擁有這些事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1ac40-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="1ac40-131">如果用戶端程式碼尚未訂閱事件，程式碼會建立事件類型的通道，以便在從任何其他服務發行該事件時，可從 RabbitMQ 接收推送樣式的事件。</span><span class="sxs-lookup"><span data-stu-id="1ac40-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ac40-132">[上一頁](integration-event-based-microservice-communications.md)
>[下一頁](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="1ac40-132">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
