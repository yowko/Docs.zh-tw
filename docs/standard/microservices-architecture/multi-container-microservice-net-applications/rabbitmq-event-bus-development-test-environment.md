---
title: 針對開發或測試環境使用 RabbitMQ 實作事件匯流排
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對開發或測試環境使用 RabbitMQ 實作事件匯流排
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: fb9bf51d947774cddd7b42ade0f05abc8fb3d7e9
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104749"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="5efc2-103">針對開發或測試環境使用 RabbitMQ 實作事件匯流排</span><span class="sxs-lookup"><span data-stu-id="5efc2-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="5efc2-104">首先您應該知道，如果您根據容器中所執行的 RabbitMQ 來建立自訂事件匯流排 (如同 eShopOnContainers 應用程式的做法)，則只能用於開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="5efc2-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="5efc2-105">除非您將它當做準備好用於生產環境之服務匯流排的一部分來建置，否則不應該用於生產環境中。</span><span class="sxs-lookup"><span data-stu-id="5efc2-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="5efc2-106">簡單的自訂事件匯流排可能會遺失許多商業服務匯流排所具備並可供生產環境使用的重要功能。</span><span class="sxs-lookup"><span data-stu-id="5efc2-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="5efc2-107">eShopOnContainers 的其中一個事件匯流排自訂實作基本上是使用 RabbitMQ API 的程式庫 (另一個實作是以 Azure 服務匯流排為依據)。</span><span class="sxs-lookup"><span data-stu-id="5efc2-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span> 

<span data-ttu-id="5efc2-108">使用 RabbitMQ 的事件匯流排實作可讓微服務訂閱事件、發行事件和接收事件，如圖 8-21 所示。</span><span class="sxs-lookup"><span data-stu-id="5efc2-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="5efc2-109">**圖 8-21：**</span><span class="sxs-lookup"><span data-stu-id="5efc2-109">**Figure 8-21.**</span></span> <span data-ttu-id="5efc2-110">事件匯流排的 RabbitMQ 實作</span><span class="sxs-lookup"><span data-stu-id="5efc2-110">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="5efc2-111">在程式碼中，EventBusRabbitMQ 類別會實作泛型 IEventBus 介面。</span><span class="sxs-lookup"><span data-stu-id="5efc2-111">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="5efc2-112">這是以相依性插入為基礎，因此您可以從此開發/測試版本切換至生產版本。</span><span class="sxs-lookup"><span data-stu-id="5efc2-112">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="5efc2-113">範例開發/測試事件匯流排的 RabbitMQ 實作是未定案程式碼。</span><span class="sxs-lookup"><span data-stu-id="5efc2-113">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="5efc2-114">它必須處理 RabbitMQ 伺服器的連接，並提供程式碼將訊息事件發行到佇列。</span><span class="sxs-lookup"><span data-stu-id="5efc2-114">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="5efc2-115">它也必須實作每個事件類型之整合事件處理常式集合的字典，這些事件類型可以針對每個接收器微服務有不同的具現化和不同的訂閱，如圖 8-21 所示。</span><span class="sxs-lookup"><span data-stu-id="5efc2-115">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="5efc2-116">使用 RabbitMQ 實作簡單的發行方法</span><span class="sxs-lookup"><span data-stu-id="5efc2-116">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="5efc2-117">下列程式碼是 RabbitMQ 之簡化事件匯流排的一部分，已在 eShopOnContainers 的[實際程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)中獲得改善。</span><span class="sxs-lookup"><span data-stu-id="5efc2-117">The following code is part is a simplified event bus implementation for RabbitMQ, improved in the [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of eShopOnContainers.</span></span> <span data-ttu-id="5efc2-118">除非您想要改進，否則您通常不需要撰寫其程式碼。</span><span class="sxs-lookup"><span data-stu-id="5efc2-118">You usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="5efc2-119">此程式碼會取得連至 RabbitMQ 的連接和通道、建立訊息，然後將訊息發行到佇列。</span><span class="sxs-lookup"><span data-stu-id="5efc2-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="5efc2-120">eShopOnContainers 應用程式中發行方法的[實際程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)可透過使用 [Polly](https://github.com/App-vNext/Polly) 重試原則來改進，該原則會在 RabbitMQ 容器未就緒時，重試工作特定次數。</span><span class="sxs-lookup"><span data-stu-id="5efc2-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="5efc2-121">當 docker-compose 正在啟動容器時，就會發生此情況；例如，RabbitMQ 容器可能會比其他容器更慢啟動。</span><span class="sxs-lookup"><span data-stu-id="5efc2-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="5efc2-122">如前所述，RabbitMQ 中有許多可能的組態，因此這段程式碼只應該用於開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="5efc2-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="5efc2-123">使用 RabbitMQ API 實作訂閱程式碼</span><span class="sxs-lookup"><span data-stu-id="5efc2-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="5efc2-124">如同發行程式碼，下列程式碼是 RabbitMQ 之事件匯流排實作的一部分簡化。</span><span class="sxs-lookup"><span data-stu-id="5efc2-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="5efc2-125">同樣地，除非您想要改進，否則您通常不需要將它變更。</span><span class="sxs-lookup"><span data-stu-id="5efc2-125">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="5efc2-126">每個事件類型會有相關的通道以從 RabbitMQ 取得事件。</span><span class="sxs-lookup"><span data-stu-id="5efc2-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="5efc2-127">之後，您可以視需要針對每個通道和事件類型，擁有許多事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5efc2-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="5efc2-128">Subscribe 方法接受 IIntegrationEventHandler 物件，就像是目前微服務及其相關 IntegrationEvent 物件中的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="5efc2-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="5efc2-129">此程式碼接著會將該事件處理常式新增至事件處理常式清單，每個整合事件類型可根據每個用戶端微服務擁有這些事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5efc2-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="5efc2-130">如果用戶端程式碼尚未訂閱事件，程式碼會建立事件類型的通道，以便在從任何其他服務發行該事件時，可從 RabbitMQ 接收推送樣式的事件。</span><span class="sxs-lookup"><span data-stu-id="5efc2-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5efc2-131">[上一頁](integration-event-based-microservice-communications.md)
[下一頁](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="5efc2-131">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
