---
title: 訂閱事件
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 了解發佈及訂閱整合事件的詳細資料。
ms.date: 01/13/2021
ms.openlocfilehash: c9146ddbdfbf00e743108c07af1f74d7690a17a8
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188721"
---
# <a name="subscribing-to-events"></a>訂閱事件

使用事件匯流排的第一個步驟是訂閱所要接收之事件的微服務。 這項功能應該在接收者微服務中完成。

下列簡單程式碼顯示每個接收者微服務在啟動服務時必須實作的項目 (也就是在 `Startup` 類別中)，以便訂閱所需的事件。 在本例中，`basket-api` 微服務需要訂閱 `ProductPriceChangedIntegrationEvent` 和 `OrderStartedIntegrationEvent` 訊息。

比方說，在訂閱事件時， `ProductPriceChangedIntegrationEvent` 這會讓購物籃微服務知道產品價格的任何變更，並讓使用者在使用者的購物籃中有該產品的變更時警告使用者。

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

執行此程式碼之後，訂閱者微服務會透過 RabbitMQ 通道接聽。 當 ProductPriceChangedIntegrationEvent 類型的任何訊息抵達時，程式碼會叫用傳遞給它的事件處理常式並處理事件。

## <a name="publishing-events-through-the-event-bus"></a>透過事件匯流排發行事件

最後，訊息傳送者 (來源微服務) 會使用類似下列範例的程式碼發行整合事件  (這種方法是簡化的範例，並不會將不可部分完成性納入考慮。 ) 您只要在多個微服務之間傳播事件，通常會在從原始微服務認可資料或交易之後，執行類似的程式碼。

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

然後，從控制器的方法中使用它，就像在 UpdateProduct 方法中一樣：

```csharp
[Route("items")]
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

當您透過分散式傳訊系統 (例如您的事件匯流排) 發佈整合事件時，會發生以不可部分完成方式更新原始資料庫及發佈事件的問題 (也就是兩個作業皆完成或皆未完成)。 例如，在稍早所示的簡化範例中，程式碼會在產品價格變更時將資料認可至資料庫，然後發行 ProductPriceChangedIntegrationEvent 訊息。 乍看之下，以不可分割方式執行這兩個作業可能很重要。 但是，如果您使用的分散式交易牽涉到資料庫和訊息代理程式，就像您在 [Microsoft Message Queuing (MSMQ) ](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))等舊版系統中所做的一樣，基於 [CAP 定理](https://www.quora.com/What-Is-CAP-Theorem-1)所述的原因不建議使用此方法。

基本上，您可以使用微服務來建置可擴充且高度可用的系統。 簡單來說，CAP 定理指出您無法建立 (分散式) 資料庫 (或擁有其模型) 持續可用、高度一致 *且* 可容忍任何資料分割的微服務。 您必須從這三個屬性中選擇兩個。

在以微服務為基礎的架構中，您應該選擇可用性和容錯功能，而且應該消除強式一致性。 因此，在大多數現代化微服務架構應用程式中，您通常不想要在傳訊中使用分散式交易 (就像是使用 [MSMQ](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)) 實作以 Windows Distributed Transaction Coordinator (DTC) 為基礎的[分散式交易](/previous-versions/windows/desktop/ms681205(v=vs.85))時一樣)。

讓我們回到初始問題及其範例。 如果服務在更新資料庫之後損毀 (在這種情況下，請在程式程式碼後面 `_context.SaveChangesAsync()`) ，但在整合事件發行之前，整體系統可能會不一致。 這種方法可能是商務關鍵性的，視您處理的特定商務操作而定。

如稍早的＜架構＞一節中所述，您有數個方法可解決這個問題：

- 使用完整的[事件溯源模式](/azure/architecture/patterns/event-sourcing)。

- 使用交易記錄採礦。

- 使用[寄件匣模式](https://www.kamilgrzybek.com/design/the-outbox-pattern/)。 這是交易式資料表，可儲存整合事件 (以延伸本機交易)。

在此案例中，使用完整的事件溯源 (ES) 模式即使不是「最佳」方法，也是最佳方法之一。 不過，在許多應用程式案例中，您可能無法實作完整的 ES 系統。 ES 表示只會將領域事件儲存在您的交易式資料庫中，而不會儲存目前的狀態資料。 只儲存領域事件可能有許多好處，例如提供系統歷程記錄，以及能夠判斷過去任何時間的系統狀態。 不過，實作完整的 ES 系統需要您重新架構大部分的系統，因而引進許多其他的複雜度和需求。 例如，您會想要使用專為事件溯源所建立的資料庫 (例如[事件存放區](https://eventstore.org/))，或文件導向資料庫 (例如 Azure Cosmos DB、MongoDB、Cassandra、CouchDB 或 RavenDB)。 ES 是解決這個問題的最好方法，但除非您已熟悉事件溯源，否則並不是最簡單的解決方法。

使用交易記錄挖掘的選項一開始看起來是透明的。 不過，若要使用此方法，微服務必須與 RDBMS 交易記錄結合，例如 SQL Server 交易記錄。 這種方法可能不理想。 另一個缺點是，交易記錄中記錄的低層級更新可能不會與高層級整合事件位於相同層級。 如果是這樣，可能會很難處理這些交易記錄作業的反向工程。

一個平衡的方法是混合交易式資料庫資料表和簡化的 ES 模式。 您可以使用「準備發行事件」之類的狀態，這是您在將其認可至整合事件資料表時，在原始事件中設定的狀態。 然後，您可以嘗試將事件發行至事件匯流排。 如果發行事件動作成功，您會在源服務中啟動另一項交易，並將狀態從「準備發行事件」移至「已發行的事件」。

如果事件匯流排中的「發行事件」動作失敗，則資料在原始微服務中仍不會不一致—它仍標示為「準備發行事件」，而且對於其餘的服務而言，它最終會是一致的。 您一律可以讓背景工作檢查整合事件的交易狀態。 如果作業在「準備發行事件」狀態中找到事件，它可以嘗試將該事件重新發佈至事件匯流排。

請注意，使用此方法，您只會保存每個來源微服務的整合事件，以及您要傳達給其他微服務或外部系統的事件。 相較之下，在完整的 ES 系統中，您也會儲存所有領域事件。

因此，此平衡的方法是簡化的 ES 系統。 您需要一份整合事件清單及其目前狀態 ( 「準備發行」和「已發佈」 ) 。 但是，您只需要實作整合事件的這些狀態。 此外，在此方法中，您不需要如同在完整的 ES 系統中，將所有領域資料儲存為交易式資料庫中的事件。

如果您已使用關聯式資料庫，您可以使用交易式資料表來儲存整合事件。 若要達到應用程式中的不可部分完成性，您可以使用以本機交易為基礎的雙步驟程序。 基本上，您在具有領域實體的相同資料庫中會有 IntegrationEvent 資料表。 該資料表可確保達到不可部分完成性，讓您在認可領域資料的相同交易中包含持續性整合事件。

逐步程序如下：

1. 應用程式開始本機資料庫交易。

2. 它接著會更新您的領域實體狀態，並將事件插入整合事件資料表。

3. 最後，其會認可交易，您即可如預期得到不可部份完成的作業，然後

4. 您會以某種方式發佈事件 (下一步)。

實作發行事件的步驟時，您有下列選擇：

- 在認可交易之後直接發行整合事件，並使用另一個本機交易將資料表中的事件標示為已發行。 然後，使用資料表作為成品，以在遠端微服務發生問題時追蹤整合事件，並根據儲存的整合事件來執行補償動作。

- 使用資料表作為一種佇列。 另一個應用程式執行緒或處理序會查詢整合事件資料表、將事件發行至事件匯流排，然後使用本機交易將事件標示為已發行。

圖 6-22 顯示這些方法中第一個方法的架構。

![不使用背景工作微服務發行時的不可部分完成性圖表。](./media/subscribe-events/atomicity-publish-event-bus.png)

**圖 6-22**。 將事件發行至事件匯流排時的不可部分完成性

圖 6-22 中所述的方法缺少負責檢查並確認已發佈整合事件是否成功的額外背景工作微服務。 若失敗，該額外檢查程式背景工作微服務會從資料表讀取事件並重新發佈，亦即重複步驟 2。

關於第二個方法：您會使用 EventLog 資料表作為佇列，且一律會使用背景工作微服務來發行訊息。 在此情況下，其流程會如圖 6-23 所示。 圖中顯示額外的微服務，而且資料表是發行事件時的單一來源。

![使用背景工作微服務發行時的不可部分完成性圖表。](./media/subscribe-events/atomicity-publish-worker-microservice.png)

**圖 6-23**。 使用背景工作微服務將事件發行至事件匯流排時的不可部分完成性

為了簡化起見，eShopOnContainers 範例使用第一個方法 (沒有額外的處理序或檢查微服務) 再加上事件匯流排。 不過，eShopOnContainers 範例不會處理所有可能的失敗案例。 在部署至雲端的實際應用程式中，您必須體認到該問題終究會發生，而且您必須實作該檢查並重新傳送邏輯。 如果當您透過事件匯流排發佈事件 (使用背景工作) 時，有該資料表作為單一事件來源，使用資料表作為佇列可能會比第一個方法更有效。

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>透過事件匯流排發行整合事件時實作不可部分完成性

下列程式碼示範如何建立涉及多個 DbContext 物件的單一交易：一個內容與要更新的原始資料相關，第二個內容與 IntegrationEventLog 資料表相關。

如果與資料庫的連接在程式碼執行時有任何問題，則下列範例程式碼中的交易將無法復原。 在 Azure SQL DB 等雲端式系統中，由於可能會在伺服器之間移動資料庫，因此可能會發生此情況。 若要在多個內容之間實作復原交易，請參閱本指南稍後的[實作具有恢復功能的 Entity Framework Core SQL 連接](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md)一節。

為了清楚起見，下列範例會在單一程式碼片段中顯示整個程序。 不過，eShopOnContainers 的執行是重構的，並將此邏輯分割成多個類別，以便更容易維護。

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
  if (!raiseProductPriceChangedEvent)
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

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      _integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

建立 ProductPriceChangedIntegrationEvent 整合事件之後，儲存原始領域作業 (更新目錄項目) 的交易也會在 EventLog 資料表中包含事件的持續性。 這會使它成為單一交易，而且您一律可以檢查是否已傳送事件訊息。

事件記錄檔資料表已透過原始資料庫作業以不可分割方式更新，並對相同的資料庫使用本機交易。 如果有任何作業失敗，則會擲回例外狀況，且交易會復原所有已完成的作業，讓網域作業與儲存到資料表的事件訊息之間保有一致性。

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

事件處理常式需要確認產品是否存在於任何購物籃執行個體中。 它也會更新每個相關購物籃明細項目的項目價格。 最後，其會建立一個警示，向使用者顯示價格變更，如圖 6-24 所示。

![顯示使用者購物車之價格變更通知的瀏覽器螢幕擷取畫面。](./media/subscribe-events/display-item-price-change.png)

**圖 6-24**。 顯示購物籃中的項目價格變更，如整合事件所傳達

## <a name="idempotency-in-update-message-events"></a>更新訊息事件中的等冪性

更新訊息事件的一個重點是，通訊期間任何時間失敗都應該導致重試訊息。 否則，背景工作可能會嘗試發行已發行的事件，並建立競爭條件。 請確定更新為等冪或提供足夠的資訊，以確保您可以偵測到重複的、捨棄它，然後只傳回一個回應。

如稍早所述，等冪性表示作業可執行多次而不會變更結果。 在傳訊環境中，當傳達事件時，如果可傳遞事件多次而不會變更接收者微服務的結果，事件會是等冪。 由於事件本身的本質，或由於系統處理事件的方式，這可能會是必要條件。 訊息等冪性在使用傳訊的任何應用程式中都很重要，不是只有在實作事件匯流排模式的應用程式中才重要。

等冪作業的一個範例是 SQL 陳述式，該陳述式只有在資料表中還沒有資料時，才會將該資料插入資料表。 該 INSERT SQL 陳述式的執行次數並不重要；結果會相同，資料表將會包含該資料。 如果可能不只一次傳送並處理訊息，當處理訊息時，也可能需要類似的等冪性。 例如，如果重試邏輯導致傳送者多次傳送完全相同的訊息，您需要確定它是等冪的。

您可以設計等冪訊息。 舉例來說，您可以建立事件，指出「將產品價格設定為美金 $25 元」，而非「將產品價格增加美金 $5 元。」 您可以安全地處理第一則訊息不限次數，結果會相同。 第二則訊息則不然。 但即使是在第一個案例中，您可能不想要處理第一個事件，因為系統也可能已傳送較新的價格變更事件，而且您將覆寫新價格。

另一個範例可能是傳播至多個訂閱者的已完成訂單事件。 應用程式必須確保在其他系統中的訂單資訊只會在其他系統中更新一次，即使是相同的訂單完成事件也有重複的訊息事件也一樣。

讓每個事件有某種識別會方便您建立邏輯，以強制每個接收者只處理每個事件一次。

某些訊息處理本來就具等冪性。 例如，如果系統會產生影像縮圖，處理所產生縮圖的相關訊息多少次可能不重要，結果會產生縮圖，而且每次都一樣。 相反地，呼叫付款閘道來支付信用卡之類的作業可能不完全具等冪性。 在這些情況下，您需要確保多次處理訊息的效果符合您的預期。

### <a name="additional-resources"></a>其他資源

- **接受訊息等冪性** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>刪除重複的整合事件訊息

您可以確定每個訂閱者在不同層級上傳送和處理訊息事件一次。 一個方法是使用您正在使用之傳訊基礎結構所提供的重複資料刪除功能。 另一個方法是在您的目的地微服務中實作自訂邏輯。 最好是在傳輸層和應用程式層都有驗證。

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>在 EventHandler 層級刪除重複的訊息事件

有一種方式可以確保每個接收者只處理一個事件一次，就是在處理事件處理常式中的訊息事件時執行特定邏輯。 例如，這是 eShopOnContainers 應用程式中使用的方法，您可以在收到整合事件時，在 [UserCheckoutAcceptedIntegrationEventHandler 類別的原始程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) 中看到 `UserCheckoutAcceptedIntegrationEvent` 。  (在這種情況下， `CreateOrderCommand` 會 `IdentifiedCommand` 使用 `eventMsg.RequestId` 做為識別碼的包裝，然後再將它傳送至命令處理常式) 。

### <a name="deduplicating-messages-when-using-rabbitmq"></a>使用 RabbitMQ 時刪除重複的訊息

發生間歇性網路失敗時，訊息可能會重複，因此訊息接收者必須準備處理這些重複的訊息。 可能的話，接收者應該以等冪方式來處理這些訊息，這會比使用重複資料刪除功能來明確處理這些訊息還要理想。

根據 [RabbitMQ 檔](https://www.rabbitmq.com/reliability.html#consumer)，「如果訊息傳遞給取用者，然後再重新排入佇列 (，因為它在取用者連接卸載之前未經過認可，例如) 接著，RabbitMQ 就會在傳遞時，將重新傳遞的旗標設定 (是否為相同的取用者或不同的) 。

如果已設定「重新傳遞」旗標，則接收者必須將該旗標列入考慮，因為訊息可能已經處理過。 但不保證一定如此，訊息在離開訊息代理程式之後可能從未抵達接收者 (或許因為網路問題)。 另一方面，如果未設定「重新傳遞」旗標，則保證訊息未傳送一次以上。 因此，只有在訊息中設定「重新傳遞」旗標時，接收者才需要以等冪方式刪除訊息或處理訊息。

### <a name="additional-resources"></a>其他資源

- **使用 NServiceBus (特定軟體的分叉 eShopOnContainers)** \
    <https://go.particular.net/eShopOnContainers>

- **事件驅動的訊息** \
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- **Jimmy Bogard。重構以提高彈性：評估結合程度** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **發佈-訂閱通道** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **系結內容之間的通訊** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **最終一致性** \
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Philip 棕色。整合限定內容的策略** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson。使用匯總、事件來源和 CQRS 開發交易微服務-第2部分** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson。事件來源模式** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **事件來源簡介** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Event Store 資料庫**. 官方網站。 \
    <https://geteventstore.com/>

- **派翠克 Nommensen。適用于微服務的 Event-Driven 資料管理** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **端點定理** \
    <https://en.wikipedia.org/wiki/CAP_theorem>

- **什麼是 CAP 定理？** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **資料一致性入門** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling。CAP 定理：為什麼雲端和網際網路的「一切都不同」** \
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewer。在十二年後的上限：「規則」的變更** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure 服務匯流排代理訊息：重複偵測**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **可靠性指南** (RabbitMQ 文件) \
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> [上一個](rabbitmq-event-bus-development-test-environment.md) 
> [下一步](test-aspnet-core-services-web-apps.md)
