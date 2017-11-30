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
# <a name="subscribing-to-events"></a><span data-ttu-id="b4835-104">訂閱事件</span><span class="sxs-lookup"><span data-stu-id="b4835-104">Subscribing to events</span></span>

<span data-ttu-id="b4835-105">使用事件匯流排的第一個步驟是訂閱 microservices 他們想要接收的事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-105">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="b4835-106">應在接收者 microservices 中完成。</span><span class="sxs-lookup"><span data-stu-id="b4835-106">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="b4835-107">下列簡單程式碼會顯示每個接收者微服務必須實作啟動服務時 （也就是在啟動類別中） 讓它訂閱事件它需要。</span><span class="sxs-lookup"><span data-stu-id="b4835-107">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the Startup class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="b4835-108">比方說，basket.api 微服務需要訂閱 ProductPriceChangedIntegrationEvent 訊息。</span><span class="sxs-lookup"><span data-stu-id="b4835-108">For instance, the basket.api microservice needs to subscribe to ProductPriceChangedIntegrationEvent messages.</span></span> <span data-ttu-id="b4835-109">這對產品價格注意之任何變更的微服務，並讓它發出警告與變更相關的使用者，該產品是否在使用者的購物籃中。</span><span class="sxs-lookup"><span data-stu-id="b4835-109">This makes the microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

<span data-ttu-id="b4835-110">執行此程式碼之後，「 訂閱者 」 的微服務會接聽透過 RabbitMQ 通道。</span><span class="sxs-lookup"><span data-stu-id="b4835-110">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="b4835-111">當類型 ProductPriceChangedIntegrationEvent 的任何訊息抵達時，程式碼會叫用傳遞給它，及處理事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b4835-111">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="b4835-112">事件匯流排透過發行事件</span><span class="sxs-lookup"><span data-stu-id="b4835-112">Publishing events through the event bus</span></span>

<span data-ttu-id="b4835-113">最後，訊息寄件者 （原點微服務） 整合將事件發行與下例類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4835-113">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="b4835-114">（這是簡化的範例不接受不可部份完成性納入考量）。每當事件必須傳播跨多個 microservices，通常是右資料或從原點微服務的交易認可之後，您也會實作類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4835-114">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="b4835-115">首先，事件匯流排實作物件 （根據 RabbitMQ 或服務匯流排上），將會插入在控制器建構函式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="b4835-115">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="b4835-116">然後您使用它從您的控制器方法，就像 UpdateProduct 方法中：</span><span class="sxs-lookup"><span data-stu-id="b4835-116">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="b4835-117">在此情況下，由於原點微服務是簡單的 CRUD 微服務，該程式碼置於權限的 Web API 控制器。</span><span class="sxs-lookup"><span data-stu-id="b4835-117">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> <span data-ttu-id="b4835-118">在更進階的 microservices，它無法認可原始資料之後實作 CommandHandler 類別右中。</span><span class="sxs-lookup"><span data-stu-id="b4835-118">In more advanced microservices, it could be implemented in the CommandHandler class, right after the original data is committed.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="b4835-119">發行到事件匯流排時，設計不可部份完成性和恢復功能</span><span class="sxs-lookup"><span data-stu-id="b4835-119">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="b4835-120">當您發行透過分散式傳訊整合事件系統喜歡事件匯流排時，已自動更新原始資料庫並發行事件的問題。</span><span class="sxs-lookup"><span data-stu-id="b4835-120">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="b4835-121">比方說，在稍早所示簡化範例中，程式碼到資料庫認可資料的產品價格的變更，並接著將發佈 ProductPriceChangedIntegrationEvent 訊息時。</span><span class="sxs-lookup"><span data-stu-id="b4835-121">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="b4835-122">一開始，它看起來可能不可或缺的自動執行這兩項操作。</span><span class="sxs-lookup"><span data-stu-id="b4835-122">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="b4835-123">不過，如果您使用分散式的交易涉及的資料庫和訊息 broker，就像是在較舊的系統，例如[Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)，不建議這樣所描述的原因[CAP 理論](https://www.quora.com/What-Is-CAP-Theorem-1)。</span><span class="sxs-lookup"><span data-stu-id="b4835-123">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="b4835-124">基本上，您可以使用 microservices 建置可擴充、 高可用性的系統。</span><span class="sxs-lookup"><span data-stu-id="b4835-124">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="b4835-125">以稍微簡化，CAP 理論指出資料庫 （或擁有其模型的微服務） 無法建立持續可用、 強式一致性、*和*容許任何磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="b4835-125">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="b4835-126">您必須選擇兩個這三個屬性。</span><span class="sxs-lookup"><span data-stu-id="b4835-126">You must choose two of these three properties.</span></span>

<span data-ttu-id="b4835-127">在 microservices 架構中，您應該選擇可用性和容錯，，您應該強調強式一致性。</span><span class="sxs-lookup"><span data-stu-id="b4835-127">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="b4835-128">因此，在大多數最新型的微服務架構應用程式，通常不想使用分散式的交易，在訊息中，就像您實作[分散式交易](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c)根據 Windows 分散式交易協調器 (DTC) 與[MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="b4835-128">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="b4835-129">讓我們回到初始的問題和其範例。</span><span class="sxs-lookup"><span data-stu-id="b4835-129">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="b4835-130">在服務中止後資料庫的更新 (在此情況下，以滑鼠右鍵一行後面的程式碼與\_內容。SaveChangesAsync())，但發行整合事件之前，整體系統可能會不一致。</span><span class="sxs-lookup"><span data-stu-id="b4835-130">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="b4835-131">這可能是商務關鍵的視您正在處理的特定商務作業而定。</span><span class="sxs-lookup"><span data-stu-id="b4835-131">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="b4835-132">與上述架構 > 一節中，您可以有數個方式來處理這個問題：</span><span class="sxs-lookup"><span data-stu-id="b4835-132">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="b4835-133">使用完整[事件來源模式](https://msdn.microsoft.com/en-us/library/dn589792.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b4835-133">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="b4835-134">使用[交易記錄採礦](http://www.scoop.it/t/sql-server-transaction-log-mining)。</span><span class="sxs-lookup"><span data-stu-id="b4835-134">Using [transaction log mining](http://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="b4835-135">使用[寄件匣模式](http://gistlabs.com/2014/05/the-outbox/)。</span><span class="sxs-lookup"><span data-stu-id="b4835-135">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="b4835-136">這是交易式的資料表，以儲存整合事件 （延伸本機交易）。</span><span class="sxs-lookup"><span data-stu-id="b4835-136">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="b4835-137">此案例中，使用完整的事件來源 (ES) 模式的其中一種最佳的方法，如果不是最佳。</span><span class="sxs-lookup"><span data-stu-id="b4835-137">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="b4835-138">不過，在許多應用程式案例中，您可能無法以實作完整的 ES 系統。</span><span class="sxs-lookup"><span data-stu-id="b4835-138">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="b4835-139">ES 表示只有網域事件儲存在您的交易式資料庫，而不是儲存目前的狀態資料。</span><span class="sxs-lookup"><span data-stu-id="b4835-139">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="b4835-140">儲存只有網域事件可以有極大的好處，例如您的系統提供的歷程記錄以及可以判斷在過去任何時間的系統狀態。</span><span class="sxs-lookup"><span data-stu-id="b4835-140">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="b4835-141">不過，實作完整的 ES 系統會要求您 rearchitect 大部分的系統，並導入了許多其他的複雜性和要求。</span><span class="sxs-lookup"><span data-stu-id="b4835-141">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="b4835-142">例如，您會想要使用資料庫，特別是對事件來源，例如[事件存放區](https://geteventstore.com/)，或文件導向的資料庫，例如 Azure Cosmos DB、 MongoDB、 Cassandra、 CouchDB 或 RavenDB。</span><span class="sxs-lookup"><span data-stu-id="b4835-142">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="b4835-143">ES 是最好的方法，這個問題，但不是最簡單的方法，除非您已熟悉事件來源。</span><span class="sxs-lookup"><span data-stu-id="b4835-143">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="b4835-144">若要使用採礦一開始的交易記錄檔選項看起來非常透明。</span><span class="sxs-lookup"><span data-stu-id="b4835-144">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="b4835-145">不過，若要使用這種方法，微服務有令人敬 RDBMS 交易記錄檔，例如 SQL Server 交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b4835-145">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="b4835-146">這可能就不需要這樣做。</span><span class="sxs-lookup"><span data-stu-id="b4835-146">This is probably not desirable.</span></span> <span data-ttu-id="b4835-147">另一個缺點是，交易記錄檔中記錄的低層級更新可能會在相同層級為概要整合事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-147">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="b4835-148">如果是這樣，反向工程的程序的交易記錄作業很難。</span><span class="sxs-lookup"><span data-stu-id="b4835-148">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="b4835-149">一種是交易式資料庫資料表和簡化的 ES 模式的混合。</span><span class="sxs-lookup"><span data-stu-id="b4835-149">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="b4835-150">您可以使用狀態，例如 「 已備妥可發行事件，「 您在原始的事件時認可整合事件資料表中設定。</span><span class="sxs-lookup"><span data-stu-id="b4835-150">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="b4835-151">您嘗試發行事件至事件匯流排時。</span><span class="sxs-lookup"><span data-stu-id="b4835-151">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="b4835-152">如果發行事件動作成功，您 origin 服務啟動另一個交易，並將狀態從 「 準備發行事件 」 移至 「 事件已發佈 」。</span><span class="sxs-lookup"><span data-stu-id="b4835-152">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="b4835-153">如果發行事件動作會在事件匯流排失敗，資料仍不會不一致的原點微服務內，它仍標示為 「 準備發佈事件 」，相對於其他的服務，它最終將一致。</span><span class="sxs-lookup"><span data-stu-id="b4835-153">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="b4835-154">您一律可以檢查整合事件之交易的狀態的背景工作。</span><span class="sxs-lookup"><span data-stu-id="b4835-154">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="b4835-155">如果工作中的 「 準備發行事件 」 的狀態，找到事件，它可以嘗試重新發行該事件，事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="b4835-155">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="b4835-156">請注意，使用此方法時，您要保存只能每個來源微服務，整合事件與您想要傳達給其他 microservices 或外部系統的事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-156">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="b4835-157">相較之下，在完整 ES 系統中，您會儲存所有網域事件以及。</span><span class="sxs-lookup"><span data-stu-id="b4835-157">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="b4835-158">因此，此平衡的方法是簡化的 ES 系統。</span><span class="sxs-lookup"><span data-stu-id="b4835-158">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="b4835-159">您需要一份整合事件及其目前狀態 （「 已準備好發佈 」 與 「 發行 」）。</span><span class="sxs-lookup"><span data-stu-id="b4835-159">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="b4835-160">但是，您只需要實作這些整合事件的狀態。</span><span class="sxs-lookup"><span data-stu-id="b4835-160">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="b4835-161">這種方法，您不需要將所有網域的資料都儲存為事件在交易式資料庫中，在完整的 ES 系統中一樣。</span><span class="sxs-lookup"><span data-stu-id="b4835-161">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="b4835-162">如果您已經使用關聯式資料庫，您可以使用交易式的資料表來儲存整合事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-162">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="b4835-163">若要達到不可部份完成性應用程式中的，您可以使用本機交易為基礎的兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="b4835-163">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="b4835-164">基本上，您有網域實體相同資料庫中有 IntegrationEvent 資料表。</span><span class="sxs-lookup"><span data-stu-id="b4835-164">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="b4835-165">該資料表會依照針對達到不可部份完成性，讓您包含保險保存整合事件認可網域資料的相同交易運作。</span><span class="sxs-lookup"><span data-stu-id="b4835-165">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="b4835-166">逐步解說，程序如下： 應用程式開始在本機資料庫交易。</span><span class="sxs-lookup"><span data-stu-id="b4835-166">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="b4835-167">然後更新您的網域實體的狀態，並且整合事件資料表中插入事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="b4835-168">最後，它會認可交易。</span><span class="sxs-lookup"><span data-stu-id="b4835-168">Finally, it commits the transaction.</span></span> <span data-ttu-id="b4835-169">您取得所需的不可部份完成性。</span><span class="sxs-lookup"><span data-stu-id="b4835-169">You get the desired atomicity.</span></span>

<span data-ttu-id="b4835-170">如果實作發行事件的步驟，則會有這些選項：</span><span class="sxs-lookup"><span data-stu-id="b4835-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="b4835-171">發行整合事件認可交易之後，權限，並使用另一個本機交易標示為正在發行資料表中的事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="b4835-172">然後，追蹤整合事件發生問題的遠端 microservices，就像成品使用資料表，以及執行預存的整合事件為基礎的補償動作。</span><span class="sxs-lookup"><span data-stu-id="b4835-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="b4835-173">使用資料表做為一種佇列。</span><span class="sxs-lookup"><span data-stu-id="b4835-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="b4835-174">個別的應用程式執行緒或處理程序整合事件資料表中查詢、 將事件發行到事件匯流排，然後使用本機交易標記為已發佈的事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="b4835-175">圖 8 到 22 顯示這些方法的第一個架構。</span><span class="sxs-lookup"><span data-stu-id="b4835-175">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="b4835-176">**圖 8 到 22**。</span><span class="sxs-lookup"><span data-stu-id="b4835-176">**Figure 8-22**.</span></span> <span data-ttu-id="b4835-177">不可部分完成性事件匯流排發佈事件時</span><span class="sxs-lookup"><span data-stu-id="b4835-177">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="b4835-178">圖 8 到 22 所述的方法遺漏負責檢查並確認成功的已發行的整合事件額外的背景工作微服務。</span><span class="sxs-lookup"><span data-stu-id="b4835-178">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="b4835-179">發生失敗時，該其他檢查工作者微服務可以讀取資料表中的事件，並將它們重新發行。</span><span class="sxs-lookup"><span data-stu-id="b4835-179">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="b4835-180">第二個方法： 使用事件記錄檔以資料表為佇列，並一律使用背景工作的微服務將訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="b4835-180">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="b4835-181">在此情況下，處理程序是類似的顯示圖 8-23。</span><span class="sxs-lookup"><span data-stu-id="b4835-181">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="b4835-182">這會顯示其他的微服務，並發佈事件時，資料表會是單一來源。</span><span class="sxs-lookup"><span data-stu-id="b4835-182">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="b4835-183">**圖 8-23**。</span><span class="sxs-lookup"><span data-stu-id="b4835-183">**Figure 8-23**.</span></span> <span data-ttu-id="b4835-184">不可部分完成性與背景工作的微服務事件匯流排發佈事件時</span><span class="sxs-lookup"><span data-stu-id="b4835-184">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="b4835-185">為了簡化，eShopOnContainers 範例會使用第一個方法 （不含額外的處理序或檢查 microservices） 再加上事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="b4835-185">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="b4835-186">不過，eShopOnContainers 並不會處理所有可能的失敗案例。</span><span class="sxs-lookup"><span data-stu-id="b4835-186">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="b4835-187">在實際的應用程式，部署至雲端，您也必須不怕事實會最後，會發生問題，您必須實作檢查並重新傳送的邏輯。</span><span class="sxs-lookup"><span data-stu-id="b4835-187">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="b4835-188">使用資料表為佇列可能會比第一種方法更有效，如果您有該資料表做為單一來源時發行它們透過事件匯流排的事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-188">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="b4835-189">發行事件匯流排透過整合事件時實作不可部份完成性</span><span class="sxs-lookup"><span data-stu-id="b4835-189">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="b4835-190">下列程式碼將示範如何建立單一交易涉及多個 DbContext 物件-正在更新的原始資料相關的一個內容與第二個 IntegrationEventLog 資料表相關的內容。</span><span class="sxs-lookup"><span data-stu-id="b4835-190">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="b4835-191">請注意，下列範例程式碼中的交易將不會有彈性，如果資料庫的連接時執行程式碼時有任何問題。</span><span class="sxs-lookup"><span data-stu-id="b4835-191">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="b4835-192">這會發生在雲端為基礎的系統，例如 Azure SQL DB 可能會在伺服器之間移動資料庫。</span><span class="sxs-lookup"><span data-stu-id="b4835-192">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="b4835-193">跨多個內容中實作彈性的交易，請參閱[實作有彈性的 Entity Framework Core SQL 連接](#implementing_resilient_EFCore_SQL_conns)本指南中稍後的章節。</span><span class="sxs-lookup"><span data-stu-id="b4835-193">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](#implementing_resilient_EFCore_SQL_conns) section later in this guide.</span></span>

<span data-ttu-id="b4835-194">為了清楚起見，下列範例會顯示整個程序，在單一程式碼片段中。</span><span class="sxs-lookup"><span data-stu-id="b4835-194">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="b4835-195">不過，eShopOnContainers 實作實際重構，並將此邏輯分割成多個類別，因此很容易維護。</span><span class="sxs-lookup"><span data-stu-id="b4835-195">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

<span data-ttu-id="b4835-196">建立 ProductPriceChangedIntegrationEvent 整合事件之後，會儲存原始網域作業 （更新類別目錄項目） 的交易也包含事件的持續性事件記錄檔資料表中。</span><span class="sxs-lookup"><span data-stu-id="b4835-196">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="b4835-197">如此便可在單一交易，並一律可以檢查是否已傳送事件訊息。</span><span class="sxs-lookup"><span data-stu-id="b4835-197">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="b4835-198">事件記錄檔資料表會自動更新與原始的資料庫作業，使用本機交易中針對相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b4835-198">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="b4835-199">如果有任何作業失敗時，擲回例外狀況，交易回復任何已完成的作業，因此維護網域作業與傳送的事件訊息之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="b4835-199">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="b4835-200">從訂閱接收訊息： 接收者 microservices 中的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="b4835-200">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="b4835-201">除了事件訂閱邏輯，您需要實作整合事件處理常式 （例如回呼方法） 的內部程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4835-201">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="b4835-202">此事件處理常式會是您可在此指定接收和處理特定類型的事件訊息。</span><span class="sxs-lookup"><span data-stu-id="b4835-202">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="b4835-203">事件處理常式，首先會從事件匯流排接收事件執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4835-203">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="b4835-204">然後找出要處理的元件與整合事件傳播和保存為在接收者微服務的狀態變更事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-204">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="b4835-205">比方說，如果 ProductPriceChanged 事件源自目錄微服務，它會在購物籃微服務中處理並變更以及，這個收件者籃微服務中的狀態，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="b4835-205">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="b4835-206">此事件處理常式需要確認產品是否存在於任何購物籃的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4835-206">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="b4835-207">它也會更新每個相關的購物籃行項目的項目價格。</span><span class="sxs-lookup"><span data-stu-id="b4835-207">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="b4835-208">最後，它會建立與變更相關的價格，對使用者顯示警示示圖 8-24。</span><span class="sxs-lookup"><span data-stu-id="b4835-208">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="b4835-209">**圖 8-24**。</span><span class="sxs-lookup"><span data-stu-id="b4835-209">**Figure 8-24**.</span></span> <span data-ttu-id="b4835-210">顯示項目價格變動中為購物籃，傳達整合事件</span><span class="sxs-lookup"><span data-stu-id="b4835-210">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="b4835-211">在更新訊息事件等冪</span><span class="sxs-lookup"><span data-stu-id="b4835-211">Idempotency in update message events</span></span>

<span data-ttu-id="b4835-212">更新訊息事件的重要層面是在任何時間點的通訊失敗，應該會導致重試訊息。</span><span class="sxs-lookup"><span data-stu-id="b4835-212">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="b4835-213">否則背景工作可能會嘗試發佈已發行，建立競爭條件的事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-213">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="b4835-214">您需要確定更新為等冪或它們提供足夠的資訊，以確保可以偵測到重複出現，捨棄它，並傳送回只有一個回應。</span><span class="sxs-lookup"><span data-stu-id="b4835-214">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="b4835-215">如前文所述，等冪性表示的作業可以執行多次而不會變更結果。</span><span class="sxs-lookup"><span data-stu-id="b4835-215">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="b4835-216">在傳訊環境中，為事件時進行通訊的事件，為等冪，如果可以傳遞多次而不需要變更接收者微服務的結果。</span><span class="sxs-lookup"><span data-stu-id="b4835-216">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="b4835-217">這可能需要由於的本質之事件本身，或因為系統會處理此事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-217">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="b4835-218">訊息等冪性，請務必在任何使用傳訊應用程式中，不只是在執行事件匯流排模式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b4835-218">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="b4835-219">等冪運算的範例之一是將資料插入資料表，只有該資料不是已在資料表中的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b4835-219">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="b4835-220">就不重要了多少次您執行的 insert SQL 陳述式。結果會相同，表格將包含該資料。</span><span class="sxs-lookup"><span data-stu-id="b4835-220">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="b4835-221">視需要處理的訊息，如果可能無法傳送的訊息時，因此處理的一次，也可以是等冪以外，像這樣。</span><span class="sxs-lookup"><span data-stu-id="b4835-221">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="b4835-222">比方說，如果重試邏輯造成多次傳送相同訊息寄件者，您需要確定它是等冪。</span><span class="sxs-lookup"><span data-stu-id="b4835-222">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="b4835-223">它可設計具有等冪性訊息。</span><span class="sxs-lookup"><span data-stu-id="b4835-223">It is possible to design idempotent messages.</span></span> <span data-ttu-id="b4835-224">比方說，您可以建立事件，指出 」 設定的產品價格為\$25"而不是 「 新增\$產品價格的 5。 」</span><span class="sxs-lookup"><span data-stu-id="b4835-224">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="b4835-225">您可以安全地處理第一個訊息次數，結果會相同。</span><span class="sxs-lookup"><span data-stu-id="b4835-225">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="b4835-226">不針對第二個訊息，則為 true。</span><span class="sxs-lookup"><span data-stu-id="b4835-226">That is not true for the second message.</span></span> <span data-ttu-id="b4835-227">但是，即使在第一個案例中，您可能不想處理的第一個事件，因為系統可能也傳送較新的價格變更事件，而且您將會覆寫，新的價格。</span><span class="sxs-lookup"><span data-stu-id="b4835-227">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="b4835-228">另一個範例可能會傳播至多個 「 訂閱者 」 所造成的順序完成事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-228">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="b4835-229">請務必，訂單資訊更新其他系統中只有一次，即使有重複的訊息相同的順序完成事件的事件。</span><span class="sxs-lookup"><span data-stu-id="b4835-229">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="b4835-230">並方便有某種類型的每個事件的識別，讓您可以建立邏輯，會強制執行每個事件會處理一次只能每個接收者。</span><span class="sxs-lookup"><span data-stu-id="b4835-230">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="b4835-231">某些訊息處理本質上是等冪。</span><span class="sxs-lookup"><span data-stu-id="b4835-231">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="b4835-232">比方說，如果系統會產生影像縮圖，就可能不重要產生縮圖的相關訊息已處理的次數結果會產生縮圖，以及它們是相同的每一次。</span><span class="sxs-lookup"><span data-stu-id="b4835-232">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="b4835-233">相反地，例如先呼叫信用卡付款閘道的作業可能不完全是等冪。</span><span class="sxs-lookup"><span data-stu-id="b4835-233">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="b4835-234">在這些情況下，您需要確保多次處理的訊息具有您預期的效果。</span><span class="sxs-lookup"><span data-stu-id="b4835-234">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b4835-235">其他資源</span><span class="sxs-lookup"><span data-stu-id="b4835-235">Additional resources</span></span>

-   <span data-ttu-id="b4835-236">**接受訊息等冪**（在此頁面上的子標題） [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="b4835-236">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="b4835-237">刪除重複資料整合事件訊息</span><span class="sxs-lookup"><span data-stu-id="b4835-237">Deduplicating integration event messages</span></span>

<span data-ttu-id="b4835-238">您可以確保訊息事件是傳送，並只處理一次每個訂閱者在不同層級。</span><span class="sxs-lookup"><span data-stu-id="b4835-238">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="b4835-239">一種方式為使用您正在使用此訊息基礎結構所提供的重複資料刪除功能。</span><span class="sxs-lookup"><span data-stu-id="b4835-239">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="b4835-240">另一個是在您的目的地微服務中實作自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="b4835-240">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="b4835-241">驗證在傳輸層級和應用程式層級是您的最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="b4835-241">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="b4835-242">刪除重複資料的訊息事件處理常式層級的事件</span><span class="sxs-lookup"><span data-stu-id="b4835-242">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="b4835-243">確定事件一次處理任何接收者的一個方式是藉由實作處理事件處理常式中的訊息事件時的特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="b4835-243">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="b4835-244">例如，為 eShopOnContainers 應用程式中使用的方法中，您可以看到[原始程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs)OrdersController 類別收到 CreateOrderCommand 命令時。</span><span class="sxs-lookup"><span data-stu-id="b4835-244">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="b4835-245">（我們在此情況下使用的 HTTP 要求命令不是以訊息為基礎的指令，但是您必須先以訊息為基礎的命令等冪邏輯也很類似。）</span><span class="sxs-lookup"><span data-stu-id="b4835-245">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="b4835-246">刪除重複資料的訊息時使用 RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="b4835-246">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="b4835-247">若間歇網路失敗，訊息可以重複，，而且訊息接收者必須準備好處理這些重複的訊息。</span><span class="sxs-lookup"><span data-stu-id="b4835-247">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="b4835-248">可能的話，接收者應該處理等冪的方式，優於明確重複資料刪除處理這些訊息。</span><span class="sxs-lookup"><span data-stu-id="b4835-248">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="b4835-249">根據[RabbitMQ 文件](https://www.rabbitmq.com/reliability.html#consumer)，「 如果將訊息傳遞至取用者，並再排入佇列，（因為它尚未被認可之前取用者中斷連線，例如），則 RabbitMQ 會設定已重新傳遞的旗標上它一次傳遞 （是否以相同的消費者或另一部） 時使用。</span><span class="sxs-lookup"><span data-stu-id="b4835-249">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="b4835-250">如果設定 「 已重新傳遞 」 的旗標，接收者必須考慮的帳戶，因為訊息可能已經處理。</span><span class="sxs-lookup"><span data-stu-id="b4835-250">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="b4835-251">但是，不一定。訊息可能永遠不會有之後，到達收件者從訊息代理人，可能是因為網路問題。</span><span class="sxs-lookup"><span data-stu-id="b4835-251">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="b4835-252">相反地，如果未設定 」 已重新傳遞 」 的旗標，這樣會保證的訊息已傳送一次以上。</span><span class="sxs-lookup"><span data-stu-id="b4835-252">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="b4835-253">因此，接收者使用重複資料刪除等冪的方式處理訊息的訊息中設定 「 已重新傳遞 」 旗標時，才需要。</span><span class="sxs-lookup"><span data-stu-id="b4835-253">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b4835-254">其他資源</span><span class="sxs-lookup"><span data-stu-id="b4835-254">Additional resources</span></span>

-   <span data-ttu-id="b4835-255">**事件驅動訊息**
    [*http://soapatterns.org/design\_模式/事件\_驅動\_傳訊*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="b4835-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="b4835-256">**Jimmy Bogard：重構朝向彈性： 評估結合**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="b4835-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="b4835-257">**發行-訂閱通道**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="b4835-257">**Publish-Subscribe channel**
[*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="b4835-258">**之間通訊的繫結內容**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="b4835-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="b4835-259">**最終一致性**
    [*https://en.wikipedia.org/wiki/Eventual\_一致性*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="b4835-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="b4835-260">**Philip Brown。整合策略繫結內容**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="b4835-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="b4835-261">**Chris Richardson。開發使用彙總 」、 「 事件來源和 「 CQRS-第 2 部分的交易式 Microservices**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="b4835-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="b4835-262">**Chris Richardson。事件 Sourcing 模式**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="b4835-262">**Chris Richardson. Event Sourcing pattern**
[*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="b4835-263">**簡介 事件來源**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="b4835-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="b4835-264">**事件存放區資料庫**。</span><span class="sxs-lookup"><span data-stu-id="b4835-264">**Event Store database**.</span></span> <span data-ttu-id="b4835-265">官方網站。</span><span class="sxs-lookup"><span data-stu-id="b4835-265">Official site.</span></span>
    [<span data-ttu-id="b4835-266">*https://geteventstore.com/*</span><span class="sxs-lookup"><span data-stu-id="b4835-266">*https://geteventstore.com/*</span></span>](https://geteventstore.com/)

-   <span data-ttu-id="b4835-267">**Patrick Nommensen。事件驅動的 Microservices 資料管理**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*</span><span class="sxs-lookup"><span data-stu-id="b4835-267">**Patrick Nommensen. Event-Driven Data Management for Microservices**
*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span></span>

-   <span data-ttu-id="b4835-268">**CAP 理論**
    [*https://en.wikipedia.org/wiki/CAP\_理論*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="b4835-268">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="b4835-269">**什麼是 CAP 理論？** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="b4835-269">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="b4835-270">**資料一致性入門**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="b4835-270">**Data Consistency Primer**
[*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="b4835-271">**Rick Saling。CAP 理論： 原因 」 的所有項目不同 「 雲端與網際網路**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="b4835-271">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="b4835-272">**Eric Brewer。CAP 十二年稍後： 如何變更 「 規則 」**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="b4835-272">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="b4835-273">**參與外部 (DTC) 交易**(MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="b4835-273">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="b4835-274">**Azure 服務匯流排。代理訊息： 重複的偵測**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="b4835-274">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="b4835-275">**可靠性指南**（RabbitMQ 文件） [ *https://www.rabbitmq.com/reliability.html\#取用者*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="b4835-275">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="b4835-276">[上一個](rabbitmq-event-bus-development-test-environment.md) [下一步] (test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="b4835-276">[Previous] (rabbitmq-event-bus-development-test-environment.md) [Next] (test-aspnet-core-services-web-apps.md)</span></span>
