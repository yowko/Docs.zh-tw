---
title: 領域事件： 設計和實作
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 領域事件、設計和實作
keywords: Docker, 微服務, ASP.NET, 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bec1341df85f86d5f2aa15753a11a9c4a2d0173f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="domain-events-design-and-implementation"></a>領域事件：設計和實作

使用領域事件可明確實作您領域中變更的副作用。 換句話說 (以 DDD 術語來說)，使用領域事件可在多個彙總之間明確實作副作用。 為了提高延展性並降低資料庫鎖定的影響，您可以選擇在相同領域中的多個彙總之間使用最終一致性。

## <a name="what-is-a-domain-event"></a>什麼是領域事件？

事件是指過去發生的某件事。 領域事件邏輯上是指特定領域中發生的某件事，也是您想要相同領域 (同處理序) 的其他部分注意並可能回應的某件事。

領域事件的一項重要優點是，領域中發生某件事之後的副作用可以明確 (而不是隱含) 表示。 這些副作用必須一致，因此與商務工作相關的所有作業不是全部發生，就是完全不會發生。 此外，領域事件可以改進相同領域中類別之間的關注點分離。

例如，如果您只使用 Entity Framework 和實體或甚至是彙總，而且使用案例必須引發副作用，則這些副作用會在發生某件事之後，以結合程式碼中的隱含概念來實作。 但如果您只看到該程式碼，您可能不知道該程式碼 (副作用) 是主要作業的一部分或真的是副作用。 相反地，使用領域事件可讓概念明確並成為通用語言的一部分。 例如，在 eShopOnContainers 應用程式中，建立訂單不只與訂單相關，還會根據原始使用者來更新或建立購買者彙總，因為使用者必須下訂單才會成為購買者。 如果您使用領域事件，您可以明確表示由領域專家所提供並以通用語言為基礎的領域規則。

領域事件有點類似傳訊樣式事件，但有一個重要的差異。 透過即時傳訊、訊息佇列、訊息代理程式或使用 AMPQ 的服務匯流排，訊息一律會以非同步方式傳送，並跨處理序與電腦通訊。 這有助於整合多個限定內容、微服務或甚至是不同的應用程式。 不過，使用領域事件時，您不只希望從目前正在執行的領域作業引發事件，也希望所有副作用都會出現在相同的領域中。

領域事件及其副作用 (之後會觸發並由事件處理常式管理的動作) 應該幾乎會在相同領域 (通常是同處理序) 中立即發生。 因此，領域事件可以為同步或非同步。 不過，整合事件應該一律為非同步。

## <a name="domain-events-versus-integration-events"></a>領域事件與整合事件的比較

語意上來說，領域事件與整合事件同義，兩者都會通知剛發生的某件事。 不過，其實作必須不同。 領域事件是推送至領域事件發送器的訊息，可實作為以 IoC 容器或任何其他方法為基礎的記憶體內部中繼程序。

另一方面，整合事件的目的是將已認可的交易和更新傳播至其他子系統，不論是其他微服務、限定內容或甚至是外部應用程式。 因此，只有在成功保存實體時才應該出現，因為在許多情況下，如果失敗，整個作業實際上永遠不會發生。

此外，如前所述，整合事件必須以多個微服務 (其他限定內容) 或甚至是外部系統/應用程式之間的非同步通訊為基礎。 因此，事件匯流排介面需要可在潛在遠端服務之間進行處理序間和分散式通訊的一些基礎結構。 它可以依據商業服務匯流排、佇列、用作信箱的共用資料庫，或任何其他分散式且最好為發送型傳訊系統。

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>領域事件是在相同領域中的多個彙總之間觸發副作用的慣用方法

如果執行與一個彙總執行個體相關的命令需要在一或多個額外的彙總上執行其他領域規則，您應該設計並實作領域事件所要觸發的這些副作用。 如圖 9-14 所示 (這是其中一個最重要的使用案例)，您應該使用領域事件，在相同領域模型中的多個彙總之間傳播狀態變更。

![](./media/image15.png)

**圖 9-14**： 要在相同領域中的多個彙總之間強制執行一致性的領域事件

在圖中，當使用者起始訂單時，根據識別微服務中的原始使用者資訊 (以及 CreateOrder 命令中所提供的資訊)，OrderStarted 領域事件會觸發在訂購微服務中建立「購買者」物件的程序。 第一次建立訂單時，訂單彙總會產生領域事件。

或者，您可以讓彙總根訂閱其彙總成員 (子實體) 所引發的事件。 例如，當項目價格高於特定金額或產品項目金額太高時，每個 OrderItem 子實體都會引發一個事件。 然後，彙總根可接收這些事件，並執行全域計算或彙總。

請務必了解，此事件架構通訊不會直接在彙總內實作；您必須實作領域事件處理常式。 處理領域事件是應用程式考量。 領域模型層應該只著重於領域邏輯 (也就是領域專家了解的內容)，而不是應用程式基礎結構 (例如處理常式及使用儲存機制的副作用持續性動作)。 因此，應用程式層是引發領域事件時，您應該讓領域事件處理常式觸發動作的位置。

領域事件也可用來觸發任何數目的應用程式動作，而且更重要的是，必須沒有限制才能在未來以低耦合方式增加數目。 例如，啟動訂單時，您可能想要發行領域事件，將該資訊傳播至其他彙總，或甚至是引發通知等應用程式動作。

重點是不要限制領域事件出現時所要執行的動作數目。 領域和應用程式中的動作和規則最終都會成長。 發生某件事時的副作用動作複雜度或數目會成長，但如果您的程式碼與 “glue” 結合 (亦即只使用 C\# 中的新關鍵字具現化物件)，則每次您需要新增動作時，都需要變更原始程式碼。 這可能會導致新的錯誤 (bug)，因為每個新的需求都需要您變更原始程式碼流程。 這違背 [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) 的[開閉原則](https://en.wikipedia.org/wiki/Open/closed_principle)。 不僅如此，協調作業的原始類別會不斷成長，這違背[單一功能原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)。

相反地，如果您使用領域事件，就可以透過此方法分離職責，來建立更細緻且低耦合的實作：

1.  傳送命令 (例如 CreateOrder)。
2.  接收命令處理常式中的命令。
    -   執行單一彙總的交易。
    -   (選擇性) 引發副作用的領域事件 (例如 OrderStartedDomainEvent)。
1.  處理領域事件 (在目前的處理序中)，這些事件會在多個彙總或應用程式動作中執行不限數目的副作用。 例如: 
    -   確認或建立購買者和付款方式。
    -   建立相關的整合事件並傳送至事件匯流排，以在微服務之間傳播狀態，或觸發外部動作，例如將電子郵件傳送給購買者。
    -   處理其他副作用。

如圖 9-15 所示，從同一個領域事件開始，您可以處理與領域中其他彙總相關的多個動作，或您需要在連接至整合事件和事件匯流排的微服務之間執行的其他應用程式動作。

![](./media/image16.png)

**圖 9-15**： 處理每個領域的多個動作

事件處理常式通常是在應用程式層中，因為您會針對微服務的行為使用儲存機制或應用程式 API 等基礎結構物件。 就這點而言，事件處理常式類似命令處理常式，因此兩者都屬於應用程式層。 重要的差異在於命令只能處理一次。 因為可能有多個接收者或事件處理常式 (每個處理常式的目的不同) 接收領域事件，所以領域事件可能處理零至 *n* 次。

每個領域事件之處理常式數目不限的可能性，讓您可以新增更多領域規則，而不影響您目前的程式碼。 例如，實作以下必須在事件之後立即發生的商務規則，可能與新增幾個事件處理常式 (或甚至只有一個) 一樣容易：

當顧客在商店購買任意數目的訂單總金額超過 6000 USD 時，會對每個新的訂單套用 10% 的折扣，並以電子郵件通知顧客未來訂單的折扣。

## <a name="implementing-domain-events"></a>實作領域事件

在 C# 中，領域事件單純是資料保留結構或類別 (例如 DTO)，其中包含與領域中剛發生的事件相關的所有資訊，如下列範例所示：

```csharp
public class OrderStartedDomainEvent : INotification
{
    public string UserId { get; }
    public int CardTypeId { get; }
    public string CardNumber { get; }
    public string CardSecurityNumber { get; }
    public string CardHolderName { get; }
    public DateTime CardExpiration { get; }
    public Order Order { get; }

    public OrderStartedDomainEvent(Order order,
                                   int cardTypeId, string cardNumber,
                                   string cardSecurityNumber, string cardHolderName,
                                   DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

這基本上是保留與 OrderStarted 事件相關之所有資料的類別。

根據領域的通用語言，由於事件是過去發生的某件事，因此事件的類別名稱應該以過去式動詞來表示，例如 OrderStartedDomainEvent 或 OrderShippedDomainEvent。 這是在 eShopOnContainers 的訂購微服務中實作領域事件的方式。

如稍早所述，事件的一個重要特性是，由於事件是過去發生的某件事，不應該變更。 因此，它必須是不可變的類別。 如您在上一個程式碼中所見，屬性在物件外部是唯讀的。 當您建立事件物件時，更新物件的唯一方式是透過建構函式。

### <a name="raising-domain-events"></a>引發領域事件

下一個問題是如何引發領域事件，使它抵達其相關的事件處理常式。 您可以使用多個方法。

Udi Dahan 原本建議使用靜態類別來管理及引發事件 (如數篇相關的文章所示，例如 [Domain Events - Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/) (領域事件 - 續篇))。 這可能包含名為 DomainEvents 的靜態類別，該類別會在呼叫時，使用 DomainEvents.Raise(Event myEvent) 等語法立即引發領域事件。 Jimmy Bogard 所撰寫的部落格文章 ([Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/) (增強您的領域：領域事件)) 建議類似的方法。

不過，當領域事件類別為靜態時，它也會立即分派至處理常式。 這會使得測試和偵錯更加困難，因為在引發事件之後會立即執行具有副作用邏輯的事件處理常式。 當您進行測試和偵錯時，您只想要專注於目前彙總類別中正在發生的事件，而不想要因為與其他彙總或應用程式邏輯相關的副作用，而突然被重新導向至其他事件處理常式。 這就是其他方法進化的原因，如下一節中所述。

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>引發和分派事件的延後方法

您最好將領域事件新增至集合，然後在認可交易 (如同 EF 中的 SaveChanges)「之前」或「之後」分派這些領域事件，而不是直接分派至領域事件處理常式 (Jimmy Bogard 在 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/) (更佳的領域事件模式) 的這篇文章中說明此方法)。

請務必決定在認可交易之前或之後傳送領域事件，因為這會決定您將副作用加入作為相同交易的一部分，還是加入不同的交易。 在後者的情況下，您需要處理多個彙總之間的最終一致性。 下一節將討論這個主題。

eShopOnContainers 使用延後方法。 首先，您會將實體中正在發生的事件新增至每個實體的事件集合或清單。 該清單應該是實體物件的一部分，最好是基底實體類別的一部分，如實體基底類別的下列範例所示：

```csharp
public abstract class Entity
{
     //... 
    private List<INotification> _domainEvents;
    public List<INotification> DomainEvents => _domainEvents;

    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

當您想要引發事件時，您只要從彙總根實體之任何方法的程式碼將它新增至事件集合。

下列程式碼 (屬於 [eShopOnContainers 的 OrderAggrergateRoot](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)) 顯示一個範例：

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

請注意，AddDomainEvent 方法只會將事件新增至清單。 尚未分派任何事件，而且尚未叫用任何事件處理常式。

您實際上想要稍後在將交易認可至資料庫時分派事件。 如果您使用 Entity Framework Core，也就是在 EF DbContext 的 SaveChanges 方法中 (如下列程式碼所示)：

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<bool> SaveEntitiesAsync(CancellationToken cancellationToken = default(CancellationToken))
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.        
        await _mediator.DispatchDomainEventsAsync(this);

        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

在此程式碼中，您會將實體事件分派至其各自的事件處理常式。

整體結果是您將引發領域事件 (記憶體內部清單中的一個簡單新增)，與將它分派至事件處理常式的職責分離。 此外，根據您使用的發送器類型，您可以利用同步或非同步方式來分派事件。

請注意，交易界限在此扮演重要的角色。 如果您的工作單位和交易可跨多個彙總 (如同使用 EF Core 和關聯式資料庫時)，則會正常運作。 但如果交易不可跨多個彙總 (例如當您使用 Azure DocumentDB 等 NoSQL 資料庫時)，您必須實作額外的步驟，才能達到一致性。 這是永續性無知不通用的另一個原因，它需要您使用的儲存體系統。

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>跨彙總的單一交易與跨彙總的最終一致性之比較

要在多個彙總之間執行單一交易，還是要依賴這些彙總之間的最終一致性，是具爭議性的問題。 許多 DDD 作者 (像是 Eric Evans 和 Vaughn Vernon) 提倡一個交易等於一個彙總的規則，因此支持在多個彙總之間取得最終一致性。 例如，Eric Evans 在 *Domain-Driven Design* 一書中表示：

任何跨彙總的規則不必總是處於最新狀態。 透過事件處理、批次處理或其他更新機制，即可解析一段特定時間內的其他相依性 (第 128 頁)。

Vaughn Vernon 在 [Effective Aggregate DesignPart II: Making Aggregates Work Together](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf) (有效彙總設計第二部分：讓彙總搭配運作) 中表示：

因此，如果在一個彙總執行個體上執行命令需要在一或多個彙總上執行其他商務規則，請使用最終一致性 \[...\]沒有支援 DDD 模型中最終一致性的可行方法。 彙總方法會發行領域事件，及時傳遞至一或多個非同步訂閱者。

此原理是以更細緻的交易為基礎，而不是以跨許多彙總或實體的交易為基礎。 其概念是在第二個案例中，資料庫鎖定數目在具有高延展性需求的大型應用程式中會很大。 可高度擴充的應用程式不需要在多個彙總之間有立即交易一致性，認清這點事實有助於接受最終一致性概念。 企業通常不需要不可部分完成變更，而且在任何情況下，領域專家都有責任指出特定作業是否需要不可部分完成交易。 如果作業一律需要在多個彙總之間有不可部分完成交易，您可能會詢問彙總是否應該更大或設計是否不正確。

不過，其他開發人員以及像是 Jimmy Bogard 的架構設計人員接受單一交易橫跨數個彙總，但僅限於這些額外的彙總與相同原始命令的副作用相關時。 例如，Bogard 在 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/) (更佳的領域事件模式) 中表示：

一般而言，我希望領域事件的副作用出現在相同的邏輯交易內，但不一定要在引發領域事件的相同範圍內 \[...\]在我們認可交易之前，我們會將事件分派至其各自的處理常式。

如果您在認可原始交易「之前」分派領域事件，這是因為您想要將這些事件的副作用包含在相同的交易中。 例如，如果 EF DbContext SaveChanges 方法失敗，交易將會復原所有變更，包括相關領域事件處理常式所實作之任何副作用作業的結果。 這是因為 DbContext 存留期範圍預設會定義為 "scoped"。 因此，DbContext 物件會在相同範圍或物件圖形內要具現化的多個儲存機制物件之間共用。 開發 Web API 或 MVC 應用程式時，這會與 HttpRequest 範圍一致。

事實上，這兩種方法 (單一不可部分完成交易和最終一致性) 都正確。 它其實取決於您的領域或商務需求，以及領域專家給您的建議。 它也取決於您需要的服務延展性 (交易越細緻，對資料庫鎖定的影響越低)。 此外，它取決您願意對程式碼的投資，因為最終一致性需要更複雜的程式碼，才能偵測彙總之間可能不一致性的情況，並需要實作補償動作。 請考慮下列情況，如果您將變更認可至原始彙總，之後當分派事件時發生問題，而且事件處理常式無法認可其副作用，則彙總之間會有不一致的情況。

一個允許補償動作的方法是將領域事件儲存在其他資料庫資料表中，讓它們可以成為原始交易的一部分。 之後，您可以有一個批次程序，藉由比較事件清單與彙總的目前狀態，來偵測不一致性的情況並執行補償動作。 補償動作屬於複雜主題，需要您深入分析，包括與企業用戶以及領域專家進行討論。

在任何情況下，您都可以選擇所需的方法。 但初始延後方法 (在認可前引發事件以便您使用單一交易) 是使用 EF Core 和關聯式資料庫時的最簡單方法。 實作起來更容易，而且在許多商務案例中很有效。 這也是 eShopOnContainers 中的訂購微服務所使用的方法。

但您實際上如何將這些事件分派至其各自的事件處理常式？ 您在上一個範例中看到的 \_mediator 物件是什麼？ 這與您可以用來對應事件與其事件處理常式的技術和成品有關。

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>領域事件發送器：事件與事件處理常式的對應

一旦您可以分派或發行事件，您需要某種會發行事件的成品，讓每個相關的處理常式可以取得它，並根據該事件來處理副作用。

一個方法是即時傳訊系統或甚至事件匯流排，可能會根據服務匯流排，而不是記憶體內部事件。 不過，在第一個案例中，即時傳訊對處理領域事件會過當，因為您只需要處理相同處理序 (也就是相同領域和應用程式層) 中的這些事件。

另一個方法是藉由在 IoC 容器中使用類型登錄，將事件對應至多個事件處理常式，讓您可以動態推斷分派事件的目的地。 換句話說，您需要知道需要取得特定事件的事件處理常式。 圖 9-16 顯示經過簡化的方法。

![](./media/image17.png)

**圖 9-16**： 使用 IoC 的領域事件發送器

您可以建立所有連接和成品，自行實作該方法。 不過，您也可以使用 [MediatR](https://github.com/jbogard/MediatR) 等可用的程式庫，這些程式庫基本上會使用您的 IoC 容器。 因此，您可以直接使用預先定義的介面和中繼程序物件的發行/分派方法。

在程式碼中，您必須先在 IoC 容器中登錄事件處理常式類型，如 [eShopOnContainers 訂購微服務](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)的下列範例所示：

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement IAsyncNotificationHandler<>)
        // in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
                                       .GetTypeInfo().Assembly)
                                         .AsClosedTypesOf(typeof(IAsyncNotificationHandler<>));
        // Other registrations ...
    }
}
```

此程式碼會先尋找保留任何處理常式的組件，以識別包含領域事件處理常式的組件 (使用 typeof(ValidateOrAddBuyerAggregateWhenXxxx)，但您可以選擇任何其他事件處理常式來尋找組件)。 由於所有事件處理常式都會實作 IAsyncNotificationHandler 介面，因此程式碼會接著直接搜尋這些類型並登錄所有事件處理常式。

### <a name="how-to-subscribe-to-domain-events"></a>如何訂閱領域事件

當您使用 MediatR 時，每個事件處理常式必須使用 INotificationHandler 介面的泛型參數所提供的事件類型，如下列程式碼所示：

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

根據事件與事件處理常式之間的關聯性 (可視為訂閱)，MediatR 成品可探索每個事件的所有事件處理常式，並觸發每個事件處理常式。

### <a name="how-to-handle-domain-events"></a>如何處理領域事件

最後，事件處理常式通常會實作應用程式層程式碼，該程式碼使用基礎結構儲存機制來取得所需的額外彙總，並執行副作用領域邏輯。 下列 [eShopOnContainers 領域事件處理常式程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)顯示一個實作範例。

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
                   : INotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;

    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // ...Parameter validations...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ? orderStartedEvent.CardTypeId : 1;        
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;

        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }

        buyer.VerifyOrAddPaymentMethod(cardTypeId,
                                       $"Payment Method on {DateTime.UtcNow}",
                                       orderStartedEvent.CardNumber,
                                       orderStartedEvent.CardSecurityNumber,
                                       orderStartedEvent.CardHolderName,
                                       orderStartedEvent.CardExpiration,
                                       orderStartedEvent.Order.Id);

        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer) 
                                                                      : _buyerRepository.Add(buyer);

        await _buyerRepository.UnitOfWork
                .SaveEntitiesAsync();

        // Logging code using buyerUpdated info, etc.
    }
}
```

上述領域事件處理常式程式碼會視為應用程式層程式碼，因此它使用基礎結構儲存機制，如下一節的基礎結構持續性層中所述。 事件處理常式也可以使用其他基礎結構元件。

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>領域事件可以產生要在微服務界限以外發行的整合事件

最後值得一提的是，您有時可能會想要在多個微服務之間傳播事件。 這會視為整合事件，而且可透過事件匯流排從特定領域事件處理常式發行。

## <a name="conclusions-on-domain-events"></a>領域事件結論

如前所述，使用領域事件可明確實作您領域中變更的副作用。 以 DDD 術語來說，使用領域事件可在一或多個彙總之間明確實作副作用。 此外，為了提高延展性並降低資料庫鎖定的影響，請在相同領域中的多個彙總之間使用最終一致性。

## <a name="additional-resources"></a>其他資源

-   **Greg Young。什麼是領域事件？**
    [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg：領域事件與最終一致性**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard：更佳的領域事件模式**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon：有效的彙總設計第 2 部分：使彙總共同作業**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard：加強您的領域：領域事件**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *

-   **Tony Truong：領域事件模式範例**
    [*https://www.tonytruong.net/domain-events-pattern-example/*](https://www.tonytruong.net/domain-events-pattern-example/)

-   **Udi Dahan.如何建立完整封裝式領域模型**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **Udi Dahan.領域事件 - 第 2 步**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **Udi Dahan.領域事件 - 解答**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist：別發佈領域事件，傳回它們！**
    [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesar de la Torre：Domain Events vs.DDD 與微服務架構中的整合事件**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[上一個] (client-side-validation.md) [下一個] (infrastructure-persistence-layer-design.md)
