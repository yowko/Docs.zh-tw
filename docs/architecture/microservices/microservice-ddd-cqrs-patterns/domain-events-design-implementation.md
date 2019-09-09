---
title: 領域事件： 設計和實作
description: .NET 微服務：容器化 .NET 應用程式的架構 | 深入了解領域事件，這是用來在彙總之間建立通訊的重要概念。
ms.date: 10/08/2018
ms.openlocfilehash: 5f7084ef638a1d04e0050eab447cb8903c973f45
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674255"
---
# <a name="domain-events-design-and-implementation"></a>領域事件：設計和實作

使用領域事件可明確實作您領域中變更的副作用。 換句話說 (以 DDD 術語來說)，使用領域事件可在多個彙總之間明確實作副作用。 為了提高延展性並降低資料庫鎖定的影響，您可以選擇在相同領域中的多個彙總之間使用最終一致性。

## <a name="what-is-a-domain-event"></a>什麼是領域事件？

事件是指過去發生的某件事。 領域事件是領域中發生的某件事，您想要相同領域 (同處理序) 的其他組件獲知該事件。 獲通知的組件通常會以某種方式對事件做出回應。

領域事件的重要優點是可以明確表示副作用。

例如，如果您只使用 Entity Framework，而且必須對某些事件做出反應，則您可能會撰寫需要與觸發事件內容接近的任何程式碼。 因此，規則會以隱含方式與程式碼結合，您必須查看程式碼，以便了解在該處實作的規則。

另一方面，使用領域事件明確呈現概念，因為其中涉及到 `DomainEvent` 以及至少一個 `DomainEventHandler`。

例如，在 eShopOnContainers 應用程式中建立訂單時，使用者會變成購買者，因此會引發 `OrderStartedDomainEvent` 並在 `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler` 中進行處理，如此基礎概念就顯而易見。

簡單地說，領域事件可協助您明確表示由領域專家所提供並以通用語言為基礎的領域規則。 領域事件也可以改善相同領域中類別之間的關注點分離。

就像資料庫交易一樣，請務必確保與領域事件相關的所有作業都成功完成或全都未完成。

領域事件類似傳訊樣式事件，但有一個重要的差異。 透過即時傳訊、訊息佇列、訊息代理程式或使用 AMQP 的服務匯流排，訊息一律會以非同步方式傳送，並跨處理序與電腦通訊。 這有助於整合多個限定內容、微服務或甚至是不同的應用程式。 不過，使用領域事件時，您不只希望從目前正在執行的領域作業引發事件，也希望所有副作用都會出現在相同的領域中。

領域事件及其副作用 (之後會觸發並由事件處理常式管理的動作) 應該幾乎會在相同領域 (通常是同處理序) 中立即發生。 因此，領域事件可以為同步或非同步。 不過，整合事件應該一律為非同步。

## <a name="domain-events-versus-integration-events"></a>領域事件與整合事件的比較

語意上來說，領域事件與整合事件同義，兩者都會通知剛發生的某件事。 不過，其實作必須不同。 領域事件是推送至領域事件發送器的訊息，可實作為以 IoC 容器或任何其他方法為基礎的記憶體內部中繼程序。

另一方面，整合事件的目的是將已認可的交易和更新傳播至其他子系統，不論是其他微服務、限定內容或甚至是外部應用程式。 因此，它們應該只有在成功保存實體時才會出現，否則就像整個作業從未發生過一樣。

如前所述，整合事件必須以多個微服務 (其他限定內容) 或甚至是外部系統/應用程式之間的非同步通訊為基礎。

因此，事件匯流排介面需要可在潛在遠端服務之間進行處理序間和分散式通訊的一些基礎結構。 它可以依據商業服務匯流排、佇列、用作信箱的共用資料庫，或任何其他分散式且最好為發送型傳訊系統。

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>領域事件是在相同領域中的多個彙總之間觸發副作用的慣用方法

如果執行與一個彙總執行個體相關的命令需要在一或多個額外的彙總上執行其他領域規則，您應該設計並實作領域事件所要觸發的這些副作用。 如圖 7-14 所示 (這是其中一個最重要的使用案例)，您應該使用領域事件，在相同領域模型中的多個彙總之間傳播狀態變更。

![彙總之間的一致性是透過領域事件來達成，訂單彙總會傳送 OrderStarted 領域事件，以進行處理來更新購買者彙總。 ](./media/image15.png)

**圖 7-14**。 要在相同領域中的多個彙總之間強制執行一致性的領域事件

在圖中，當使用者起始訂單時，根據識別微服務中的原始使用者資訊 (以及 CreateOrder 命令中所提供的資訊)，OrderStarted 領域事件會觸發在訂購微服務中建立「購買者」物件的程序。 第一次建立訂單時，訂單彙總會產生領域事件。

或者，您可以讓彙總根訂閱其彙總成員 (子實體) 所引發的事件。 例如，當項目價格高於特定金額或產品項目金額太高時，每個 OrderItem 子實體都會引發一個事件。 然後，彙總根可接收這些事件，並執行全域計算或彙總。

請務必了解，此事件架構通訊不會直接在彙總內實作；您必須實作領域事件處理常式。

處理領域事件是應用程式考量。 領域模型層應該只著重於領域邏輯 (也就是領域專家了解的內容)，而不是應用程式基礎結構 (例如處理常式及使用儲存機制的副作用持續性動作)。 因此，應用程式層是引發領域事件時，您應該讓領域事件處理常式觸發動作的位置。

領域事件也可用來觸發任何數目的應用程式動作，而且更重要的是，必須沒有限制才能在未來以低耦合方式增加數目。 例如，啟動訂單時，您可能想要發行領域事件，將該資訊傳播至其他彙總，或甚至是引發通知等應用程式動作。

重點是不要限制領域事件出現時所要執行的動作數目。 領域和應用程式中的動作和規則最終都會成長。 發生某件事時的副作用動作複雜度或數目會成長，但如果您的程式碼與「黏附」功能結合 (亦即，使用 `new` 建立特定物件)，則每次您需要新增動作時，也需要變更可運作及經測試的程式碼。

這項變更可能會導致新的 Bug，而此方法也會違反 [SOLID](https://en.wikipedia.org/wiki/SOLID) 的 [Open–closed principl](https://en.wikipedia.org/wiki/Open/closed_principle) (開啟/關閉準則)。 不僅如此，協調作業的原始類別會不斷成長，這違背[單一功能原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)。

相反地，如果您使用領域事件，就可以透過此方法分離職責，來建立更細緻且低耦合的實作：

1. 傳送命令 (例如 CreateOrder)。
2. 接收命令處理常式中的命令。
   - 執行單一彙總的交易。
   - (選擇性) 引發副作用的領域事件 (例如 OrderStartedDomainEvent)。
3. 處理領域事件 (在目前的處理序中)，這些事件會在多個彙總或應用程式動作中執行不限數目的副作用。 例如：
   - 確認或建立購買者和付款方式。
   - 建立相關的整合事件並傳送至事件匯流排，以在微服務之間傳播狀態，或觸發外部動作，例如將電子郵件傳送給購買者。
   - 處理其他副作用。

如圖 7-15 所示，從同一個領域事件開始，您可以處理與領域中其他彙總相關的多個動作，或您需要在微服務 (與整合事件和事件匯流排連線) 之間執行的其他應用程式動作。

![應用程式層中可以有數個用於相同領域事件的處理常式，一個處理常式可以解決彙總之間的一致性問題，另一個處理常式可以發佈整合事件，讓其他微服務可以對其執行某個動作。](./media/image16.png)

**圖 7-15**。 處理每個領域的多個動作

事件處理常式通常是在應用程式層中，因為您會針對微服務的行為使用儲存機制或應用程式 API 等基礎結構物件。 就這點而言，事件處理常式類似命令處理常式，因此兩者都屬於應用程式層。 重要的差異在於命令只能處理一次。 因為可能有多個接收者或事件處理常式 (每個處理常式的目的不同) 接收領域事件，所以領域事件可能處理零至 *n* 次。

不限制每個領域事件的處理常式數目，可讓您新增所需數目的領域規則，而不影響目前的程式碼。 例如，實作下列商務規則，可能與新增幾個事件處理常式 (或甚至只有一個) 一樣容易：

> 當顧客在商店購買任意數目的訂單總金額超過 6000 USD 時，會對每個新的訂單套用 10% 的折扣，並以電子郵件通知顧客未來訂單的折扣。

## <a name="implement-domain-events"></a>實作領域事件

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

如稍早所述，事件的一個重要特性是，由於事件是過去發生的某件事，不應該變更。 因此，它必須是不可變的類別。 您可以在上一個程式碼中看到屬性是唯讀的。 沒有任何方式可更新物件，您只能在建立時設定值。

在這裡要特別強調的是，如果領域事件是以非同步方式處理，並使用需要序列化和還原序列化事件物件的佇列，屬性必須是「私人集合」而不是唯讀，因此還原序列化程式可以在清除佇列時指派值。 因為網域事件發佈/訂閱是使用 MediatR 以同步方式實作，所以這在訂購微服務中不成問題。

### <a name="raise-domain-events"></a>引發領域事件

下一個問題是如何引發領域事件，使它抵達其相關的事件處理常式。 您可以使用多個方法。

Udi Dahan 原本建議使用靜態類別來管理及引發事件 (如數篇相關的文章所示，例如 [Domain Events - Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/) (領域事件 - 續篇))。 這可能包含名為 DomainEvents 的靜態類別，該類別會在呼叫時，使用 `DomainEvents.Raise(Event myEvent)` 等語法立即引發領域事件。 Jimmy Bogard 已撰寫一篇部落格文章 ([Strengthening your domain:Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/))，建議類似方法。

不過，當領域事件類別為靜態時，它也會立即分派至處理常式。 這會使得測試和偵錯更加困難，因為在引發事件之後會立即執行具有副作用邏輯的事件處理常式。 當您進行測試和偵錯時，您只想要專注於目前彙總類別中正在發生的事件，而不想要因為與其他彙總或應用程式邏輯相關的副作用，而突然被重新導向至其他事件處理常式。 這就是其他方法進化的原因，如下一節中所述。

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>引發和分派事件的延後方法

您最好將領域事件新增至集合，然後在認可交易 (如同 EF 中的 SaveChanges)「之前」  或「之後」   分派這些領域事件，而不是直接分派至領域事件處理常式 (Jimmy Bogard 在 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/) (更佳的領域事件模式) 的這篇文章中說明此方法)。

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
         _domainEvents?.Remove(eventItem);
     }
     //... Additional code
}
```

當您想要引發事件時，您只要從彙總根實體之任何方法的程式碼將它新增至事件集合。

下列程式碼 (屬於 [eShopOnContainers 的 Order aggregate-root](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)) 顯示一個範例：

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
        // event handlers) performed through the DbContext will be committed
        var result = await base.SaveChangesAsync();
    }
}
```

在此程式碼中，您會將實體事件分派至其各自的事件處理常式。

整體結果是您將引發領域事件 (記憶體內部清單中的一個簡單新增)，與將它分派至事件處理常式的職責分離。 此外，根據您使用的發送器類型，您可以利用同步或非同步方式來分派事件。

請注意，交易界限在此扮演重要的角色。 如果您的工作單位和交易可跨多個彙總 (如同使用 EF Core 和關聯式資料庫時)，則會正常運作。 但如果交易不可跨多個彙總 (例如當您使用 Azure CosmosDB 等 NoSQL 資料庫時)，您必須實作額外的步驟，才能達到一致性。 這是永續性無知不通用的另一個原因，它需要您使用的儲存體系統。 

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>跨彙總的單一交易與跨彙總的最終一致性之比較

要在多個彙總之間執行單一交易，還是要依賴這些彙總之間的最終一致性，是具爭議性的問題。 許多 DDD 作者 (像是 Eric Evans 和 Vaughn Vernon) 提倡一個交易等於一個彙總的規則，因此支持在多個彙總之間取得最終一致性。 例如，Eric Evans 在 *Domain-Driven Design* 一書中表示：

> 任何跨彙總的規則不必總是處於最新狀態。 透過事件處理、批次處理或其他更新機制，即可解析一段特定時間內的其他相依性 (第 128 頁)。

Vaughn Vernon 在 [Effective Aggregate DesignPart II:Making Aggregates Work Together](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf) (有效彙總設計第二部分：讓彙總搭配運作) 中表示下列看法：

> 因此，如果在一個彙總執行個體上執行命令需要在一或多個彙總上執行其他商務規則，請使用最終一致性 \[...\]沒有支援 DDD 模型中最終一致性的可行方法。 彙總方法會發行領域事件，及時傳遞至一或多個非同步訂閱者。

此原理是以更細緻的交易為基礎，而不是以跨許多彙總或實體的交易為基礎。 其概念是在第二個案例中，資料庫鎖定數目在具有高延展性需求的大型應用程式中會很大。 可高度擴充的應用程式不需要在多個彙總之間有立即交易一致性，認清這點事實有助於接受最終一致性概念。 企業通常不需要不可部分完成變更，而且在任何情況下，領域專家都有責任指出特定作業是否需要不可部分完成交易。 如果作業一律需要在多個彙總之間有不可部分完成交易，您可能會詢問彙總是否應該更大或設計是否不正確。

不過，其他開發人員以及像是 Jimmy Bogard 的架構設計人員接受單一交易橫跨數個彙總，但僅限於這些額外的彙總與相同原始命令的副作用相關時。 例如，Bogard 在 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/) (更佳的領域事件模式) 中表示：

> 一般而言，我希望領域事件的副作用出現在相同的邏輯交易內，但不一定要在引發領域事件的相同範圍內 \[...\]在我們認可交易之前，我們會將事件分派至其各自的處理常式。

如果您在認可原始交易「之前」  分派領域事件，這是因為您想要將這些事件的副作用包含在相同的交易中。 例如，如果 EF DbContext SaveChanges 方法失敗，交易將會復原所有變更，包括相關領域事件處理常式所實作之任何副作用作業的結果。 這是因為 DbContext 存留期範圍預設會定義為 "scoped"。 因此，DbContext 物件會在相同範圍或物件圖形內要具現化的多個儲存機制物件之間共用。 開發 Web API 或 MVC 應用程式時，這會與 HttpRequest 範圍一致。

實際上，這兩種方法 (單一不可部分完成交易和最終一致性) 都正確。 它其實取決於您的領域或商務需求，以及領域專家給您的建議。 它也取決於您需要的服務延展性 (交易越細緻，對資料庫鎖定的影響越低)。 此外，它取決您願意對程式碼的投資，因為最終一致性需要更複雜的程式碼，才能偵測彙總之間可能不一致性的情況，並需要實作補償動作。 請考慮下列情況，如果您將變更認可至原始彙總，之後當分派事件時發生問題，而且事件處理常式無法認可其副作用，則彙總之間會有不一致的情況。

一個允許補償動作的方法是將領域事件儲存在其他資料庫資料表中，讓它們可以成為原始交易的一部分。 之後，您可以有一個批次程序，藉由比較事件清單與彙總的目前狀態，來偵測不一致性的情況並執行補償動作。 補償動作屬於複雜主題，需要您深入分析，包括與企業用戶以及領域專家進行討論。

在任何情況下，您都可以選擇所需的方法。 但初始延後方法 (在認可前引發事件以便您使用單一交易) 是使用 EF Core 和關聯式資料庫時的最簡單方法。 實作起來更容易，而且在許多商務案例中很有效。 這也是 eShopOnContainers 中的訂購微服務所使用的方法。

但您實際上如何將這些事件分派至其各自的事件處理常式？ 您在上一個範例中看到的 `_mediator` 物件為何？ 這與您用來對應事件與其事件處理常式的技術和成品有關。

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>領域事件發送器：事件與事件處理常式的對應

一旦您可以分派或發行事件，您需要某種會發行事件的成品，讓每個相關的處理常式可以取得它，並根據該事件來處理副作用。

一個方法是即時傳訊系統或甚至事件匯流排，可能會根據服務匯流排，而不是記憶體內部事件。 不過，在第一個案例中，即時傳訊對處理領域事件會過當，因為您只需要處理相同處理序 (也就是相同領域和應用程式層) 中的這些事件。

另一個方法是藉由在 IoC 容器中使用類型註冊，將事件對應至多個事件處理常式，因此您可以動態推斷分派事件的位置。 換句話說，您需要知道需要取得特定事件的事件處理常式。 圖 7-16 顯示此方法的簡化方法。

![相依性插入可以用來建立事件與事件處理常式的關聯，這是 MediatR 所使用的方法](./media/image17.png)

**圖 7-16**。 使用 IoC 的領域事件發送器

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

根據事件與事件處理常式之間的關聯性 (可視為訂閱)，MediatR 成品可探索每個事件的所有事件處理常式，並觸發每一個事件處理常式。

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

最後值得一提的是，您有時可能會想要在多個微服務之間傳播事件。 這項傳播是整合事件，而且可透過事件匯流排從特定領域事件處理常式發佈。

## <a name="conclusions-on-domain-events"></a>領域事件結論

如前所述，使用領域事件可明確實作您領域中變更的副作用。 以 DDD 術語來說，使用領域事件可在一或多個彙總之間明確實作副作用。 此外，為了提高延展性並降低資料庫鎖定的影響，請在相同領域中的多個彙總之間使用最終一致性。

## <a name="additional-resources"></a>其他資源

- **Greg Young。What is a Domain Event?** (什麼是領域事件？) \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Jan Stenberg：Domain Events and Eventual Consistency** (領域事件與最終一致性) \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard：A better domain events pattern** (更佳的領域事件模式) \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon：Effective Aggregate Design Part II:Making Aggregates Work Together** (有效彙總設計第二部分：讓彙總搭配運作) \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard：Strengthening your domain:Domain Events** (加強您的領域：領域事件) \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Tony Truong：Domain Events Pattern Example** (領域事件模式範例) \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **Udi Dahan.How to create fully encapsulated Domain Models** (如何建立完整封裝式領域模型) \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **Udi Dahan.Domain Events – Take 2** (領域事件 - 第 2 步) \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **Udi Dahan.Domain Events – Salvation** (領域事件 - 解答) \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan Kronquist：Don't publish Domain Events, return them!** (別發佈領域事件，傳回它們！) \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de la Torre：Domain Events vs.Integration Events in DDD and microservices architectures** (DDD 與微服務架構中的整合事件) \
  <https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[上一頁](client-side-validation.md)
>[下一頁](infrastructure-persistence-layer-design.md)
