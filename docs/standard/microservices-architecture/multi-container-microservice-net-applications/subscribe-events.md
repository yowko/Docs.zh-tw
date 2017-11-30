---
title: "訂閱事件"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |訂閱事件"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: fe17b53a39ff2964cd60183e291e2936d3ba28df
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="subscribing-to-events"></a>訂閱事件

使用事件匯流排的第一個步驟是訂閱 microservices 他們想要接收的事件。 應在接收者 microservices 中完成。

下列簡單程式碼會顯示每個接收者微服務必須實作啟動服務時 （也就是在啟動類別中） 讓它訂閱事件它需要。 比方說，basket.api 微服務需要訂閱 ProductPriceChangedIntegrationEvent 訊息。 這對產品價格注意之任何變更的微服務，並讓它發出警告與變更相關的使用者，該產品是否在使用者的購物籃中。

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

執行此程式碼之後，「 訂閱者 」 的微服務會接聽透過 RabbitMQ 通道。 當類型 ProductPriceChangedIntegrationEvent 的任何訊息抵達時，程式碼會叫用傳遞給它，及處理事件的事件處理常式。

## <a name="publishing-events-through-the-event-bus"></a>事件匯流排透過發行事件

最後，訊息寄件者 （原點微服務） 整合將事件發行與下例類似的程式碼。 （這是簡化的範例不接受不可部份完成性納入考量）。每當事件必須傳播跨多個 microservices，通常是右資料或從原點微服務的交易認可之後，您也會實作類似的程式碼。

首先，事件匯流排實作物件 （根據 RabbitMQ 或服務匯流排上），將會插入在控制器建構函式，如下列程式碼所示：

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

然後您使用它從您的控制器方法，就像 UpdateProduct 方法中：

```csharp
[Route("update")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

在此情況下，由於原點微服務是簡單的 CRUD 微服務，該程式碼置於權限的 Web API 控制器。 在更進階的 microservices，它無法認可原始資料之後實作 CommandHandler 類別右中。

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>發行到事件匯流排時，設計不可部份完成性和恢復功能

當您發行透過分散式傳訊整合事件系統喜歡事件匯流排時，已自動更新原始資料庫並發行事件的問題。 比方說，在稍早所示簡化範例中，程式碼到資料庫認可資料的產品價格的變更，並接著將發佈 ProductPriceChangedIntegrationEvent 訊息時。 一開始，它看起來可能不可或缺的自動執行這兩項操作。 不過，如果您使用分散式的交易涉及的資料庫和訊息 broker，就像是在較舊的系統，例如[Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)，不建議這樣所描述的原因[CAP 理論](https://www.quora.com/What-Is-CAP-Theorem-1)。

基本上，您可以使用 microservices 建置可擴充、 高可用性的系統。 以稍微簡化，CAP 理論指出資料庫 （或擁有其模型的微服務） 無法建立持續可用、 強式一致性、*和*容許任何磁碟分割。 您必須選擇兩個這三個屬性。

在 microservices 架構中，您應該選擇可用性和容錯，，您應該強調強式一致性。 因此，在大多數最新型的微服務架構應用程式，通常不想使用分散式的交易，在訊息中，就像您實作[分散式交易](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c)根據 Windows 分散式交易協調器 (DTC) 與[MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)。

讓我們回到初始的問題和其範例。 在服務中止後資料庫的更新 (在此情況下，以滑鼠右鍵一行後面的程式碼與\_內容。SaveChangesAsync())，但發行整合事件之前，整體系統可能會不一致。 這可能是商務關鍵的視您正在處理的特定商務作業而定。

與上述架構 > 一節中，您可以有數個方式來處理這個問題：

-   使用完整[事件來源模式](https://msdn.microsoft.com/en-us/library/dn589792.aspx)。

-   使用[交易記錄採礦](http://www.scoop.it/t/sql-server-transaction-log-mining)。

-   使用[寄件匣模式](http://gistlabs.com/2014/05/the-outbox/)。 這是交易式的資料表，以儲存整合事件 （延伸本機交易）。

此案例中，使用完整的事件來源 (ES) 模式的其中一種最佳的方法，如果不是最佳。 不過，在許多應用程式案例中，您可能無法以實作完整的 ES 系統。 ES 表示只有網域事件儲存在您的交易式資料庫，而不是儲存目前的狀態資料。 儲存只有網域事件可以有極大的好處，例如您的系統提供的歷程記錄以及可以判斷在過去任何時間的系統狀態。 不過，實作完整的 ES 系統會要求您 rearchitect 大部分的系統，並導入了許多其他的複雜性和要求。 例如，您會想要使用資料庫，特別是對事件來源，例如[事件存放區](https://geteventstore.com/)，或文件導向的資料庫，例如 Azure Cosmos DB、 MongoDB、 Cassandra、 CouchDB 或 RavenDB。 ES 是最好的方法，這個問題，但不是最簡單的方法，除非您已熟悉事件來源。

若要使用採礦一開始的交易記錄檔選項看起來非常透明。 不過，若要使用這種方法，微服務有令人敬 RDBMS 交易記錄檔，例如 SQL Server 交易記錄檔。 這可能就不需要這樣做。 另一個缺點是，交易記錄檔中記錄的低層級更新可能會在相同層級為概要整合事件。 如果是這樣，反向工程的程序的交易記錄作業很難。

一種是交易式資料庫資料表和簡化的 ES 模式的混合。 您可以使用狀態，例如 「 已備妥可發行事件，「 您在原始的事件時認可整合事件資料表中設定。 您嘗試發行事件至事件匯流排時。 如果發行事件動作成功，您 origin 服務啟動另一個交易，並將狀態從 「 準備發行事件 」 移至 「 事件已發佈 」。

如果發行事件動作會在事件匯流排失敗，資料仍不會不一致的原點微服務內，它仍標示為 「 準備發佈事件 」，相對於其他的服務，它最終將一致。 您一律可以檢查整合事件之交易的狀態的背景工作。 如果工作中的 「 準備發行事件 」 的狀態，找到事件，它可以嘗試重新發行該事件，事件匯流排。

請注意，使用此方法時，您要保存只能每個來源微服務，整合事件與您想要傳達給其他 microservices 或外部系統的事件。 相較之下，在完整 ES 系統中，您會儲存所有網域事件以及。

因此，此平衡的方法是簡化的 ES 系統。 您需要一份整合事件及其目前狀態 （「 已準備好發佈 」 與 「 發行 」）。 但是，您只需要實作這些整合事件的狀態。 這種方法，您不需要將所有網域的資料都儲存為事件在交易式資料庫中，在完整的 ES 系統中一樣。

如果您已經使用關聯式資料庫，您可以使用交易式的資料表來儲存整合事件。 若要達到不可部份完成性應用程式中的，您可以使用本機交易為基礎的兩個步驟。 基本上，您有網域實體相同資料庫中有 IntegrationEvent 資料表。 該資料表會依照針對達到不可部份完成性，讓您包含保險保存整合事件認可網域資料的相同交易運作。

逐步解說，程序如下： 應用程式開始在本機資料庫交易。 然後更新您的網域實體的狀態，並且整合事件資料表中插入事件。 最後，它會認可交易。 您取得所需的不可部份完成性。

如果實作發行事件的步驟，則會有這些選項：

-   發行整合事件認可交易之後，權限，並使用另一個本機交易標示為正在發行資料表中的事件。 然後，追蹤整合事件發生問題的遠端 microservices，就像成品使用資料表，以及執行預存的整合事件為基礎的補償動作。

-   使用資料表做為一種佇列。 個別的應用程式執行緒或處理程序整合事件資料表中查詢、 將事件發行到事件匯流排，然後使用本機交易標記為已發佈的事件。

圖 8 到 22 顯示這些方法的第一個架構。

![](./media/image23.png)

**圖 8 到 22**。 不可部分完成性事件匯流排發佈事件時

圖 8 到 22 所述的方法遺漏負責檢查並確認成功的已發行的整合事件額外的背景工作微服務。 發生失敗時，該其他檢查工作者微服務可以讀取資料表中的事件，並將它們重新發行。

第二個方法： 使用事件記錄檔以資料表為佇列，並一律使用背景工作的微服務將訊息發佈。 在此情況下，處理程序是類似的顯示圖 8-23。 這會顯示其他的微服務，並發佈事件時，資料表會是單一來源。

![](./media/image24.png)

**圖 8-23**。 不可部分完成性與背景工作的微服務事件匯流排發佈事件時

為了簡化，eShopOnContainers 範例會使用第一個方法 （不含額外的處理序或檢查 microservices） 再加上事件匯流排。 不過，eShopOnContainers 並不會處理所有可能的失敗案例。 在實際的應用程式，部署至雲端，您也必須不怕事實會最後，會發生問題，您必須實作檢查並重新傳送的邏輯。 使用資料表為佇列可能會比第一種方法更有效，如果您有該資料表做為單一來源時發行它們透過事件匯流排的事件。

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>發行事件匯流排透過整合事件時實作不可部份完成性

下列程式碼將示範如何建立單一交易涉及多個 DbContext 物件-正在更新的原始資料相關的一個內容與第二個 IntegrationEventLog 資料表相關的內容。

請注意，下列範例程式碼中的交易將不會有彈性，如果資料庫的連接時執行程式碼時有任何問題。 這會發生在雲端為基礎的系統，例如 Azure SQL DB 可能會在伺服器之間移動資料庫。 跨多個內容中實作彈性的交易，請參閱[實作有彈性的 Entity Framework Core SQL 連接](#implementing_resilient_EFCore_SQL_conns)本指南中稍後的章節。

為了清楚起見，下列範例會顯示整個程序，在單一程式碼片段中。 不過，eShopOnContainers 實作實際重構，並將此邏輯分割成多個類別，因此很容易維護。

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult>
    UpdateProduct([FromBody]CatalogItem productToUpdate)
{
    var catalogItem = await _catalogContext.CatalogItems
        .SingleOrDefaultAsync(i => i.Id == productToUpdate.Id);

    if (catalogItem == null) return NotFound();

    bool raiseProductPriceChangedEvent = false;

    IntegrationEvent priceChangedEvent = null;

    if (catalogItem.Price != productToUpdate.Price)
        raiseProductPriceChangedEvent = true;

    if (raiseProductPriceChangedEvent) // Create event if price has changed
    {
        var oldPrice = catalogItem.Price;
        priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
            productToUpdate.Price,
            oldPrice);
    }

    // Update current product
    catalogItem = productToUpdate;
    // Achieving atomicity between original DB and the IntegrationEventLog
    // with a local transaction

    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);

        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if(raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
   }

   // Publish to event bus only if product price changed

   if (raiseProductPriceChangedEvent)
   {
       _eventBus.Publish(priceChangedEvent);
       integrationEventLogService.MarkEventAsPublishedAsync(
           priceChangedEvent);
   }

   return Ok();
}
```

建立 ProductPriceChangedIntegrationEvent 整合事件之後，會儲存原始網域作業 （更新類別目錄項目） 的交易也包含事件的持續性事件記錄檔資料表中。 如此便可在單一交易，並一律可以檢查是否已傳送事件訊息。

事件記錄檔資料表會自動更新與原始的資料庫作業，使用本機交易中針對相同的資料庫。 如果有任何作業失敗時，擲回例外狀況，交易回復任何已完成的作業，因此維護網域作業與傳送的事件訊息之間的一致性。

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>從訂閱接收訊息： 接收者 microservices 中的事件處理常式

除了事件訂閱邏輯，您需要實作整合事件處理常式 （例如回呼方法） 的內部程式碼。 此事件處理常式會是您可在此指定接收和處理特定類型的事件訊息。

事件處理常式，首先會從事件匯流排接收事件執行個體。 然後找出要處理的元件與整合事件傳播和保存為在接收者微服務的狀態變更事件。 比方說，如果 ProductPriceChanged 事件源自目錄微服務，它會在購物籃微服務中處理並變更以及，這個收件者籃微服務中的狀態，如下列程式碼所示。

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

此事件處理常式需要確認產品是否存在於任何購物籃的執行個體。 它也會更新每個相關的購物籃行項目的項目價格。 最後，它會建立與變更相關的價格，對使用者顯示警示示圖 8-24。

![](./media/image25.png)

**圖 8-24**。 顯示項目價格變動中為購物籃，傳達整合事件

## <a name="idempotency-in-update-message-events"></a>在更新訊息事件等冪

更新訊息事件的重要層面是在任何時間點的通訊失敗，應該會導致重試訊息。 否則背景工作可能會嘗試發佈已發行，建立競爭條件的事件。 您需要確定更新為等冪或它們提供足夠的資訊，以確保可以偵測到重複出現，捨棄它，並傳送回只有一個回應。

如前文所述，等冪性表示的作業可以執行多次而不會變更結果。 在傳訊環境中，為事件時進行通訊的事件，為等冪，如果可以傳遞多次而不需要變更接收者微服務的結果。 這可能需要由於的本質之事件本身，或因為系統會處理此事件。 訊息等冪性，請務必在任何使用傳訊應用程式中，不只是在執行事件匯流排模式的應用程式。

等冪運算的範例之一是將資料插入資料表，只有該資料不是已在資料表中的 SQL 陳述式。 就不重要了多少次您執行的 insert SQL 陳述式。結果會相同，表格將包含該資料。 視需要處理的訊息，如果可能無法傳送的訊息時，因此處理的一次，也可以是等冪以外，像這樣。 比方說，如果重試邏輯造成多次傳送相同訊息寄件者，您需要確定它是等冪。

它可設計具有等冪性訊息。 比方說，您可以建立事件，指出 」 設定的產品價格為\$25"而不是 「 新增\$產品價格的 5。 」 您可以安全地處理第一個訊息次數，結果會相同。 不針對第二個訊息，則為 true。 但是，即使在第一個案例中，您可能不想處理的第一個事件，因為系統可能也傳送較新的價格變更事件，而且您將會覆寫，新的價格。

另一個範例可能會傳播至多個 「 訂閱者 」 所造成的順序完成事件。 請務必，訂單資訊更新其他系統中只有一次，即使有重複的訊息相同的順序完成事件的事件。

並方便有某種類型的每個事件的識別，讓您可以建立邏輯，會強制執行每個事件會處理一次只能每個接收者。

某些訊息處理本質上是等冪。 比方說，如果系統會產生影像縮圖，就可能不重要產生縮圖的相關訊息已處理的次數結果會產生縮圖，以及它們是相同的每一次。 相反地，例如先呼叫信用卡付款閘道的作業可能不完全是等冪。 在這些情況下，您需要確保多次處理的訊息具有您預期的效果。

### <a name="additional-resources"></a>其他資源

-   **接受訊息等冪**（在此頁面上的子標題） [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>刪除重複資料整合事件訊息

您可以確保訊息事件是傳送，並只處理一次每個訂閱者在不同層級。 一種方式為使用您正在使用此訊息基礎結構所提供的重複資料刪除功能。 另一個是在您的目的地微服務中實作自訂邏輯。 驗證在傳輸層級和應用程式層級是您的最佳選擇。

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>刪除重複資料的訊息事件處理常式層級的事件

確定事件一次處理任何接收者的一個方式是藉由實作處理事件處理常式中的訊息事件時的特定邏輯。 例如，為 eShopOnContainers 應用程式中使用的方法中，您可以看到[原始程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs)OrdersController 類別收到 CreateOrderCommand 命令時。 （我們在此情況下使用的 HTTP 要求命令不是以訊息為基礎的指令，但是您必須先以訊息為基礎的命令等冪邏輯也很類似。）

### <a name="deduplicating-messages-when-using-rabbitmq"></a>刪除重複資料的訊息時使用 RabbitMQ

若間歇網路失敗，訊息可以重複，，而且訊息接收者必須準備好處理這些重複的訊息。 可能的話，接收者應該處理等冪的方式，優於明確重複資料刪除處理這些訊息。

根據[RabbitMQ 文件](https://www.rabbitmq.com/reliability.html#consumer)，「 如果將訊息傳遞至取用者，並再排入佇列，（因為它尚未被認可之前取用者中斷連線，例如），則 RabbitMQ 會設定已重新傳遞的旗標上它一次傳遞 （是否以相同的消費者或另一部） 時使用。

如果設定 「 已重新傳遞 」 的旗標，接收者必須考慮的帳戶，因為訊息可能已經處理。 但是，不一定。訊息可能永遠不會有之後，到達收件者從訊息代理人，可能是因為網路問題。 相反地，如果未設定 」 已重新傳遞 」 的旗標，這樣會保證的訊息已傳送一次以上。 因此，接收者使用重複資料刪除等冪的方式處理訊息的訊息中設定 「 已重新傳遞 」 旗標時，才需要。

### <a name="additional-resources"></a>其他資源

-   **事件驅動訊息**
    [*http://soapatterns.org/design\_模式/事件\_驅動\_傳訊*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard：重構朝向彈性： 評估結合**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **發行-訂閱通道**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **之間通訊的繫結內容**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)

-   **最終一致性**
    [*https://en.wikipedia.org/wiki/Eventual\_一致性*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Philip Brown。整合策略繫結內容**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Chris Richardson。開發使用彙總 」、 「 事件來源和 「 CQRS-第 2 部分的交易式 Microservices**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Chris Richardson。事件 Sourcing 模式**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)

-   **簡介 事件來源**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)

-   **事件存放區資料庫**。 官方網站。
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen。事件驅動的 Microservices 資料管理**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*

-   **CAP 理論**
    [*https://en.wikipedia.org/wiki/CAP\_理論*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **什麼是 CAP 理論？** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **資料一致性入門**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)

-   **Rick Saling。CAP 理論： 原因 」 的所有項目不同 「 雲端與網際網路**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric Brewer。CAP 十二年稍後： 如何變更 「 規則 」**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **參與外部 (DTC) 交易**(MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Azure 服務匯流排。代理訊息： 重複的偵測**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **可靠性指南**（RabbitMQ 文件） [ *https://www.rabbitmq.com/reliability.html\#取用者*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[上一個](rabbitmq-event-bus-development-test-environment.md) [下一步] (test-aspnet-core-services-web-apps.md)
