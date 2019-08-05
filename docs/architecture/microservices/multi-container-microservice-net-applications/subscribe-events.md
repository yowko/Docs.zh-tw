---
title: 訂閱事件
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 了解發佈及訂閱整合事件的詳細資料。
ms.date: 10/02/2018
ms.openlocfilehash: c0eaacce51b186191431bf827bb84d3a2d2b7b1f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675865"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="57a91-103">訂閱事件</span><span class="sxs-lookup"><span data-stu-id="57a91-103">Subscribing to events</span></span>

<span data-ttu-id="57a91-104">使用事件匯流排的第一個步驟是訂閱所要接收之事件的微服務。</span><span class="sxs-lookup"><span data-stu-id="57a91-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="57a91-105">這應該在接收者微服務中完成。</span><span class="sxs-lookup"><span data-stu-id="57a91-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="57a91-106">下列簡單程式碼顯示每個接收者微服務在啟動服務時必須實作的項目 (也就是在 `Startup` 類別中)，以便訂閱所需的事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="57a91-107">在本例中，`basket.api` 微服務需要訂閱 `ProductPriceChangedIntegrationEvent` 和 `OrderStartedIntegrationEvent` 訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="57a91-108">例如，訂閱 `ProductPriceChangedIntegrationEvent` 事件時，可讓購物籃微服務注意到產品價格的任何變更，並在使用者的購物籃中有該項產品時，警告使用者有此變更。</span><span class="sxs-lookup"><span data-stu-id="57a91-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="57a91-109">執行此程式碼之後，訂閱者微服務會透過 RabbitMQ 通道接聽。</span><span class="sxs-lookup"><span data-stu-id="57a91-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="57a91-110">當 ProductPriceChangedIntegrationEvent 類型的任何訊息抵達時，程式碼會叫用傳遞給它的事件處理常式並處理事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="57a91-111">透過事件匯流排發行事件</span><span class="sxs-lookup"><span data-stu-id="57a91-111">Publishing events through the event bus</span></span>

<span data-ttu-id="57a91-112">最後，訊息傳送者 (來源微服務) 會使用類似下列範例的程式碼發行整合事件</span><span class="sxs-lookup"><span data-stu-id="57a91-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="57a91-113">(這是經過簡化的範例，不可部分完成性不在考量範圍內)。只要必須在多個微服務之間傳播事件 (通常是在從來源微服務認可資料或交易之後)，您就會實作類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="57a91-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="57a91-114">首先，事件匯流排實作物件 (採用 RabbitMQ 或採用服務匯流排) 會插入控制器建構函式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="57a91-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="57a91-115">然後，您可以從控制器的方法使用它，就像是在 UpdateProduct 方法中一樣：</span><span class="sxs-lookup"><span data-stu-id="57a91-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="57a91-116">在本例中，由於來源微服務是簡單的 CRUD 微服務，因此該程式碼會直接放在 Web API 控制器中。</span><span class="sxs-lookup"><span data-stu-id="57a91-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="57a91-117">在更進階的微服務中，例如使用 CQRS 方法時，它可以在 `Handle()` 方法的 `CommandHandler` 類別中實作。</span><span class="sxs-lookup"><span data-stu-id="57a91-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="57a91-118">設計發行至事件匯流排時的不可部分完成性和復原</span><span class="sxs-lookup"><span data-stu-id="57a91-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="57a91-119">當您透過分散式傳訊系統 (例如您的事件匯流排) 發佈整合事件時，會發生以不可部分完成方式更新原始資料庫及發佈事件的問題 (也就是兩個作業皆完成或皆未完成)。</span><span class="sxs-lookup"><span data-stu-id="57a91-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="57a91-120">例如，在稍早所示的簡化範例中，程式碼會在產品價格變更時將資料認可至資料庫，然後發行 ProductPriceChangedIntegrationEvent 訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="57a91-121">乍看之下，以不可分割方式執行這兩個作業可能很重要。</span><span class="sxs-lookup"><span data-stu-id="57a91-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="57a91-122">不過，如果您使用涉及資料庫和訊息代理程式的分散式交易，如同您在 [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx) 等較舊系統中的做法，則不建議這樣做，原因如 [CAP 定理](https://www.quora.com/What-Is-CAP-Theorem-1)所述。</span><span class="sxs-lookup"><span data-stu-id="57a91-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="57a91-123">基本上，您可以使用微服務來建置可擴充且高度可用的系統。</span><span class="sxs-lookup"><span data-stu-id="57a91-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="57a91-124">簡單來說，CAP 定理指出您無法建置持續可用、極為一致「且」  容許任何分割的 (分散式) 資料庫 (或擁有自己模型的微服務)。</span><span class="sxs-lookup"><span data-stu-id="57a91-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="57a91-125">您必須從這三個屬性中選擇兩個。</span><span class="sxs-lookup"><span data-stu-id="57a91-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="57a91-126">在微服務架構中，您應該選擇可用性和容錯，而且您應該不要強調強式一致性。</span><span class="sxs-lookup"><span data-stu-id="57a91-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="57a91-127">因此，在大多數現代化微服務架構應用程式中，您通常不想要在傳訊中使用分散式交易 (就像是使用 [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx) 實作以 Windows Distributed Transaction Coordinator (DTC) 為基礎的[分散式交易](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85))時一樣)。</span><span class="sxs-lookup"><span data-stu-id="57a91-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="57a91-128">讓我們回到一開始的問題及其範例。</span><span class="sxs-lookup"><span data-stu-id="57a91-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="57a91-129">如果服務損毀發生在更新資料庫之後 (在本例中會是具有 \_context.SaveChangesAsync() 的程式碼行之後)，但在發行整合事件之前，整體系統可能會變成不一致。</span><span class="sxs-lookup"><span data-stu-id="57a91-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="57a91-130">視您正在處理的特定商務作業而定，這可能具商務關鍵性。</span><span class="sxs-lookup"><span data-stu-id="57a91-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="57a91-131">如稍早的＜架構＞一節中所述，您有數個方法可解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="57a91-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="57a91-132">使用完整的[事件溯源模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)。</span><span class="sxs-lookup"><span data-stu-id="57a91-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="57a91-133">使用[交易記錄採礦](https://www.scoop.it/t/sql-server-transaction-log-mining)。</span><span class="sxs-lookup"><span data-stu-id="57a91-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="57a91-134">使用[寄件匣模式](http://gistlabs.com/2014/05/the-outbox/)。</span><span class="sxs-lookup"><span data-stu-id="57a91-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="57a91-135">這是交易式資料表，可儲存整合事件 (以延伸本機交易)。</span><span class="sxs-lookup"><span data-stu-id="57a91-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="57a91-136">在此案例中，使用完整的事件溯源 (ES) 模式即使不是「最佳」  方法，也是最佳方法之一。</span><span class="sxs-lookup"><span data-stu-id="57a91-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="57a91-137">不過，在許多應用程式案例中，您可能無法實作完整的 ES 系統。</span><span class="sxs-lookup"><span data-stu-id="57a91-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="57a91-138">ES 表示只會將領域事件儲存在您的交易式資料庫中，而不會儲存目前的狀態資料。</span><span class="sxs-lookup"><span data-stu-id="57a91-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="57a91-139">只儲存領域事件可能有許多好處，例如提供系統歷程記錄，以及能夠判斷過去任何時間的系統狀態。</span><span class="sxs-lookup"><span data-stu-id="57a91-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="57a91-140">不過，實作完整的 ES 系統需要您重新架構大部分的系統，因而引進許多其他的複雜度和需求。</span><span class="sxs-lookup"><span data-stu-id="57a91-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="57a91-141">例如，您會想要使用專為事件溯源所建立的資料庫 (例如[事件存放區](https://eventstore.org/))，或文件導向資料庫 (例如 Azure Cosmos DB、MongoDB、Cassandra、CouchDB 或 RavenDB)。</span><span class="sxs-lookup"><span data-stu-id="57a91-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="57a91-142">ES 是解決這個問題的最好方法，但除非您已熟悉事件溯源，否則並不是最簡單的解決方法。</span><span class="sxs-lookup"><span data-stu-id="57a91-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="57a91-143">使用交易記錄採礦的選項一開始看起來很簡單。</span><span class="sxs-lookup"><span data-stu-id="57a91-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="57a91-144">不過，若要使用此方法，微服務必須與 RDBMS 交易記錄結合，例如 SQL Server 交易記錄。</span><span class="sxs-lookup"><span data-stu-id="57a91-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="57a91-145">這可能不適當。</span><span class="sxs-lookup"><span data-stu-id="57a91-145">This is probably not desirable.</span></span> <span data-ttu-id="57a91-146">另一個缺點是，交易記錄中記錄的低層級更新可能不會與高層級整合事件位於相同層級。</span><span class="sxs-lookup"><span data-stu-id="57a91-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="57a91-147">如果是這樣，可能會很難處理這些交易記錄作業的反向工程。</span><span class="sxs-lookup"><span data-stu-id="57a91-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="57a91-148">一個平衡的方法是混合交易式資料庫資料表和簡化的 ES 模式。</span><span class="sxs-lookup"><span data-stu-id="57a91-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="57a91-149">您可以使用「準備發行事件」等狀態，當您將它認可至整合事件資料表時，會在原始事件中設定此狀態。</span><span class="sxs-lookup"><span data-stu-id="57a91-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="57a91-150">然後，您可以嘗試將事件發行至事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="57a91-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="57a91-151">如果發行事件動作成功，您可以啟動來源服務中的另一個交易，並將狀態從「準備發行事件」移至「事件已發行」。</span><span class="sxs-lookup"><span data-stu-id="57a91-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="57a91-152">如果事件匯流排中的發行事件動作失敗，來源微服務中的資料不會一直處於不一致的狀態 (它仍標示為「準備發行事件」，但對於其餘服務而言，它最終將會一致)。</span><span class="sxs-lookup"><span data-stu-id="57a91-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="57a91-153">您一律可以讓背景工作檢查整合事件的交易狀態。</span><span class="sxs-lookup"><span data-stu-id="57a91-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="57a91-154">如果工作發現事件處於「準備發行事件」狀態，它可以嘗試將該事件重新發行至事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="57a91-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="57a91-155">請注意，使用此方法，您只會保存每個來源微服務的整合事件，以及您要傳達給其他微服務或外部系統的事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="57a91-156">相較之下，在完整的 ES 系統中，您也會儲存所有領域事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="57a91-157">因此，此平衡的方法是簡化的 ES 系統。</span><span class="sxs-lookup"><span data-stu-id="57a91-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="57a91-158">您需要一份整合事件及其目前狀態 (「準備發行」與「已發行」) 的清單。</span><span class="sxs-lookup"><span data-stu-id="57a91-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="57a91-159">但是，您只需要實作整合事件的這些狀態。</span><span class="sxs-lookup"><span data-stu-id="57a91-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="57a91-160">此外，在此方法中，您不需要如同在完整的 ES 系統中，將所有領域資料儲存為交易式資料庫中的事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="57a91-161">如果您已使用關聯式資料庫，您可以使用交易式資料表來儲存整合事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="57a91-162">若要達到應用程式中的不可部分完成性，您可以使用以本機交易為基礎的雙步驟程序。</span><span class="sxs-lookup"><span data-stu-id="57a91-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="57a91-163">基本上，您在具有領域實體的相同資料庫中會有 IntegrationEvent 資料表。</span><span class="sxs-lookup"><span data-stu-id="57a91-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="57a91-164">該資料表可確保達到不可部分完成性，讓您在認可領域資料的相同交易中包含持續性整合事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="57a91-165">逐步程序如下：</span><span class="sxs-lookup"><span data-stu-id="57a91-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="57a91-166">應用程式開始本機資料庫交易。</span><span class="sxs-lookup"><span data-stu-id="57a91-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="57a91-167">它接著會更新您的領域實體狀態，並將事件插入整合事件資料表。</span><span class="sxs-lookup"><span data-stu-id="57a91-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="57a91-168">最後，其會認可交易，您即可如預期得到不可部份完成的作業，然後</span><span class="sxs-lookup"><span data-stu-id="57a91-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="57a91-169">您會以某種方式發佈事件 (下一步)。</span><span class="sxs-lookup"><span data-stu-id="57a91-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="57a91-170">實作發行事件的步驟時，您有下列選擇：</span><span class="sxs-lookup"><span data-stu-id="57a91-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="57a91-171">在認可交易之後直接發行整合事件，並使用另一個本機交易將資料表中的事件標示為已發行。</span><span class="sxs-lookup"><span data-stu-id="57a91-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="57a91-172">然後，使用資料表作為成品，以在遠端微服務發生問題時追蹤整合事件，並根據儲存的整合事件來執行補償動作。</span><span class="sxs-lookup"><span data-stu-id="57a91-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="57a91-173">使用資料表作為一種佇列。</span><span class="sxs-lookup"><span data-stu-id="57a91-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="57a91-174">另一個應用程式執行緒或處理序會查詢整合事件資料表、將事件發行至事件匯流排，然後使用本機交易將事件標示為已發行。</span><span class="sxs-lookup"><span data-stu-id="57a91-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="57a91-175">圖 6-22 顯示這些方法中第一個方法的架構。</span><span class="sxs-lookup"><span data-stu-id="57a91-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![在發佈事件時，處理不可部分完成之作業的方法之一：使用一個交易將事件認可至事件記錄表，然後使用其他交易來發佈 (在 eShopOnContainers 中使用)](./media/image23.png)

<span data-ttu-id="57a91-177">**圖 6-22**。</span><span class="sxs-lookup"><span data-stu-id="57a91-177">**Figure 6-22**.</span></span> <span data-ttu-id="57a91-178">將事件發行至事件匯流排時的不可部分完成性</span><span class="sxs-lookup"><span data-stu-id="57a91-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="57a91-179">圖 6-22 中所述的方法缺少負責檢查並確認已發佈整合事件是否成功的額外背景工作微服務。</span><span class="sxs-lookup"><span data-stu-id="57a91-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="57a91-180">若失敗，該額外檢查程式背景工作微服務會從資料表讀取事件並重新發佈，亦即重複步驟 2。</span><span class="sxs-lookup"><span data-stu-id="57a91-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="57a91-181">關於第二個方法：您會使用 EventLog 資料表作為佇列，且一律會使用背景工作微服務來發行訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="57a91-182">在此情況下，其流程會如圖 6-23 所示。</span><span class="sxs-lookup"><span data-stu-id="57a91-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="57a91-183">圖中顯示額外的微服務，而且資料表是發行事件時的單一來源。</span><span class="sxs-lookup"><span data-stu-id="57a91-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![處理不可部分完成之作業的另一方法：發佈至事件記錄表，然後以其他微服務 (在幕後執行) 發佈事件。](./media/image24.png)

<span data-ttu-id="57a91-185">**圖 6-23**。</span><span class="sxs-lookup"><span data-stu-id="57a91-185">**Figure 6-23**.</span></span> <span data-ttu-id="57a91-186">使用背景工作微服務將事件發行至事件匯流排時的不可部分完成性</span><span class="sxs-lookup"><span data-stu-id="57a91-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="57a91-187">為了簡化起見，eShopOnContainers 範例使用第一個方法 (沒有額外的處理序或檢查微服務) 再加上事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="57a91-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="57a91-188">不過，eShopOnContainers 並不會處理所有可能的失敗案例。</span><span class="sxs-lookup"><span data-stu-id="57a91-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="57a91-189">在部署至雲端的實際應用程式中，您必須體認到該問題終究會發生，而且您必須實作該檢查並重新傳送邏輯。</span><span class="sxs-lookup"><span data-stu-id="57a91-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="57a91-190">如果當您透過事件匯流排發佈事件 (使用背景工作) 時，有該資料表作為單一事件來源，使用資料表作為佇列可能會比第一個方法更有效。</span><span class="sxs-lookup"><span data-stu-id="57a91-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="57a91-191">透過事件匯流排發行整合事件時實作不可部分完成性</span><span class="sxs-lookup"><span data-stu-id="57a91-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="57a91-192">下列程式碼示範如何建立涉及多個 DbContext 物件的單一交易：一個內容與要更新的原始資料相關，第二個內容與 IntegrationEventLog 資料表相關。</span><span class="sxs-lookup"><span data-stu-id="57a91-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="57a91-193">請注意，如果資料庫連接在執行程式碼時發生任何問題，下列範例程式碼中的交易將不會復原。</span><span class="sxs-lookup"><span data-stu-id="57a91-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="57a91-194">在 Azure SQL DB 等雲端式系統中，由於可能會在伺服器之間移動資料庫，因此可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="57a91-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="57a91-195">若要在多個內容之間實作復原交易，請參閱本指南稍後的[實作具有恢復功能的 Entity Framework Core SQL 連接](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md)一節。</span><span class="sxs-lookup"><span data-stu-id="57a91-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="57a91-196">為了清楚起見，下列範例會在單一程式碼片段中顯示整個程序。</span><span class="sxs-lookup"><span data-stu-id="57a91-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="57a91-197">不過，eShopOnContainers 實作實際上已重構，並將此邏輯分割成多個類別，因此很容易維護。</span><span class="sxs-lookup"><span data-stu-id="57a91-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="57a91-198">建立 ProductPriceChangedIntegrationEvent 整合事件之後，儲存原始領域作業 (更新目錄項目) 的交易也會在 EventLog 資料表中包含事件的持續性。</span><span class="sxs-lookup"><span data-stu-id="57a91-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="57a91-199">這會使它成為單一交易，而且您一律可以檢查是否已傳送事件訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="57a91-200">事件記錄檔資料表已透過原始資料庫作業以不可分割方式更新，並對相同的資料庫使用本機交易。</span><span class="sxs-lookup"><span data-stu-id="57a91-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="57a91-201">如果有任何作業失敗，則會擲回例外狀況，且交易會復原所有已完成的作業，讓網域作業與儲存到資料表的事件訊息之間保有一致性。</span><span class="sxs-lookup"><span data-stu-id="57a91-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="57a91-202">從訂閱接收訊息：接收者微服務中的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="57a91-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="57a91-203">除了事件訂閱邏輯之外，您還需要實作整合事件處理常式的內部程式碼 (例如回呼方法)。</span><span class="sxs-lookup"><span data-stu-id="57a91-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="57a91-204">此事件處理常式是您指定特定類型之事件訊息接收和處理的位置。</span><span class="sxs-lookup"><span data-stu-id="57a91-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="57a91-205">事件處理常式會先從事件匯流排接收事件執行個體。</span><span class="sxs-lookup"><span data-stu-id="57a91-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="57a91-206">然後，它會找出要處理且與該整合事件相關的元件，並在接收者微服務中的狀態變更時傳播及保存事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="57a91-207">例如，如果 ProductPriceChanged 事件源自目錄微服務，則會在購物籃微服務中處理，也會變更此接收者購物籃微服務中的狀態，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="57a91-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="57a91-208">事件處理常式需要確認產品是否存在於任何購物籃執行個體中。</span><span class="sxs-lookup"><span data-stu-id="57a91-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="57a91-209">它也會更新每個相關購物籃明細項目的項目價格。</span><span class="sxs-lookup"><span data-stu-id="57a91-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="57a91-210">最後，其會建立一個警示，向使用者顯示價格變更，如圖 6-24 所示。</span><span class="sxs-lookup"><span data-stu-id="57a91-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![使用者購物車上價格變更通知的瀏覽器檢視。](./media/image25.png)

<span data-ttu-id="57a91-212">**圖 6-24**。</span><span class="sxs-lookup"><span data-stu-id="57a91-212">**Figure 6-24**.</span></span> <span data-ttu-id="57a91-213">顯示購物籃中的項目價格變更，如整合事件所傳達</span><span class="sxs-lookup"><span data-stu-id="57a91-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="57a91-214">更新訊息事件中的等冪性</span><span class="sxs-lookup"><span data-stu-id="57a91-214">Idempotency in update message events</span></span>

<span data-ttu-id="57a91-215">更新訊息事件的一個重點是，通訊期間任何時間失敗都應該導致重試訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="57a91-216">否則，背景工作可能會嘗試發行已發行的事件，並建立競爭條件。</span><span class="sxs-lookup"><span data-stu-id="57a91-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="57a91-217">您需要確定更新為等冪或提供足夠的資訊，以確保您可以偵測重複項、將它捨棄，並只傳回一個回應。</span><span class="sxs-lookup"><span data-stu-id="57a91-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="57a91-218">如稍早所述，等冪性表示作業可執行多次而不會變更結果。</span><span class="sxs-lookup"><span data-stu-id="57a91-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="57a91-219">在傳訊環境中，當傳達事件時，如果可傳遞事件多次而不會變更接收者微服務的結果，事件會是等冪。</span><span class="sxs-lookup"><span data-stu-id="57a91-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="57a91-220">由於事件本身的本質，或由於系統處理事件的方式，這可能會是必要條件。</span><span class="sxs-lookup"><span data-stu-id="57a91-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="57a91-221">訊息等冪性在使用傳訊的任何應用程式中都很重要，不是只有在實作事件匯流排模式的應用程式中才重要。</span><span class="sxs-lookup"><span data-stu-id="57a91-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="57a91-222">等冪作業的一個範例是 SQL 陳述式，該陳述式只有在資料表中還沒有資料時，才會將該資料插入資料表。</span><span class="sxs-lookup"><span data-stu-id="57a91-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="57a91-223">該 INSERT SQL 陳述式的執行次數並不重要；結果會相同，資料表將會包含該資料。</span><span class="sxs-lookup"><span data-stu-id="57a91-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="57a91-224">如果可能不只一次傳送並處理訊息，當處理訊息時，也可能需要類似的等冪性。</span><span class="sxs-lookup"><span data-stu-id="57a91-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="57a91-225">例如，如果重試邏輯導致傳送者多次傳送完全相同的訊息，您需要確定它是等冪的。</span><span class="sxs-lookup"><span data-stu-id="57a91-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="57a91-226">您可以設計等冪訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="57a91-227">舉例來說，您可以建立事件，指出「將產品價格設定為美金 $25 元」，而非「將產品價格增加美金 $5 元。」</span><span class="sxs-lookup"><span data-stu-id="57a91-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="57a91-228">您可以安全地處理第一則訊息不限次數，結果會相同。</span><span class="sxs-lookup"><span data-stu-id="57a91-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="57a91-229">第二則訊息則不然。</span><span class="sxs-lookup"><span data-stu-id="57a91-229">That is not true for the second message.</span></span> <span data-ttu-id="57a91-230">但即使是在第一個案例中，您可能不想要處理第一個事件，因為系統也可能已傳送較新的價格變更事件，而且您將覆寫新價格。</span><span class="sxs-lookup"><span data-stu-id="57a91-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="57a91-231">另一個範例可能是將訂單已完成事件傳播至多個訂閱者。</span><span class="sxs-lookup"><span data-stu-id="57a91-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="57a91-232">請確保只在其他系統中更新訂單資訊一次，即使同一個訂單已完成事件有重複的訊息事件亦然。</span><span class="sxs-lookup"><span data-stu-id="57a91-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="57a91-233">讓每個事件有某種識別會方便您建立邏輯，以強制每個接收者只處理每個事件一次。</span><span class="sxs-lookup"><span data-stu-id="57a91-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="57a91-234">某些訊息處理本來就具等冪性。</span><span class="sxs-lookup"><span data-stu-id="57a91-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="57a91-235">例如，如果系統會產生影像縮圖，處理所產生縮圖的相關訊息多少次可能不重要，結果會產生縮圖，而且每次都一樣。</span><span class="sxs-lookup"><span data-stu-id="57a91-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="57a91-236">相反地，呼叫付款閘道來支付信用卡之類的作業可能不完全具等冪性。</span><span class="sxs-lookup"><span data-stu-id="57a91-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="57a91-237">在這些情況下，您需要確保多次處理訊息的效果符合您的預期。</span><span class="sxs-lookup"><span data-stu-id="57a91-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="57a91-238">其他資源</span><span class="sxs-lookup"><span data-stu-id="57a91-238">Additional resources</span></span>

- <span data-ttu-id="57a91-239">**遵循訊息冪等**</span><span class="sxs-lookup"><span data-stu-id="57a91-239">**Honoring message idempotency**</span></span> <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="57a91-240">刪除重複的整合事件訊息</span><span class="sxs-lookup"><span data-stu-id="57a91-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="57a91-241">您可以確保不同層級的每個訂閱者只傳送及處理一次訊息事件。</span><span class="sxs-lookup"><span data-stu-id="57a91-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="57a91-242">一個方法是使用您正在使用之傳訊基礎結構所提供的重複資料刪除功能。</span><span class="sxs-lookup"><span data-stu-id="57a91-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="57a91-243">另一個方法是在您的目的地微服務中實作自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="57a91-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="57a91-244">最好是在傳輸層和應用程式層都有驗證。</span><span class="sxs-lookup"><span data-stu-id="57a91-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="57a91-245">在 EventHandler 層級刪除重複的訊息事件</span><span class="sxs-lookup"><span data-stu-id="57a91-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="57a91-246">若要確定任何接收者只處理一次事件，一個方式是在處理事件處理常式中的訊息事件時實作特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="57a91-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="57a91-247">舉例來說，eShopOnContainers 應用程式就使用了這個方法，就如其在接收到 UserCheckoutAcceptedIntegrationEvent 整合事件時，在 [UserCheckoutAcceptedIntegrationEventHandler 類別的原始程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs)中所示。</span><span class="sxs-lookup"><span data-stu-id="57a91-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="57a91-248">(在此案例中，在把 CreateOrderCommand 傳送至命令處理常式前，我們使用 eventMsg.RequestId 作為識別碼，用 IdentifiedCommand 加以包裝)。</span><span class="sxs-lookup"><span data-stu-id="57a91-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="57a91-249">使用 RabbitMQ 時刪除重複的訊息</span><span class="sxs-lookup"><span data-stu-id="57a91-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="57a91-250">發生間歇性網路失敗時，訊息可能會重複，因此訊息接收者必須準備處理這些重複的訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="57a91-251">可能的話，接收者應該以等冪方式來處理這些訊息，這會比使用重複資料刪除功能來明確處理這些訊息還要理想。</span><span class="sxs-lookup"><span data-stu-id="57a91-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="57a91-252">根據 [RabbitMQ 文件](https://www.rabbitmq.com/reliability.html#consumer)，「如果將訊息傳遞給取用者，然後要求訊息 (例如因為取用者在中斷連線之前未認可訊息)，則 RabbitMQ 會在再次傳遞訊息時 (不論是對相同的取用者或不同的取用者)，設定訊息的 redelivered 旗標。</span><span class="sxs-lookup"><span data-stu-id="57a91-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="57a91-253">如果設定了 “redelivered” 旗標，接收者必須將此列入考量，因為可能已處理訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="57a91-254">但不保證一定如此，訊息在離開訊息代理程式之後可能從未抵達接收者 (或許因為網路問題)。</span><span class="sxs-lookup"><span data-stu-id="57a91-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="57a91-255">相反地，如果未設定 “redelivered” 旗標，就會保證訊息不會多次傳送。</span><span class="sxs-lookup"><span data-stu-id="57a91-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="57a91-256">因此，只有訊息中已設定 “redelivered” 旗標時，接收者才必須刪除重複的訊息或以等冪方式處理訊息。</span><span class="sxs-lookup"><span data-stu-id="57a91-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="57a91-257">其他資源</span><span class="sxs-lookup"><span data-stu-id="57a91-257">Additional resources</span></span>

- <span data-ttu-id="57a91-258">**使用 NServiceBus 派生的 eShopOnContainers (Particular Software)**  </span><span class="sxs-lookup"><span data-stu-id="57a91-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="57a91-259">**事件驅動傳訊** </span><span class="sxs-lookup"><span data-stu-id="57a91-259">**Event Driven Messaging** </span></span>\
    [http://soapatterns.org/design\_patterns/event\_driven\_messaging](http://soapatterns.org/design_patterns/event_driven_messaging)

- <span data-ttu-id="57a91-260">**Jimmy Bogard：重構以提高彈性：評估結合程度** </span><span class="sxs-lookup"><span data-stu-id="57a91-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="57a91-261">**發佈訂閱通道** </span><span class="sxs-lookup"><span data-stu-id="57a91-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="57a91-262">**在繫結的內容之間通訊** </span><span class="sxs-lookup"><span data-stu-id="57a91-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="57a91-263">**最終一致性** </span><span class="sxs-lookup"><span data-stu-id="57a91-263">**Eventual Consistency** </span></span>\
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- <span data-ttu-id="57a91-264">**Philip Brown：整合已繫結內容的策略** </span><span class="sxs-lookup"><span data-stu-id="57a91-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="57a91-265">**Chris Richardson：使用彙總、事件溯源及 CQRS 開發交易微服務 - 第 2 部分** </span><span class="sxs-lookup"><span data-stu-id="57a91-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="57a91-266">**Chris Richardson：事件溯源模式** </span><span class="sxs-lookup"><span data-stu-id="57a91-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="57a91-267">**事件溯源簡介** </span><span class="sxs-lookup"><span data-stu-id="57a91-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="57a91-268">**Event Store 資料庫**.</span><span class="sxs-lookup"><span data-stu-id="57a91-268">**Event Store database**.</span></span> <span data-ttu-id="57a91-269">官方網站。</span><span class="sxs-lookup"><span data-stu-id="57a91-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="57a91-270">**Patrick Nommensen：微服務的事件驅動資料管理** </span><span class="sxs-lookup"><span data-stu-id="57a91-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="57a91-271">**CAP 定理** </span><span class="sxs-lookup"><span data-stu-id="57a91-271">**The CAP Theorem** </span></span>\
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- <span data-ttu-id="57a91-272">**什麼是 CAP 定理？**</span><span class="sxs-lookup"><span data-stu-id="57a91-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="57a91-273">**資料一致性入門** </span><span class="sxs-lookup"><span data-stu-id="57a91-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="57a91-274">**Rick Saling：CAP 定理：為何雲端及網際網路的「一切都不同」**  </span><span class="sxs-lookup"><span data-stu-id="57a91-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span></span>\
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="57a91-275">**Eric Brewer：十二年後的 CAP：「規則」變更的方式** </span><span class="sxs-lookup"><span data-stu-id="57a91-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="57a91-276">**Azure 服務匯流排：代理傳訊：重複項目偵測**  </span><span class="sxs-lookup"><span data-stu-id="57a91-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="57a91-277">**可靠性指南** (RabbitMQ 文件) </span><span class="sxs-lookup"><span data-stu-id="57a91-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

> [!div class="step-by-step"]
> <span data-ttu-id="57a91-278">[上一頁](rabbitmq-event-bus-development-test-environment.md)
> [下一頁](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="57a91-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
