---
title: "網域的事件。 設計和實作"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |網域事件、 設計和實作"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2d98b302be4ee72d8225526944fc3e41cbadcb5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="domain-events-design-and-implementation"></a>網域事件： 設計和實作

使用網域事件來明確地實作您的網域中的變更的副作用。 在其他字，和使用 DDD 術語中，使用網域事件以明確實作跨多個彙總的副作用。 （選擇性） 更好的延展性較資料庫鎖定的影響，請使用相同的網域中的彙總之間的最終一致性。

## <a name="what-is-a-domain-event"></a>什麼是網域事件？

事件是發生在過去的項目。 網域事件以邏輯方式，是發生在特定網域的項目，項目您想要注意和可能反應的相同網域 （同處理序） 的其他部分。

網域事件中的重要優點是之後在網域中發生問題的副作用可能會明確地以而不是以隱含方式。 這些效果必須一致，因此所有作業與商務工作相關的情形可能發生的側邊或無一。 此外，網域事件可讓更好的考量，在相同網域中的類別之間的分隔。

比方說，如果您只要使用只是 Entity Framework 和實體或甚至是彙總，如果必須有一個使用案例所觸發的副作用，這些會實作為繫結的程式碼中的隱含概念之後發生。 但是，如果您只看到該程式碼，您可能不知道該程式碼 （副作用） 有主要作業的一部分，或如果這是真的副作用。 相反地，使用網域事件可讓概念明確和通用語言的一部分。 比方說，eShopOnContainers 應用程式中建立訂單不幾乎的順序。它會更新，或建立買方彙總根據原始的使用者，因為使用者不是買方就地訂單之前。 如果您使用網域事件時，您可以明確地表示該網域以規則為基礎的通用網域專家所提供的語言。

網域事件是有點像訊息樣式事件，但有一個重要的差異。 實際的訊息、 訊息佇列，訊息代理程式，或使用 AMPQ 服務匯流排，訊息一律以非同步方式傳送，並跨程序和機器通訊。 這是適用於多個繫結內容、 microservices 或甚至不同的應用程式整合。 然而，有網域事件中，您想要引發事件，從網域作業目前正在執行，但您想要在相同網域中發生任何副作用。

網域事件和其副作用 （所觸發的動作之後所管理的事件處理常式） 應該幾乎會立即發生，通常是同處理序，並在相同網域中。 因此，網域事件可以同步或非同步。 整合事件，不過，應該一律為非同步。

## <a name="domain-events-versus-integration-events"></a>網域與整合事件的事件

網域和整合事件語意上來說，是相同的東西： 項目剛好的通知。 不過，其實作必須不同。 定義域事件是只推入到網域事件發送器，這可能會實作為 IoC 容器或任何其他方法為基礎的記憶體中傳遞的訊息。

相反地，整合事件的目的是傳播已認可的交易與更新其他子系統，無論是其他 microservices、 繫結的內容或外部的應用程式。 因此，它們應該只当成功保存實體，因為在許多情況下如果失敗，整個作業實際上永遠不會發生。

此外，以及所述，整合事件必須以多個 microservices （其他繫結內容中） 或外部系統/應用程式之間的非同步通訊。 因此，事件匯流排介面需要一些基礎結構間的程序及發佈潛在遠端服務之間的通訊。 它可以根據商業服務匯流排、 佇列、 共用的資料庫做為信箱，或任何其他分散式，並在理想情況下發送架構的傳訊系統。

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>網域事件中當做觸發副作用跨多個相同的網域中的彙總的慣用方法

如果執行命令相關的其中一個彙總的執行個體都需要額外的定義域規則執行一個或多個其他彙總，您應該設計並實作網域事件所觸發的副作用。 顯示在圖 9-14，以及其中一個最重要的使用案例，網域事件應該用來散佈在相同的網域模型中的多個彙總的狀態變更。

![](./media/image15.png)

**圖 9-14**。 若要強制執行相同的網域中的多個彙總之間的一致性定義域事件

在圖中，當使用者啟動的順序，OrderStarted 網域事件觸發程序建立買方物件在排序的微服務，根據原始使用者資訊識別微服務從 （與 CreateOrder 命令中提供的資訊）。 在第一次建立時，會產生順序彙總所網域事件。

或者，您可以讓彙總根訂閱以供其彙總 （子實體） 的成員所引發的事件。 比方說，每個 OrderItem 子實體可以引發事件，當項目價格高於特定容量，或產品項目數量太高。 彙總根可以接收這些事件並執行全域的計算或彙總。

請務必了解，此事件為基礎的通訊不會實作直接在彙總; 內您需要實作網域事件處理常式。 處理網域事件是應用程式考量。 網域模型層應該只著重於網域邏輯 — 網域專家瞭解的重點，不像處理常式，並使用儲存機制的副作用是持續性動作的應用程式基礎結構。 因此，應用程式層級是您應該在其中有網域網域事件引發時，觸發動作的事件處理常式。

網域事件也可用來觸發任何數目的應用程式的動作，並更重要的是，必須開啟才能解除解合的方式增加未來該數字。 比方說，當啟動順序時，您可以發佈網域事件傳播至其他彙總該資訊或甚至引發通知之類的應用程式動作。

重點是開啟的網域事件發生時要執行的動作數目。 最後，將會成長的動作和網域和應用程式中的規則。 複雜度或一些副作用動作發生情況時將會成長，但如果您的程式碼結合 「 黏附 」 (也就只具現化新的關鍵字在 C 中的物件\#)，則每當您需要加入新的動作，您必須變更原始的程式碼。 因為每個新的需求，您可能需要變更原始碼流程，這可能導致新的 bug。 這會針對[開啟/關閉原則](https://en.wikipedia.org/wiki/Open/closed_principle)從[實心](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))。 不僅如此，原始的協調作業的類別會成長，成長時，它會針對[單一責任原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)。

相反地，如果您使用網域事件時，您可以建立更細緻和低耦合實作將分別存放於責任使用這種方法：

1.  傳送命令 (例如，CreateOrder)。
2.  接收命令的命令處理常式中。
    -   執行的單一彙總的交易。
    -   （選擇性）引發網域副作用 (例如，OrderStartedDomainDvent) 事件。
1.  控制代碼網域 （在目前的處理序） 內的事件 thast 中多個彙總或應用程式動作，將執行副作用中開啟的數目。 例如: 
    -   請確認，或建立買方 」 和 「 付款方法。
    -   建立並傳送到事件匯流排散佈 microservices 或觸發程序外部的動作，例如傳送電子郵件給買方的狀態相關的整合事件。
    -   處理其他副作用。

所示圖 9-15，從相同的網域事件中，您可以處理多個網域或您要執行跨 microservices 與整合事件和事件匯流排連線的其他應用程式動作中的其他彙總相關的動作。

![](./media/image16.png)

**圖 9-15**。 處理每個網域的多個動作

事件處理常式通常是在應用程式層中，因為您將使用應用程式 API 等儲存機制的基礎結構物件的微服務的行為。 該意義而言，事件處理常式如下命令處理常式，因此兩者都是應用程式層的一部分。 重要的差異在於命令應該就可以一次處理。 網域事件可能是處理零或* n *逾時，因為如果可以由多個接收者或有不同的用途，每個處理常式的事件處理常式接收。

開啟數目的每個網域事件處理常式的可能性，可讓您新增許多更多的定義域規則，而不會影響您目前的程式碼。 比方說，實作下列的商務規則必須在發生事件之後，就可能發生權限可能是，只要加入幾個事件處理常式 （或甚至只是其中一個）：

當客戶購買的存放區中任何數目的訂單之間的總金額超過 $6000 時，10%折扣關閉套用於每個新的訂單，並通知未來訂單該折扣的相關電子郵件與客戶。

## <a name="implementing-domain-events"></a>實作定義域事件

在 C# 中，只需的網域事件是保存資料之結構或類別，例如 DTO，相關項目剛好在網域中，如下列範例所示的所有資訊：

```csharp
public class OrderStartedDomainEvent : IAsyncNotification
{
    public int CardTypeId { get; private set; }
    public string CardNumber { get; private set; }
    public string CardSecurityNumber { get; private set; }
    public string CardHolderName { get; private set; }
    public DateTime CardExpiration { get; private set; }
    public Order Order { get; private set; }

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

這是基本上保留 OrderStarted 事件相關的所有資料的類別。

根據網域的通用語言事件是發生在過去，因為事件的類別名稱應該表示成過去式時態動詞命令，例如 OrderStartedDomainEvent 或 OrderShippedDomainEvent。 這是網域事件中 eShopOnContainers 中順序的微服務的實作方式。

如我們所述，重要的特性的事件是因為事件是發生在過去，不應該變更的項目。 因此，它必須是不可變的類別。 您可以看到上述的屬性是唯讀狀態從外部物件的程式碼中。 更新物件的唯一方式是透過建構函式，當您建立事件物件。

### <a name="raising-domain-events"></a>引發定義域事件

下一個問題是如何引發網域事件，讓它達到其相關的事件處理常式。 您可以使用多個方法。

Udi Dahan 原本 (例如，在幾個相關的文章，例如[網域事件 – 採用 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) 使用靜態類別，用於管理和引發事件。 這可能包括名為 DomainEvents，就會引發網域事件立即時呼叫它時，使用類似下面的 DomainEvents.Raise (事件 myEvent) 語法的靜態類別。 Jimmy Bogard 所撰寫的部落格文章 ([加強您的網域： 定義域事件](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) 的建議有類似的方法。

不過，靜態網域事件類別時，它也會分派至處理常式立即。 這使得測試和偵錯更加困難，因為具有副作用邏輯的事件處理常式就會引發事件之後立即執行。 當您測試和偵錯時，您想要在焦點時，就為什麼在目前的彙總類別。您不想突然重新導向至其他的事件處理常式與其他彙總或應用程式邏輯相關的副作用。 這就是為什麼進化其他方法下, 一節中所述。

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>延後的方法，引發及分派事件

更好的方法是將網域事件加入至集合而不是立即分派給網域的事件處理常式，然後再分派這些網域事件*前*或*右* *之後*（如同在 EF SaveChanges) 認可交易。 (這種方法所述的 Jimmy Bogard 這篇文章[更好的網域事件模式](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)。)

決定是否網域事件傳送右或向右之前認可交易之後是交易的很重要，因為它會決定是否將包含副作用包含做為相同或在不同的交易的一部分。 在後者的情況下，您需要跨多個彙總處理最終一致性。 本主題下一節中討論。

延後的方法是何種 eShopOnContainers 使用。 首先，您將事件加入至集合或每個實體的事件清單中實體的情況。 該清單應使用屬於的實體物件，或更好的是，您的基底實體類別，如下列範例所示：

```csharp
public abstract class Entity
{
    private List<IAsyncNotification> _domainEvents;

    public List<IAsyncNotification> DomainEvents => _domainEvents;

    public void AddDomainEvent(IAsyncNotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<IAsyncNotification>();
        _domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(IAsyncNotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

當您想要引發事件時，您只將它加入至事件的集合，以便放置在彙總實體方法中，下列程式碼所示：

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
    cardTypeId,
    cardNumber,
    cardSecurityNumber,
    cardHolderName,
    cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

請注意唯一 AddDomainEvent 方法正在進行的事情將事件加入至清單。 不會引發事件，以及尚未叫用事件處理常式。

您實際想要分派事件之後，當您認可資料庫交易。 如果您使用 Entity Framework Core，就表示您 EF DbContext，如下列程式碼所示的 SaveChanges 方法：

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<int> SaveEntitiesAsync()
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

使用此程式碼中，您分派至其各自的事件處理常式的實體事件。

整體結果是，您必須分開 （簡單新增到清單中，在記憶體中） 的網域事件的引發分派給事件處理常式。 此外，根據您使用何種發送器，以同步或非同步方式無法分派事件。

請注意交易界限進入重大這裡播放。 如果您的工作和交易的單位可以跨越多個彙總 （如同使用 EF 核心和關聯式資料庫時），這可以正常運作。 但是，如果交易無法跨越彙總，例如當您使用類似 Azure DocumentDB 的 NoSQL 資料庫您必須實作額外的步驟，以達到一致性。 這是另一個原因永續性無知之不通用。這取決於您使用的儲存系統。

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>單一交易上與最終一致性彙總的彙總

是否要執行跨與信賴憑證者最終一致性跨這些彙總的彙總的單一交易的問題是爭議一個。 許多 DDD 作者像 Eric Evans 和 Vaughn Vernon 主張規則的一筆交易 = 一個彙總，並因此主張最終一致性跨彙總。 例如，在他的書*Domain-Driven 設計*，Eric Evans 表示：

跨越彙總任何規則就不應該在任何時間都保持最新狀態。 事件處理、 批次的處理或其他的更新機制，透過其他相依性可以解決一些特定的時間內。 (pg。 128)

Vaughn Vernon 說明中的下列[有效彙總設計。第 II 部分︰ 進行彙總工作一起](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

因此，如果其中一個彙總的執行個體都需要額外的商務規則執行一個或多個彙總上執行命令，使用 [最終一致性\[...\]沒有可行的方式，可支援 DDD 模型中的最終一致性。 彙總的方法發行時間傳遞給一個或多個非同步訂閱者的網域事件。

這根據對照採用更細緻的交易，而不是跨越多個彙總或實體的交易。 作法是在第二個案例中，資料庫鎖定數目將會相當高的延展性需求的大型應用程式中。 採用高可擴充的應用程式需要具有多個彙總之間的即時交易一致性的事實會協助接受最終一致性的概念。 企業通常不需要不可部分完成的變更，它負責在任何情況下網域專家說出特定作業是否需要不可部分完成交易，或不。 如果作業一律需要多個彙總之間的不可部分完成交易，您可能會要求您彙總是否應該是較大，或設計不正確。

不過，其他開發人員和架構設計人員 Jimmy Bogard 像要橫跨數個彙總的單一交易，但只有當這些額外的彙總相關相同原始命令的副作用。 例如，在[更好的網域事件模式](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)，Bogard 表示：

一般而言，我想網域事件發生在相同的邏輯交易內，但不是一定相同範圍的乘冪，網域事件中的副作用\[...\]我們只認可我們交易之前，我們會分派至其個別的處理常式我們事件。

如果分派網域事件右邊*之前*認可原始交易，這是因為您想要在相同交易中包含這些事件產生的副作用。 例如，如果 EF DbContext SaveChanges 方法失敗，交易將會回復所有變更，包括任何相關的網域的事件處理常式所實作的副作用作業的結果。 這是因為 DbContext 生命範圍定義為預設 「 範圍限定。 」 因此，將 DbContext 物件共用跨多個具現化相同範圍或物件圖形內的儲存機制物件。 這會伴隨 HttpRequest 範圍，開發 Web 應用程式開發介面或 MVC 應用程式時。

事實上，這兩種方法 （「 單一不可部分完成交易 」 和 「 最終一致性 」） 可以是權限。 它其實取決於您的網域或商務需求和目標網域專家告訴您。 它也取決於您需要的服務如何擴充 （更細微的交易都有較不會影響資料庫鎖定方面）。 同時，取決於多少投資您願意，讓您的程式碼中，因為最終一致性需要更複雜的程式碼，以便在彙總的需要實作的補償動作，以及偵測可能不一致。 請考量您與原始的彙總之後，當發送事件認可變更，如果沒有問題和事件處理常式無法認可其副作用，您必須彙總之間的不一致。

可補償動作的方法是在其他資料庫資料表中儲存網域事件，以便它們可以是原始交易的一部分。 之後，您可能會有批次程序偵測到不一致，並藉由比較事件的目前狀態的彙總清單中執行的補償動作。 補償動作是主題的一個複雜將會需要從端，其中包括討論與商務使用者 」 和 「 網域專家的深入分析的一部分。

在任何情況下，您可以選擇您需要的方法。 初始延遲方法，但是 — 認可之前，引發事件，讓您使用單一交易 — 使用 EF 核心和關聯式資料庫時，是最簡單的方法。 它是您更輕鬆地實作和許多商業案例中有效。 它也是 eShopOnContainers 中順序的微服務中使用的方法。

不過，如何執行您實際分派至其各自的事件處理常式的事件嗎？ 什麼是\_暫留處理器物件，您在上述範例中，請參閱？ 具有要執行動作的技術和成品，您可以使用事件和其事件處理常式之間進行對應。

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>網域事件發送器： 從事件對應到事件處理常式

一旦您能夠分派或發行事件時，您需要某種類型的成品，讓每個相關的處理常式可以取得它，並根據該事件的處理程序的副作用，將發行事件。

其中一個方法是真正的傳訊系統或甚至事件匯流排，可能會根據服務匯流排，而不是記憶體中的事件。 不過，第一個案例中，實際傳訊有點大材小用處理網域事件，因為您只需要處理這些相同的程序內的事件 (也就是相同的網域和應用程式層中)。

將事件對應至多個事件處理常式的另一種方式是使用 IoC 容器中的型別註冊，讓您以動態方式可以推斷分派事件的位置。 換句話說，您需要知道需要取得的特定事件的事件處理常式。 圖 9 到 16 個顯示的簡單的方法。

![](./media/image17.png)

**圖 9 到 16 個**。 網域事件發送器使用 IoC

您可以建立所有的配管和方法實作自己的成品。 不過，您也可以使用可用的程式庫，例如[MediatR](https://github.com/jbogard/MediatR)，基本上它會使用您的 IoT 容器。 因此，您可以直接使用預先定義的介面和暫留處理器物件的發行/分派方法。

程式碼中，您必須先註冊事件處理常式型別在 IoC 容器中，如下列範例所示：

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement
        // IAsyncNotificationHandler<>) in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(
            typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
            .GetTypeInfo().Assembly)
            .Where(t => t.IsClosedTypeOf(typeof(IAsyncNotificationHandler<>)))
            .AsImplementedInterfaces();
        // Other registrations ...
    }
}
```

程式碼會先識別包含網域事件處理常式，找出保存任何處理常式的組件的組件 （使用 typeof(ValidateOrAddBuyerAggregateWhenXxxx)，但您也可以選擇任何其他事件處理常式來找出組件）。 因為所有的事件處理常式實作 IAsyncNotificationHandler 介面，然後只搜尋那些，程式碼類型和註冊事件處理常式。

### <a name="how-to-subscribe-to-domain-events"></a>如何訂閱定義域事件

當您使用 MediatR 時，每個事件處理常式必須使用提供 IAsyncNotificationHandler 介面的泛型參數的事件類型，您可以在下列程式碼中看到如下：

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

根據事件和事件處理常式，可視為訂用帳戶，之間的關聯性 MediatR 成品可以探索每個事件的所有事件處理常式，並觸發每個這些事件處理常式。

### <a name="how-to-handle-domain-events"></a>如何處理定義域事件

最後，此事件處理常式通常會實作會使用基礎結構的儲存機制，來取得所需的其他彙總，並執行副作用網域邏輯的應用程式層程式碼。 下列程式碼示範範例。

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
    : IAsyncNotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;
    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // Parameter validations
        //...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ?
            orderStartedEvent.CardTypeId : 1;
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
        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer) :
        _buyerRepository.Add(buyer);
        await _buyerRepository.UnitOfWork.SaveEntitiesAsync();
        // Logging code using buyerUpdated info, etc.
    }
}
```

此事件處理常式程式碼應用程式層程式碼，因此視為它會使用基礎結構儲存機制中，基礎結構保存層中下一節所說明。 事件處理常式也可以使用其他基礎結構元件。

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>可以產生整合事件發佈微服務界限以外的網域事件

最後，請務必提到，您有時可能會想要跨多個 microservices 傳播事件。 這即視為整合事件，並無法從任何特定網域的事件處理常式的事件匯流排透過已發佈。

## <a name="conclusions-on-domain-events"></a>結論定義域事件 

如所述，使用網域事件明確實作您的網域中的變更的副作用。 若要使用 DDD 術語，用於網域事件明確實作跨一個或多個彙總的副作用。 此外，取得更好的延展性和較不影響資料庫鎖定，使用相同的網域中的彙總之間的最終一致性。

#### <a name="additional-resources"></a>其他資源

-   **Greg Young。什麼是網域事件？** 
     [ *http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg。網域事件和最終一致性**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard：更好的網域事件模式**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon：有效彙總設計第 2 部分： 一起彙總工作進行**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_文章/Vernon\_2011\_2.pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard：加強您的網域： 定義域事件**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>*

-   **Tong Truong。網域事件模式範例**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)

-   **Udi Dahan。如何建立完整封裝網域模型**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **Udi Dahan。網域事件 – 採用 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **Udi Dahan。網域事件 – 拯救**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist。不發行網域事件，將其傳回 ！** 
     [ *https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesar de la Torre：網域事件 vs。DDD 和 microservices 架構中的整合事件**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[上一個](用戶端-側邊-validation.md) [下一步] (基礎結構-持續性-層-design.md)
