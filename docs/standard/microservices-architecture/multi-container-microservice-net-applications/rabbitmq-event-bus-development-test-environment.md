---
title: "實作與 RabbitMQ 事件匯流排的開發或測試環境"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作與 RabbitMQ 事件匯流排的開發或測試環境"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f58d355b6f5fd31a21791d3b072c77f70f90c387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="a131d-104">實作與 RabbitMQ 事件匯流排的開發或測試環境</span><span class="sxs-lookup"><span data-stu-id="a131d-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="a131d-105">我們應該開始所說，是否您建立您的自訂事件匯流排根據 eShopOnContainers 應用程式會在容器中，執行 RabbitMQ，它應該只能用於您的開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="a131d-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="a131d-106">您應該不將它用於生產環境中，除非您正在建置它可實際執行的服務匯流排的一部分。</span><span class="sxs-lookup"><span data-stu-id="a131d-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="a131d-107">簡單的自訂事件匯流排可能會遺失許多商業服務匯流排具有可實際執行的重要功能。</span><span class="sxs-lookup"><span data-stu-id="a131d-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="a131d-108">事件匯流排 eShopOnContainers 自訂實作基本上是使用 RabbitMQ API 程式庫。</span><span class="sxs-lookup"><span data-stu-id="a131d-108">The eShopOnContainers custom implementation of an event bus is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="a131d-109">實作讓 microservices 訂閱事件、 事件、 發行和接收事件，如圖 8-21 所示。</span><span class="sxs-lookup"><span data-stu-id="a131d-109">The implementation lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="a131d-110">**圖 8-21。**</span><span class="sxs-lookup"><span data-stu-id="a131d-110">**Figure 8-21.**</span></span> <span data-ttu-id="a131d-111">事件匯流排的 RabbitMQ 實作</span><span class="sxs-lookup"><span data-stu-id="a131d-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="a131d-112">在程式碼的 EventBusRabbitMQ 類別會實作泛型 IEventBus 介面。</span><span class="sxs-lookup"><span data-stu-id="a131d-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="a131d-113">這根據相依性插入，因此，您可以交換從此開發/測試版本的實際執行版本。</span><span class="sxs-lookup"><span data-stu-id="a131d-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="a131d-114">範例開發/測試事件匯流排的 RabbitMQ 實作是未定案程式碼。</span><span class="sxs-lookup"><span data-stu-id="a131d-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="a131d-115">必須處理 RabbitMQ 伺服器的連線，並提供程式碼發行至佇列的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="a131d-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="a131d-116">它也必須實作的每個事件類型; 整合事件處理常式集合的字典這些事件類型可以有不同的具現化和不同的訂用帳戶的每個接收者微服務，如圖 8-21 所示。</span><span class="sxs-lookup"><span data-stu-id="a131d-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="a131d-117">實作簡單發行具有 RabbitMQ 方法</span><span class="sxs-lookup"><span data-stu-id="a131d-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="a131d-118">下列程式碼是 RabbitMQ，eShopOnContainers 事件匯流排實作的一部分，因此您通常不需要進行改良，除非程式碼。</span><span class="sxs-lookup"><span data-stu-id="a131d-118">The following code is part of the eShopOnContainers event bus implementation for RabbitMQ, so you usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="a131d-119">程式碼取得的連接和 RabbitMQ 的通道，建立訊息，並再將訊息發佈到佇列。</span><span class="sxs-lookup"><span data-stu-id="a131d-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="a131d-120">[實際程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)的 發佈 eShopOnContainers 應用程式中的方法使用來改善[Polly](https://github.com/App-vNext/Polly)重試原則，重試工作特定數目的時間，以防 RabbitMQ 容器未就緒。</span><span class="sxs-lookup"><span data-stu-id="a131d-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="a131d-121">發生此情況時 docker 撰寫正在啟動容器。例如，可能會比其他容器的放慢啟動 RabbitMQ 容器。</span><span class="sxs-lookup"><span data-stu-id="a131d-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="a131d-122">如先前所述，有許多可能的組態中 RabbitMQ，因此這段程式碼應該只能用於開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="a131d-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="a131d-123">實作 RabbitMQ API 與訂用帳戶程式碼</span><span class="sxs-lookup"><span data-stu-id="a131d-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="a131d-124">發行程式碼後，下列程式碼是一部分的簡化主機的 RabbitMQ 事件匯流排實作。</span><span class="sxs-lookup"><span data-stu-id="a131d-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="a131d-125">同樣地，通常您不需要變更它，除非可改善。</span><span class="sxs-lookup"><span data-stu-id="a131d-125">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...
    public void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent
    {
        var eventName = typeof(T).Name;
        if (_handlers.ContainsKey(eventName))
        {
            _handlers[eventName].Add(handler);
        }
        else
        {
            var channel = GetChannel();
            channel.QueueBind(queue: _queueName,
                exchange: _brokerName,
                routingKey: eventName);
            _handlers.Add(eventName, new List<IIntegrationEventHandler>());
            _handlers[eventName].Add(handler);
            _eventTypes.Add(typeof(T));
        }
    }
}
```

<span data-ttu-id="a131d-126">每個事件類型有從 RabbitMQ 取得事件的相關的通道。</span><span class="sxs-lookup"><span data-stu-id="a131d-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="a131d-127">接著，您可以讓每個通道和事件類型，視需要最多的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a131d-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="a131d-128">Subscribe 方法接受 IIntegrationEventHandler 物件，這就像在目前的微服務的回呼方法，再加上其相關的 IntegrationEvent 物件。</span><span class="sxs-lookup"><span data-stu-id="a131d-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="a131d-129">然後程式碼會將該事件處理常式加入每個用戶端微服務有每個整合的事件類型的事件處理常式的清單中。</span><span class="sxs-lookup"><span data-stu-id="a131d-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="a131d-130">如果用戶端程式碼已經並未訂閱事件，程式碼會建立事件類型的通道，所以從任何其他服務便會發行該事件時，它可以發送樣式會與 RabbitMQ 接收事件。</span><span class="sxs-lookup"><span data-stu-id="a131d-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a131d-131">[上一個](整合-事件為基礎的微服務-communications.md) [下一步] (訂閱 events.md)</span><span class="sxs-lookup"><span data-stu-id="a131d-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
