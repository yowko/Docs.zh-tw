---
title: 針對開發或測試環境使用 RabbitMQ 實作事件匯流排
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對開發或測試環境使用 RabbitMQ 實作事件匯流排
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: e2b0f1a6152df5d323164fb2eca102fcb973667e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>針對開發或測試環境使用 RabbitMQ 實作事件匯流排

首先您應該知道，如果您根據容器中所執行的 RabbitMQ 來建立自訂事件匯流排 (如同 eShopOnContainers 應用程式的做法)，則只能用於開發和測試環境。 除非您將它當做準備好用於生產環境之服務匯流排的一部分來建置，否則不應該用於生產環境中。 簡單的自訂事件匯流排可能會遺失許多商業服務匯流排所具備並可供生產環境使用的重要功能。

eShopOnContainers 的其中一個事件匯流排自訂實作基本上是使用 RabbitMQ API 的程式庫 (另一個實作是以 Azure 服務匯流排為依據)。 

使用 RabbitMQ 的事件匯流排實作可讓微服務訂閱事件、發行事件和接收事件，如圖 8-21 所示。

![](./media/image22.png)

**圖 8-21：** 事件匯流排的 RabbitMQ 實作

在程式碼中，EventBusRabbitMQ 類別會實作泛型 IEventBus 介面。 這是以相依性插入為基礎，因此您可以從此開發/測試版本切換至生產版本。

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

範例開發/測試事件匯流排的 RabbitMQ 實作是未定案程式碼。 它必須處理 RabbitMQ 伺服器的連接，並提供程式碼將訊息事件發行到佇列。 它也必須實作每個事件類型之整合事件處理常式集合的字典，這些事件類型可以針對每個接收器微服務有不同的具現化和不同的訂閱，如圖 8-21 所示。

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>使用 RabbitMQ 實作簡單的發行方法

下列程式碼是 RabbitMQ 之簡化事件匯流排的一部分，已在 eShopOnContainers 的[實際程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)中獲得改善。 除非您想要改進，否則您通常不需要撰寫其程式碼。 此程式碼會取得連至 RabbitMQ 的連接和通道、建立訊息，然後將訊息發行到佇列。

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

eShopOnContainers 應用程式中發行方法的[實際程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)可透過使用 [Polly](https://github.com/App-vNext/Polly) 重試原則來改進，該原則會在 RabbitMQ 容器未就緒時，重試工作特定次數。 當 docker-compose 正在啟動容器時，就會發生此情況；例如，RabbitMQ 容器可能會比其他容器更慢啟動。

如前所述，RabbitMQ 中有許多可能的組態，因此這段程式碼只應該用於開發/測試環境。

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>使用 RabbitMQ API 實作訂閱程式碼

如同發行程式碼，下列程式碼是 RabbitMQ 之事件匯流排實作的一部分簡化。 同樣地，除非您想要改進，否則您通常不需要將它變更。

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

每個事件類型會有相關的通道以從 RabbitMQ 取得事件。 之後，您可以視需要針對每個通道和事件類型，擁有許多事件處理常式。

Subscribe 方法接受 IIntegrationEventHandler 物件，就像是目前微服務及其相關 IntegrationEvent 物件中的回呼方法。 此程式碼接著會將該事件處理常式新增至事件處理常式清單，每個整合事件類型可根據每個用戶端微服務擁有這些事件處理常式。 如果用戶端程式碼尚未訂閱事件，程式碼會建立事件類型的通道，以便在從任何其他服務發行該事件時，可從 RabbitMQ 接收推送樣式的事件。


>[!div class="step-by-step"]
[上一個] (integration-event-based-microservice-communications.md) [下一個] (subscribe-events.md)
