---
title: "訂閱事件"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 訂閱事件"
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
ms.openlocfilehash: 7538c760d396349fe9b1e93a21839e3e59d7f046
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="subscribing-to-events"></a>訂閱事件

使用事件匯流排的第一個步驟是訂閱所要接收之事件的微服務。 這應該在接收者微服務中完成。

下列簡單程式碼顯示每個接收者微服務在啟動服務時必須實作的項目 (也就是在 `Startup` 類別中)，以便訂閱所需的事件。 在本例中，`basket.api` 微服務需要訂閱 `ProductPriceChangedIntegrationEvent` 和 `OrderStartedIntegrationEvent` 訊息。 

例如，訂閱 `ProductPriceChangedIntegrationEvent` 事件時，可讓購物籃微服務注意到產品價格的任何變更，並在使用者的購物籃中有該項產品時，警告使用者有此變更。

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

執行此程式碼之後，訂閱者微服務會透過 RabbitMQ 通道接聽。 當 ProductPriceChangedIntegrationEvent 類型的任何訊息抵達時，程式碼會叫用傳遞給它的事件處理常式並處理事件。

## <a name="publishing-events-through-the-event-bus"></a>透過事件匯流排發行事件

最後，訊息傳送者 (來源微服務) 會使用類似下列範例的程式碼發行整合事件 (這是經過簡化的範例，不可部分完成性不在考量範圍內)。只要必須在多個微服務之間傳播事件 (通常是在從來源微服務認可資料或交易之後)，您就會實作類似的程式碼。

首先，事件匯流排實作物件 (採用 RabbitMQ 或採用服務匯流排) 會插入控制器建構函式，如下列程式碼所示：

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

然後，您可以從控制器的方法使用它，就像是在 UpdateProduct 方法中一樣：

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

在本例中，由於來源微服務是簡單的 CRUD 微服務，因此該程式碼會直接放在 Web API 控制器中。 
 
在更進階的微服務中，例如使用 CQRS 方法時，它可以在 `Handle()` 方法的 `CommandHandler` 類別中實作。 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>設計發行至事件匯流排時的不可部分完成性和復原

當您透過分散式傳訊系統 (例如您的事件匯流排) 發行整合事件時，會發生以不可分割方式更新原始資料庫和發行事件的問題。 例如，在稍早所示的簡化範例中，程式碼會在產品價格變更時將資料認可至資料庫，然後發行 ProductPriceChangedIntegrationEvent 訊息。 乍看之下，以不可分割方式執行這兩個作業可能很重要。 不過，如果您使用涉及資料庫和訊息代理程式的分散式交易，如同您在 [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx) 等較舊系統中的做法，則不建議這樣做，原因如 [CAP 定理](https://www.quora.com/What-Is-CAP-Theorem-1)所述。

基本上，您可以使用微服務來建置可擴充且高度可用的系統。 簡單來說，CAP 定理指出您無法建置持續可用、強式一致「且」容許任何分割的資料庫 (或擁有自己模型的微服務)。 您必須從這三個屬性中選擇兩個。

在微服務架構中，您應該選擇可用性和容錯，而且您應該不要強調強式一致性。 因此，在大多數現代化微服務架構應用程式中，您通常不想要在傳訊中使用分散式交易 (就像是使用 [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx) 實作以 Windows Distributed Transaction Coordinator (DTC) 為基礎的[分散式交易](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c)時一樣)。

讓我們回到一開始的問題及其範例。 如果服務損毀發生在更新資料庫之後 (在本例中會是具有 \_context.SaveChangesAsync() 的程式碼行之後)，但在發行整合事件之前，整體系統可能會變成不一致。 視您正在處理的特定商務作業而定，這可能具商務關鍵性。

如稍早的＜架構＞一節中所述，您有數個方法可解決這個問題：

-   使用完整的[事件溯源模式](https://msdn.microsoft.com/library/dn589792.aspx)。

-   使用[交易記錄採礦](http://www.scoop.it/t/sql-server-transaction-log-mining)。

-   使用[寄件匣模式](http://gistlabs.com/2014/05/the-outbox/)。 這是交易式資料表，可儲存整合事件 (以延伸本機交易)。

在此案例中，使用完整的事件溯源 (ES) 模式即使不是「最佳」方法，也是最佳方法之一。 不過，在許多應用程式案例中，您可能無法實作完整的 ES 系統。 ES 表示只會將領域事件儲存在您的交易式資料庫中，而不會儲存目前的狀態資料。 只儲存領域事件可能有許多好處，例如提供系統歷程記錄，以及能夠判斷過去任何時間的系統狀態。 不過，實作完整的 ES 系統需要您重新架構大部分的系統，因而引進許多其他的複雜度和需求。 例如，您會想要使用專為事件溯源所建立的資料庫 (例如[事件存放區](https://geteventstore.com/))，或文件導向資料庫 (例如 Azure Cosmos DB、MongoDB、Cassandra、CouchDB 或 RavenDB)。 ES 是解決這個問題的最好方法，但除非您已熟悉事件溯源，否則並不是最簡單的解決方法。

使用交易記錄採礦的選項一開始看起來很簡單。 不過，若要使用此方法，微服務必須與 RDBMS 交易記錄結合，例如 SQL Server 交易記錄。 這可能不適當。 另一個缺點是，交易記錄中記錄的低層級更新可能不會與高層級整合事件位於相同層級。 如果是這樣，可能會很難處理這些交易記錄作業的反向工程。

一個平衡的方法是混合交易式資料庫資料表和簡化的 ES 模式。 您可以使用「準備發行事件」等狀態，當您將它認可至整合事件資料表時，會在原始事件中設定此狀態。 然後，您可以嘗試將事件發行至事件匯流排。 如果發行事件動作成功，您可以啟動來源服務中的另一個交易，並將狀態從「準備發行事件」移至「事件已發行」。

如果事件匯流排中的發行事件動作失敗，來源微服務中的資料不會一直處於不一致的狀態 (它仍標示為「準備發行事件」，但對於其餘服務而言，它最終將會一致)。 您一律可以讓背景工作檢查整合事件的交易狀態。 如果工作發現事件處於「準備發行事件」狀態，它可以嘗試將該事件重新發行至事件匯流排。

請注意，使用此方法，您只會保存每個來源微服務的整合事件，以及您要傳達給其他微服務或外部系統的事件。 相較之下，在完整的 ES 系統中，您也會儲存所有領域事件。

因此，此平衡的方法是簡化的 ES 系統。 您需要一份整合事件及其目前狀態 (「準備發行」與「已發行」) 的清單。 但是，您只需要實作整合事件的這些狀態。 此外，在此方法中，您不需要如同在完整的 ES 系統中，將所有領域資料儲存為交易式資料庫中的事件。

如果您已使用關聯式資料庫，您可以使用交易式資料表來儲存整合事件。 若要達到應用程式中的不可部分完成性，您可以使用以本機交易為基礎的雙步驟程序。 基本上，您在具有領域實體的相同資料庫中會有 IntegrationEvent 資料表。 該資料表可確保達到不可部分完成性，讓您在認可領域資料的相同交易中包含持續性整合事件。

逐步程序如下：應用程式開始本機資料庫交易。 它接著會更新您的領域實體狀態，並將事件插入整合事件資料表。 最後，它會認可交易。 您會取得所需的不可部分完成性。

實作發行事件的步驟時，您有下列選擇：

-   在認可交易之後直接發行整合事件，並使用另一個本機交易將資料表中的事件標示為已發行。 然後，使用資料表作為成品，以在遠端微服務發生問題時追蹤整合事件，並根據儲存的整合事件來執行補償動作。

-   使用資料表作為一種佇列。 另一個應用程式執行緒或處理序會查詢整合事件資料表、將事件發行至事件匯流排，然後使用本機交易將事件標示為已發行。

圖 8-22 顯示上述第一個方法的架構。

![](./media/image23.png)

**圖 8-22**： 將事件發行至事件匯流排時的不可部分完成性

圖 8-22 中所述的方法遺漏負責檢查並確認已發行整合事件是否成功的額外背景工作微服務。 失敗時，該額外的檢查背景工作微服務會從資料表讀取事件並重新發行。

關於第二個方法：您會使用 EventLog 資料表作為佇列，且一律會使用背景工作微服務來發行訊息。 在此情況下，其流程會如圖 8-23 所示。 圖中顯示額外的微服務，而且資料表是發行事件時的單一來源。

![](./media/image24.png)

**圖 8-23**： 使用背景工作微服務將事件發行至事件匯流排時的不可部分完成性

為了簡化起見，eShopOnContainers 範例使用第一個方法 (沒有額外的處理序或檢查微服務) 再加上事件匯流排。 不過，eShopOnContainers 並不會處理所有可能的失敗案例。 在部署至雲端的實際應用程式中，您必須體認到該問題終究會發生，而且您必須實作該檢查並重新傳送邏輯。 如果當您透過事件匯流排發行事件時，您有資料表作為單一事件來源，使用資料表作為佇列可能會比第一個方法更有效。

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>透過事件匯流排發行整合事件時實作不可部分完成性

下列程式碼示範如何建立涉及多個 DbContext 物件的單一交易：一個內容與要更新的原始資料相關，第二個內容與 IntegrationEventLog 資料表相關。

請注意，如果資料庫連接在執行程式碼時發生任何問題，下列範例程式碼中的交易將不會復原。 在 Azure SQL DB 等雲端式系統中，由於可能會在伺服器之間移動資料庫，因此可能會發生此情況。 若要在多個內容之間實作復原交易，請參閱本指南稍後的[實作具有恢復功能的 Entity Framework Core SQL 連接](#implementing_resilient_EFCore_SQL_conns)一節。

為了清楚起見，下列範例會在單一程式碼片段中顯示整個程序。 不過，eShopOnContainers 實作實際上已重構，並將此邏輯分割成多個類別，因此很容易維護。

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate) 
{
  var catalogItem = 
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id == 
                                                               productToUpdate.Id); 
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

  // Just save the updated product if the Product's Price hasn't changed.
  if !(raiseProductPriceChangedEvent) 
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
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

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

建立 ProductPriceChangedIntegrationEvent 整合事件之後，儲存原始領域作業 (更新目錄項目) 的交易也會在 EventLog 資料表中包含事件的持續性。 這會使它成為單一交易，而且您一律可以檢查是否已傳送事件訊息。

事件記錄檔資料表已透過原始資料庫作業以不可分割方式更新，並對相同的資料庫使用本機交易。 如果有任何作業失敗，則會擲回例外狀況，且交易會回復任何已完成的作業，因此領域作業與已傳送事件訊息之間會維持一致性。

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>從訂閱接收訊息：接收者微服務中的事件處理常式

除了事件訂閱邏輯之外，您還需要實作整合事件處理常式的內部程式碼 (例如回呼方法)。 此事件處理常式是您指定特定類型之事件訊息接收和處理的位置。

事件處理常式會先從事件匯流排接收事件執行個體。 然後，它會找出要處理且與該整合事件相關的元件，並在接收者微服務中的狀態變更時傳播及保存事件。 例如，如果 ProductPriceChanged 事件源自目錄微服務，則會在購物籃微服務中處理，也會變更此接收者購物籃微服務中的狀態，如下列程式碼所示。

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

事件處理常式需要確認產品是否存在於任何購物籃執行個體中。 它也會更新每個相關購物籃明細項目的項目價格。 最後，它會建立一個警示向使用者顯示此價格變更，如圖 8-24 所示。

![](./media/image25.png)

**圖 8-24**： 顯示購物籃中的項目價格變更，如整合事件所傳達

## <a name="idempotency-in-update-message-events"></a>更新訊息事件中的等冪性

更新訊息事件的一個重點是，通訊期間任何時間失敗都應該導致重試訊息。 否則，背景工作可能會嘗試發行已發行的事件，並建立競爭條件。 您需要確定更新為等冪或提供足夠的資訊，以確保您可以偵測重複項、將它捨棄，並只傳回一個回應。

如稍早所述，等冪性表示作業可執行多次而不會變更結果。 在傳訊環境中，當傳達事件時，如果可傳遞事件多次而不會變更接收者微服務的結果，事件會是等冪。 由於事件本身的本質，或由於系統處理事件的方式，這可能會是必要條件。 訊息等冪性在使用傳訊的任何應用程式中都很重要，不是只有在實作事件匯流排模式的應用程式中才重要。

等冪作業的一個範例是 SQL 陳述式，該陳述式只有在資料表中還沒有資料時，才會將該資料插入資料表。 該 INSERT SQL 陳述式的執行次數並不重要；結果會相同，資料表將會包含該資料。 如果可能不只一次傳送並處理訊息，當處理訊息時，也可能需要類似的等冪性。 例如，如果重試邏輯導致傳送者多次傳送完全相同的訊息，您需要確定它是等冪的。

您可以設計等冪訊息。 例如，您可以建立事件，指出「將產品價格設定為 \$25」，而不是「將 \$5 新增至產品價格」。 您可以安全地處理第一則訊息不限次數，結果會相同。 第二則訊息則不然。 但即使是在第一個案例中，您可能不想要處理第一個事件，因為系統也可能已傳送較新的價格變更事件，而且您將覆寫新價格。

另一個範例可能是將訂單已完成事件傳播至多個訂閱者。 請確保只在其他系統中更新訂單資訊一次，即使同一個訂單已完成事件有重複的訊息事件亦然。

讓每個事件有某種識別會方便您建立邏輯，以強制每個接收者只處理每個事件一次。

某些訊息處理本來就具等冪性。 例如，如果系統會產生影像縮圖，處理所產生縮圖的相關訊息多少次可能不重要，結果會產生縮圖，而且每次都一樣。 相反地，呼叫付款閘道來支付信用卡之類的作業可能不完全具等冪性。 在這些情況下，您需要確保多次處理訊息的效果符合您的預期。

### <a name="additional-resources"></a>其他資源

-   **Honoring message idempotency (允許訊息等冪性)** (此頁面上的次標題) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>刪除重複的整合事件訊息

您可以確保不同層級的每個訂閱者只傳送及處理一次訊息事件。 一個方法是使用您正在使用之傳訊基礎結構所提供的重複資料刪除功能。 另一個方法是在您的目的地微服務中實作自訂邏輯。 最好是在傳輸層和應用程式層都有驗證。

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>在 EventHandler 層級刪除重複的訊息事件

若要確定任何接收者只處理一次事件，一個方式是在處理事件處理常式中的訊息事件時實作特定邏輯。 例如，當它接收 CreateOrderCommand 命令時，這會是 eShopOnContainers 應用程式中所使用的方法，如 OrdersController 類別的[原始程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs)中所示 (在本例中，我們使用 HTTP 要求命令，而不是訊息式命令，但您需要使訊息式命令等冪的邏輯很類似)。

### <a name="deduplicating-messages-when-using-rabbitmq"></a>使用 RabbitMQ 時刪除重複的訊息

發生間歇性網路失敗時，訊息可能會重複，因此訊息接收者必須準備處理這些重複的訊息。 可能的話，接收者應該以等冪方式來處理這些訊息，這會比使用重複資料刪除功能來明確處理這些訊息還要理想。

根據 [RabbitMQ 文件](https://www.rabbitmq.com/reliability.html#consumer)，「如果將訊息傳遞給取用者，然後要求訊息 (例如因為取用者在中斷連線之前未認可訊息)，則 RabbitMQ 會在再次傳遞訊息時 (不論是對相同的取用者或不同的取用者)，設定訊息的 redelivered 旗標。

如果設定了 “redelivered” 旗標，接收者必須將此列入考量，因為可能已處理訊息。 但不保證一定如此，訊息在離開訊息代理程式之後可能從未抵達接收者 (或許因為網路問題)。 相反地，如果未設定 “redelivered” 旗標，就會保證訊息不會多次傳送。 因此，只有訊息中已設定 “redelivered” 旗標時，接收者才必須刪除重複的訊息或以等冪方式處理訊息。

### <a name="additional-resources"></a>其他資源

-   **使用 NServiceBus 的分支 eShopOnContainers (Particular Software)**
    [*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)

-   **Event-Driven Messaging (事件驅動傳訊)**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard：Refactoring Towards Resilience: Evaluating Coupling (傾向復原的重構：評估結合)**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Publish-Subscribe channel (發行訂閱通道)**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Communicating Between Bounded Contexts (在限定內容之間通訊)**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Eventual consistency (最終一致性)**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Philip Brown：Strategies for Integrating Bounded Contexts (整合限定內容的策略)**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Chris Richardson：Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2 (使用彙總、事件溯源和 CQRS 開發交易式微服務 - 第二部分)**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Chris Richardson：Pattern: Event sourcing (模式：事件溯源)**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)

-   **Introducing Event Sourcing (事件溯源簡介)**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)

-   **Event Store 資料庫**. 官方網站。
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen：Event-Driven Data Management for Microservices (微服務的事件導向資料管理)**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   **CAP 定理**
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **What Is CAP Theorem? (什麼是 CAP 定理？)**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Data Consistency Primer (資料一致性入門)**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Rick Saling：The CAP Theorem: Why “Everything is Different” with the Cloud and Internet (CAP 定理：為什麼雲端和網際網路的「所有一切都不同」)**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric Brewer：CAP Twelve Years Later: How the "Rules" Have Changed (12 年後的 CAP：「規則」有何改變)**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Participating in External (DTC) Transactions (參與外部 (DTC) 交易)** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Azure 服務匯流排：Brokered Messaging: Duplicate Detection (代理傳訊：重複資料偵測)**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Reliability Guide (可靠性指南)** (RabbitMQ 文件) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[上一個] (rabbitmq-event-bus-development-test-environment.md) [下一個] (test-aspnet-core-services-web-apps.md)
