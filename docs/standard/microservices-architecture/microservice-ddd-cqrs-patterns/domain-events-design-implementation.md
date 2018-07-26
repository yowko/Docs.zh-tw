---
title: 領域事件： 設計和實作
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 領域事件、設計和實作
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 3daab93a97c57521ae6f16ea2498c3f36f30d795
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937123"
---
# <a name="domain-events-design-and-implementation"></a><span data-ttu-id="2fcb7-104">領域事件：設計和實作</span><span class="sxs-lookup"><span data-stu-id="2fcb7-104">Domain events: design and implementation</span></span>

<span data-ttu-id="2fcb7-105">使用領域事件可明確實作您領域中變更的副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-105">Use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="2fcb7-106">換句話說 (以 DDD 術語來說)，使用領域事件可在多個彙總之間明確實作副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-106">In other words, and using DDD terminology, use domain events to explicitly implement side effects across multiple aggregates.</span></span> <span data-ttu-id="2fcb7-107">為了提高延展性並降低資料庫鎖定的影響，您可以選擇在相同領域中的多個彙總之間使用最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-107">Optionally, for better scalability and less impact in database locks, use eventual consistency between aggregates within the same domain.</span></span>

## <a name="what-is-a-domain-event"></a><span data-ttu-id="2fcb7-108">什麼是領域事件？</span><span class="sxs-lookup"><span data-stu-id="2fcb7-108">What is a domain event?</span></span>

<span data-ttu-id="2fcb7-109">事件是指過去發生的某件事。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-109">An event is something that has happened in the past.</span></span> <span data-ttu-id="2fcb7-110">領域事件邏輯上是指特定領域中發生的某件事，也是您想要相同領域 (同處理序) 的其他部分注意並可能回應的某件事。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-110">A domain event is, logically, something that happened in a particular domain, and something you want other parts of the same domain (in-process) to be aware of and potentially react to.</span></span>

<span data-ttu-id="2fcb7-111">領域事件的一項重要優點是，領域中發生某件事之後的副作用可以明確 (而不是隱含) 表示。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-111">An important benefit of domain events is that side effects after something happened in a domain can be expressed explicitly instead of implicitly.</span></span> <span data-ttu-id="2fcb7-112">這些副作用必須一致，因此與商務工作相關的所有作業不是全部發生，就是完全不會發生。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-112">Those side effects must be consistent so either all the operations related to the business task happen, or none of them.</span></span> <span data-ttu-id="2fcb7-113">此外，領域事件可以改進相同領域中類別之間的關注點分離。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-113">In addition, domain events enable a better separation of concerns among classes within the same domain.</span></span>

<span data-ttu-id="2fcb7-114">例如，如果您只使用 Entity Framework 和實體或甚至是彙總，而且使用案例必須引發副作用，則這些副作用會在發生某件事之後，以結合程式碼中的隱含概念來實作。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-114">For example, if you're just using Entity Framework and entities or even aggregates, if there have to be side effects provoked by a use case, those will be implemented as an implicit concept in the coupled code after something happened.</span></span> <span data-ttu-id="2fcb7-115">但如果您只看到該程式碼，您可能不知道該程式碼 (副作用) 是主要作業的一部分或真的是副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-115">But, if you just see that code, you might not know if that code (the side effect) is part of the main operation or if it really is a side effect.</span></span> <span data-ttu-id="2fcb7-116">相反地，使用領域事件可讓概念明確並成為通用語言的一部分。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-116">On the other hand, using domain events makes the concept explicit and part of the ubiquitous language.</span></span> <span data-ttu-id="2fcb7-117">例如，在 eShopOnContainers 應用程式中，建立訂單不只與訂單相關，還會根據原始使用者來更新或建立購買者彙總，因為使用者必須下訂單才會成為購買者。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-117">For example, in the eShopOnContainers application, creating an order is not just about the order; it updates or creates a buyer aggregate based on the original user, because the user is not a buyer until there is an order in place.</span></span> <span data-ttu-id="2fcb7-118">如果您使用領域事件，您可以明確表示由領域專家所提供並以通用語言為基礎的領域規則。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-118">If you use domain events, you can explicitly express that domain rule based in the ubiquitous language provided by the domain experts.</span></span>

<span data-ttu-id="2fcb7-119">領域事件有點類似傳訊樣式事件，但有一個重要的差異。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-119">Domain events are somewhat similar to messaging-style events, with one important difference.</span></span> <span data-ttu-id="2fcb7-120">透過即時傳訊、訊息佇列、訊息代理程式或使用 AMPQ 的服務匯流排，訊息一律會以非同步方式傳送，並跨處理序與電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-120">With real messaging, message queuing, message brokers, or a service bus using AMPQ, a message is always sent asynchronously and communicated across processes and machines.</span></span> <span data-ttu-id="2fcb7-121">這有助於整合多個限定內容、微服務或甚至是不同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-121">This is useful for integrating multiple Bounded Contexts, microservices, or even different applications.</span></span> <span data-ttu-id="2fcb7-122">不過，使用領域事件時，您不只希望從目前正在執行的領域作業引發事件，也希望所有副作用都會出現在相同的領域中。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-122">However, with domain events, you want to raise an event from the domain operation you are currently running, but you want any side effects to occur within the same domain.</span></span>

<span data-ttu-id="2fcb7-123">領域事件及其副作用 (之後會觸發並由事件處理常式管理的動作) 應該幾乎會在相同領域 (通常是同處理序) 中立即發生。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-123">The domain events and their side effects (the actions triggered afterwards that are managed by event handlers) should occur almost immediately, usually in-process, and within the same domain.</span></span> <span data-ttu-id="2fcb7-124">因此，領域事件可以為同步或非同步。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-124">Thus, domain events could be synchronous or asynchronous.</span></span> <span data-ttu-id="2fcb7-125">不過，整合事件應該一律為非同步。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-125">Integration events, however, should always be asynchronous.</span></span>

## <a name="domain-events-versus-integration-events"></a><span data-ttu-id="2fcb7-126">領域事件與整合事件的比較</span><span class="sxs-lookup"><span data-stu-id="2fcb7-126">Domain events versus integration events</span></span>

<span data-ttu-id="2fcb7-127">語意上來說，領域事件與整合事件同義，兩者都會通知剛發生的某件事。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-127">Semantically, domain and integration events are the same thing: notifications about something that just happened.</span></span> <span data-ttu-id="2fcb7-128">不過，其實作必須不同。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-128">However, their implementation must be different.</span></span> <span data-ttu-id="2fcb7-129">領域事件是推送至領域事件發送器的訊息，可實作為以 IoC 容器或任何其他方法為基礎的記憶體內部中繼程序。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-129">Domain events are just messages pushed to a domain event dispatcher, which could be implemented as an in-memory mediator based on an IoC container or any other method.</span></span>

<span data-ttu-id="2fcb7-130">另一方面，整合事件的目的是將已認可的交易和更新傳播至其他子系統，不論是其他微服務、限定內容或甚至是外部應用程式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-130">On the other hand, the purpose of integration events is to propagate committed transactions and updates to additional subsystems, whether they are other microservices, Bounded Contexts or even external applications.</span></span> <span data-ttu-id="2fcb7-131">因此，只有在成功保存實體時才應該出現，因為在許多情況下，如果失敗，整個作業實際上永遠不會發生。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-131">Hence, they should occur only if the entity is successfully persisted, since in many scenarios if this fails, the entire operation effectively never happened.</span></span>

<span data-ttu-id="2fcb7-132">此外，如前所述，整合事件必須以多個微服務 (其他限定內容) 或甚至是外部系統/應用程式之間的非同步通訊為基礎。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-132">In addition, and as mentioned, integration events must be based on asynchronous communication between multiple microservices (other Bounded Contexts) or even external systems/applications.</span></span> <span data-ttu-id="2fcb7-133">因此，事件匯流排介面需要可在潛在遠端服務之間進行處理序間和分散式通訊的一些基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-133">Thus, the event bus interface needs some infrastructure that allows inter-process and distributed communication between potentially remote services.</span></span> <span data-ttu-id="2fcb7-134">它可以依據商業服務匯流排、佇列、用作信箱的共用資料庫，或任何其他分散式且最好為發送型傳訊系統。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-134">It can be based on a commercial service bus, queues, a shared database used as a mailbox, or any other distributed and ideally push based messaging system.</span></span>

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a><span data-ttu-id="2fcb7-135">領域事件是在相同領域中的多個彙總之間觸發副作用的慣用方法</span><span class="sxs-lookup"><span data-stu-id="2fcb7-135">Domain events as a preferred way to trigger side effects across multiple aggregates within the same domain</span></span>

<span data-ttu-id="2fcb7-136">如果執行與一個彙總執行個體相關的命令需要在一或多個額外的彙總上執行其他領域規則，您應該設計並實作領域事件所要觸發的這些副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-136">If executing a command related to one aggregate instance requires additional domain rules to be run on one or more additional aggregates, you should design and implement those side effects to be triggered by domain events.</span></span> <span data-ttu-id="2fcb7-137">如圖 9-14 所示 (這是其中一個最重要的使用案例)，您應該使用領域事件，在相同領域模型中的多個彙總之間傳播狀態變更。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-137">As shown in Figure 9-14, and as one of the most important use cases, a domain event should be used to propagate state changes across multiple aggregates within the same domain model.</span></span>

![](./media/image15.png)

<span data-ttu-id="2fcb7-138">**圖 9-14**：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-138">**Figure 9-14**.</span></span> <span data-ttu-id="2fcb7-139">要在相同領域中的多個彙總之間強制執行一致性的領域事件</span><span class="sxs-lookup"><span data-stu-id="2fcb7-139">Domain events to enforce consistency between multiple aggregates within the same domain</span></span>

<span data-ttu-id="2fcb7-140">在圖中，當使用者起始訂單時，根據識別微服務中的原始使用者資訊 (以及 CreateOrder 命令中所提供的資訊)，OrderStarted 領域事件會觸發在訂購微服務中建立「購買者」物件的程序。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-140">In the figure, when the user initiates an order, the OrderStarted domain event triggers creation of a Buyer object in the ordering microservice, based on the original user info from the identity microservice (with information provided in the CreateOrder command).</span></span> <span data-ttu-id="2fcb7-141">第一次建立訂單時，訂單彙總會產生領域事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-141">The domain event is generated by the order aggregate when it is created in the first place.</span></span>

<span data-ttu-id="2fcb7-142">或者，您可以讓彙總根訂閱其彙總成員 (子實體) 所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-142">Alternately, you can have the aggregate root subscribed for events raised by members of its aggregates (child entities).</span></span> <span data-ttu-id="2fcb7-143">例如，當項目價格高於特定金額或產品項目金額太高時，每個 OrderItem 子實體都會引發一個事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-143">For instance, each OrderItem child entity can raise an event when the item price is higher than a specific amount, or when the product item amount is too high.</span></span> <span data-ttu-id="2fcb7-144">然後，彙總根可接收這些事件，並執行全域計算或彙總。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-144">The aggregate root can then receive those events and perform a global calculation or aggregation.</span></span>

<span data-ttu-id="2fcb7-145">請務必了解，此事件架構通訊不會直接在彙總內實作；您必須實作領域事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-145">It is important to understand that this event-based communication is not implemented directly within the aggregates; you need to implement domain event handlers.</span></span> <span data-ttu-id="2fcb7-146">處理領域事件是應用程式考量。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-146">Handling the domain events is an application concern.</span></span> <span data-ttu-id="2fcb7-147">領域模型層應該只著重於領域邏輯 (也就是領域專家了解的內容)，而不是應用程式基礎結構 (例如處理常式及使用儲存機制的副作用持續性動作)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-147">The domain model layer should only focus on the domain logic—things that a domain expert would understand, not application infrastructure like handlers and side-effect persistence actions using repositories.</span></span> <span data-ttu-id="2fcb7-148">因此，應用程式層是引發領域事件時，您應該讓領域事件處理常式觸發動作的位置。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-148">Therefore, the application layer level is where you should have domain event handlers triggering actions when a domain event is raised.</span></span>

<span data-ttu-id="2fcb7-149">領域事件也可用來觸發任何數目的應用程式動作，而且更重要的是，必須沒有限制才能在未來以低耦合方式增加數目。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-149">Domain events can also be used to trigger any number of application actions, and what is more important, must be open to increase that number in the future in a decoupled way.</span></span> <span data-ttu-id="2fcb7-150">例如，啟動訂單時，您可能想要發行領域事件，將該資訊傳播至其他彙總，或甚至是引發通知等應用程式動作。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-150">For instance, when the order is started, you might want to publish a domain event to propagate that info to other aggregates or even to raise application actions like notifications.</span></span>

<span data-ttu-id="2fcb7-151">重點是不要限制領域事件出現時所要執行的動作數目。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-151">The key point is the open number of actions to be executed when a domain event occurs.</span></span> <span data-ttu-id="2fcb7-152">領域和應用程式中的動作和規則最終都會成長。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-152">Eventually, the actions and rules in the domain and application will grow.</span></span> <span data-ttu-id="2fcb7-153">發生某件事時的副作用動作複雜度或數目會成長，但如果您的程式碼與 “glue” 結合 (亦即只使用 C\# 中的新關鍵字具現化物件)，則每次您需要新增動作時，都需要變更原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-153">The complexity or number of side-effect actions when something happens will grow, but if your code were coupled with “glue” (that is, just instantiating objects with the new keyword in C\#), then every time you needed to add a new action you would need to change the original code.</span></span> <span data-ttu-id="2fcb7-154">這可能會導致新的錯誤 (bug)，因為每個新的需求都需要您變更原始程式碼流程。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-154">This could result in new bugs, because with each new requirement you would need to change the original code flow.</span></span> <span data-ttu-id="2fcb7-155">這違背 [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) 的[開閉原則](https://en.wikipedia.org/wiki/Open/closed_principle)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-155">This goes against the [Open/Closed principle](https://en.wikipedia.org/wiki/Open/closed_principle) from [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)).</span></span> <span data-ttu-id="2fcb7-156">不僅如此，協調作業的原始類別會不斷成長，這違背[單一功能原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-156">Not only that, the original class that was orchestrating the operations would grow and grow, which goes against the [Single Responsibility Principle (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).</span></span>

<span data-ttu-id="2fcb7-157">相反地，如果您使用領域事件，就可以透過此方法分離職責，來建立更細緻且低耦合的實作：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-157">On the other hand, if you use domain events, you can create a fine-grained and decoupled implementation by segregating responsibilities using this approach:</span></span>

1.  <span data-ttu-id="2fcb7-158">傳送命令 (例如 CreateOrder)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-158">Send a command (for example, CreateOrder).</span></span>
2.  <span data-ttu-id="2fcb7-159">接收命令處理常式中的命令。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-159">Receive the command in a command handler.</span></span>
    -   <span data-ttu-id="2fcb7-160">執行單一彙總的交易。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-160">Execute a single aggregate’s transaction.</span></span>
    -   <span data-ttu-id="2fcb7-161">(選擇性) 引發副作用的領域事件 (例如 OrderStartedDomainEvent)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-161">(Optional) Raise domain events for side effects (for example, OrderStartedDomainEvent).</span></span>
1.  <span data-ttu-id="2fcb7-162">處理領域事件 (在目前的處理序中)，這些事件會在多個彙總或應用程式動作中執行不限數目的副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-162">Handle domain events (within the current process) that will execute an open number of side effects in multiple aggregates or application actions.</span></span> <span data-ttu-id="2fcb7-163">例如: </span><span class="sxs-lookup"><span data-stu-id="2fcb7-163">For example:</span></span>
    -   <span data-ttu-id="2fcb7-164">確認或建立購買者和付款方式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-164">Verify or create buyer and payment method.</span></span>
    -   <span data-ttu-id="2fcb7-165">建立相關的整合事件並傳送至事件匯流排，以在微服務之間傳播狀態，或觸發外部動作，例如將電子郵件傳送給購買者。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-165">Create and send a related integration event to the event bus to propagate states across microservices or trigger external actions like sending an email to the buyer.</span></span>
    -   <span data-ttu-id="2fcb7-166">處理其他副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-166">Handle other side effects.</span></span>

<span data-ttu-id="2fcb7-167">如圖 9-15 所示，從同一個領域事件開始，您可以處理與領域中其他彙總相關的多個動作，或您需要在連接至整合事件和事件匯流排的微服務之間執行的其他應用程式動作。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-167">As shown in Figure 9-15, starting from the same domain event, you can handle multiple actions related to other aggregates in the domain or additional application actions you need to perform across microservices connecting with integration events and the event bus.</span></span>

![](./media/image16.png)

<span data-ttu-id="2fcb7-168">**圖 9-15**：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-168">**Figure 9-15**.</span></span> <span data-ttu-id="2fcb7-169">處理每個領域的多個動作</span><span class="sxs-lookup"><span data-stu-id="2fcb7-169">Handling multiple actions per domain</span></span>

<span data-ttu-id="2fcb7-170">事件處理常式通常是在應用程式層中，因為您會針對微服務的行為使用儲存機制或應用程式 API 等基礎結構物件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-170">The event handlers are typically in the application layer, because you will use infrastructure objects like repositories or an application API for the microservice’s behavior.</span></span> <span data-ttu-id="2fcb7-171">就這點而言，事件處理常式類似命令處理常式，因此兩者都屬於應用程式層。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-171">In that sense, event handlers are similar to command handlers, so both are part of the application layer.</span></span> <span data-ttu-id="2fcb7-172">重要的差異在於命令只能處理一次。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-172">The important difference is that a command should be processed just once.</span></span> <span data-ttu-id="2fcb7-173">因為可能有多個接收者或事件處理常式 (每個處理常式的目的不同) 接收領域事件，所以領域事件可能處理零至 *n* 次。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-173">A domain event could be processed zero or *n* times, because it can be received by multiple receivers or event handlers with a different purpose for each handler.</span></span>

<span data-ttu-id="2fcb7-174">每個領域事件之處理常式數目不限的可能性，讓您可以新增更多領域規則，而不影響您目前的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-174">The possibility of an open number of handlers per domain event allows you to add many more domain rules without impacting your current code.</span></span> <span data-ttu-id="2fcb7-175">例如，實作以下必須在事件之後立即發生的商務規則，可能與新增幾個事件處理常式 (或甚至只有一個) 一樣容易：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-175">For instance, implementing the following business rule that has to happen right after an event might be as easy as adding a few event handlers (or even just one):</span></span>

<span data-ttu-id="2fcb7-176">當顧客在商店購買任意數目的訂單總金額超過 6000 USD 時，會對每個新的訂單套用 10% 的折扣，並以電子郵件通知顧客未來訂單的折扣。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-176">When the total amount purchased by a customer in the store, across any number of orders, exceeds $6,000, apply a 10% off discount to every new order and notify the customer with an email about that discount for future orders.</span></span>

## <a name="implementing-domain-events"></a><span data-ttu-id="2fcb7-177">實作領域事件</span><span class="sxs-lookup"><span data-stu-id="2fcb7-177">Implementing domain events</span></span>

<span data-ttu-id="2fcb7-178">在 C# 中，領域事件單純是資料保留結構或類別 (例如 DTO)，其中包含與領域中剛發生的事件相關的所有資訊，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-178">In C#, a domain event is simply a data-holding structure or class, like a DTO, with all the information related to what just happened in the domain, as shown in the following example:</span></span>

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

<span data-ttu-id="2fcb7-179">這基本上是保留與 OrderStarted 事件相關之所有資料的類別。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-179">This is essentially a class that holds all the data related to the OrderStarted event.</span></span>

<span data-ttu-id="2fcb7-180">根據領域的通用語言，由於事件是過去發生的某件事，因此事件的類別名稱應該以過去式動詞來表示，例如 OrderStartedDomainEvent 或 OrderShippedDomainEvent。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-180">In terms of the ubiquitous language of the domain, since an event is something that happened in the past, the class name of the event should be represented as a past-tense verb, like OrderStartedDomainEvent or OrderShippedDomainEvent.</span></span> <span data-ttu-id="2fcb7-181">這是在 eShopOnContainers 的訂購微服務中實作領域事件的方式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-181">That is how the domain event is implemented in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="2fcb7-182">如稍早所述，事件的一個重要特性是，由於事件是過去發生的某件事，不應該變更。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-182">As noted earlier, an important characteristic of events is that since an event is something that happened in the past, it should not change.</span></span> <span data-ttu-id="2fcb7-183">因此，它必須是不可變的類別。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-183">Therefore it must be an immutable class.</span></span> <span data-ttu-id="2fcb7-184">如您在上一個程式碼中所見，屬性在物件外部是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-184">You can see in the previous code that the properties are read-only from outside of the object.</span></span> <span data-ttu-id="2fcb7-185">當您建立事件物件時，更新物件的唯一方式是透過建構函式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-185">The only way to update the object is through the constructor when you create the event object.</span></span>

### <a name="raising-domain-events"></a><span data-ttu-id="2fcb7-186">引發領域事件</span><span class="sxs-lookup"><span data-stu-id="2fcb7-186">Raising domain events</span></span>

<span data-ttu-id="2fcb7-187">下一個問題是如何引發領域事件，使它抵達其相關的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-187">The next question is how to raise a domain event so it reaches its related event handlers.</span></span> <span data-ttu-id="2fcb7-188">您可以使用多個方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-188">You can use multiple approaches.</span></span>

<span data-ttu-id="2fcb7-189">Udi Dahan 原本建議使用靜態類別來管理及引發事件 (如數篇相關的文章所示，例如 [Domain Events - Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/) (領域事件 - 續篇))。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-189">Udi Dahan originally proposed (for example, in several related posts, such as [Domain Events – Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) using a static class for managing and raising the events.</span></span> <span data-ttu-id="2fcb7-190">這可能包含名為 DomainEvents 的靜態類別，該類別會在呼叫時，使用 DomainEvents.Raise(Event myEvent) 等語法立即引發領域事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-190">This might include a static class named DomainEvents that would raise domain events immediately when it is called, using syntax like DomainEvents.Raise(Event myEvent).</span></span> <span data-ttu-id="2fcb7-191">Jimmy Bogard 所撰寫的部落格文章 ([Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/) (增強您的領域：領域事件)) 建議類似的方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-191">Jimmy Bogard wrote a blog post ([Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) that recommends a similar approach.</span></span>

<span data-ttu-id="2fcb7-192">不過，當領域事件類別為靜態時，它也會立即分派至處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-192">However, when the domain events class is static, it also dispatches to handlers immediately.</span></span> <span data-ttu-id="2fcb7-193">這會使得測試和偵錯更加困難，因為在引發事件之後會立即執行具有副作用邏輯的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-193">This makes testing and debugging more difficult, because the event handlers with side-effects logic are executed immediately after the event is raised.</span></span> <span data-ttu-id="2fcb7-194">當您進行測試和偵錯時，您只想要專注於目前彙總類別中正在發生的事件，而不想要因為與其他彙總或應用程式邏輯相關的副作用，而突然被重新導向至其他事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-194">When you are testing and debugging, you want to focus on and just what is happening in the current aggregate classes; you do not want to suddenly be redirected to other event handlers for side effects related to other aggregates or application logic.</span></span> <span data-ttu-id="2fcb7-195">這就是其他方法進化的原因，如下一節中所述。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-195">This is why other approaches have evolved, as explained in the next section.</span></span>

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a><span data-ttu-id="2fcb7-196">引發和分派事件的延後方法</span><span class="sxs-lookup"><span data-stu-id="2fcb7-196">The deferred approach for raising and dispatching events</span></span>

<span data-ttu-id="2fcb7-197">您最好將領域事件新增至集合，然後在認可交易 (如同 EF 中的 SaveChanges)「之前」或「之後」分派這些領域事件，而不是直接分派至領域事件處理常式</span><span class="sxs-lookup"><span data-stu-id="2fcb7-197">Instead of dispatching to a domain event handler immediately, a better approach is to add the domain events to a collection and then to dispatch those domain events *right before* or *right* *after* committing the transaction (as with SaveChanges in EF).</span></span> <span data-ttu-id="2fcb7-198">(Jimmy Bogard 在 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/) (更佳的領域事件模式) 的這篇文章中說明此方法)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-198">(This approach was described by Jimmy Bogard in this post [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)</span></span>

<span data-ttu-id="2fcb7-199">請務必決定在認可交易之前或之後傳送領域事件，因為這會決定您將副作用加入作為相同交易的一部分，還是加入不同的交易。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-199">Deciding if you send the domain events right before or right after committing the transaction is important, since it determines whether you will include the side effects as part of the same transaction or in different transactions.</span></span> <span data-ttu-id="2fcb7-200">在後者的情況下，您需要處理多個彙總之間的最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-200">In the latter case, you need to deal with eventual consistency across multiple aggregates.</span></span> <span data-ttu-id="2fcb7-201">下一節將討論這個主題。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-201">This topic is discussed in the next section.</span></span>

<span data-ttu-id="2fcb7-202">eShopOnContainers 使用延後方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-202">The deferred approach is what eShopOnContainers uses.</span></span> <span data-ttu-id="2fcb7-203">首先，您會將實體中正在發生的事件新增至每個實體的事件集合或清單。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-203">First, you add the events happening in your entities into a collection or list of events per entity.</span></span> <span data-ttu-id="2fcb7-204">該清單應該是實體物件的一部分，最好是基底實體類別的一部分，如實體基底類別的下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-204">That list should be part of the entity object, or even better, part of your base entity class, as shown in the following example of the Entity base class:</span></span>

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

<span data-ttu-id="2fcb7-205">當您想要引發事件時，您只要從彙總根實體之任何方法的程式碼將它新增至事件集合。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-205">When you want to raise an event, you just add it to the event collection from code at any method of the aggregate-root entity.</span></span>

<span data-ttu-id="2fcb7-206">下列程式碼 (屬於 [eShopOnContainers 的 Order aggregate-root](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)) 顯示一個範例：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-206">The following code, part of the [Order aggregate-root at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), shows an example:</span></span>

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

<span data-ttu-id="2fcb7-207">請注意，AddDomainEvent 方法只會將事件新增至清單。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-207">Notice that the only thing that the AddDomainEvent method is doing is adding an event to the list.</span></span> <span data-ttu-id="2fcb7-208">尚未分派任何事件，而且尚未叫用任何事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-208">No event is dispatched yet, and no event handler is invoked yet.</span></span>

<span data-ttu-id="2fcb7-209">您實際上想要稍後在將交易認可至資料庫時分派事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-209">You actually want to dispatch the events later on, when you commit the transaction to the database.</span></span> <span data-ttu-id="2fcb7-210">如果您使用 Entity Framework Core，也就是在 EF DbContext 的 SaveChanges 方法中 (如下列程式碼所示)：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-210">If you are using Entity Framework Core, that means in the SaveChanges method of your EF DbContext, as in the following code:</span></span>

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

<span data-ttu-id="2fcb7-211">在此程式碼中，您會將實體事件分派至其各自的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-211">With this code, you dispatch the entity events to their respective event handlers.</span></span>

<span data-ttu-id="2fcb7-212">整體結果是您將引發領域事件 (記憶體內部清單中的一個簡單新增)，與將它分派至事件處理常式的職責分離。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-212">The overall result is that you have decoupled the raising of a domain event (a simple add into a list in memory) from dispatching it to an event handler.</span></span> <span data-ttu-id="2fcb7-213">此外，根據您使用的發送器類型，您可以利用同步或非同步方式來分派事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-213">In addition, depending on what kind of dispatcher you are using, you could dispatch the events synchronously or asynchronously.</span></span>

<span data-ttu-id="2fcb7-214">請注意，交易界限在此扮演重要的角色。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-214">Be aware that transactional boundaries come into significant play here.</span></span> <span data-ttu-id="2fcb7-215">如果您的工作單位和交易可跨多個彙總 (如同使用 EF Core 和關聯式資料庫時)，則會正常運作。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-215">If your unit of work and transaction can span more than one aggregate (as when using EF Core and a relational database), this can work well.</span></span> <span data-ttu-id="2fcb7-216">但如果交易不可跨多個彙總 (例如當您使用 Azure DocumentDB 等 NoSQL 資料庫時)，您必須實作額外的步驟，才能達到一致性。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-216">But if the transaction cannot span aggregates, such as when you are using a NoSQL database like Azure DocumentDB, you have to implement additional steps to achieve consistency.</span></span> <span data-ttu-id="2fcb7-217">這是永續性無知不通用的另一個原因，它需要您使用的儲存體系統。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-217">This is another reason why persistence ignorance is not universal; it depends on the storage system you use.</span></span>

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a><span data-ttu-id="2fcb7-218">跨彙總的單一交易與跨彙總的最終一致性之比較</span><span class="sxs-lookup"><span data-stu-id="2fcb7-218">Single transaction across aggregates versus eventual consistency across aggregates</span></span>

<span data-ttu-id="2fcb7-219">要在多個彙總之間執行單一交易，還是要依賴這些彙總之間的最終一致性，是具爭議性的問題。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-219">The question of whether to perform a single transaction across aggregates versus relying on eventual consistency across those aggregates is a controversial one.</span></span> <span data-ttu-id="2fcb7-220">許多 DDD 作者 (像是 Eric Evans 和 Vaughn Vernon) 提倡一個交易等於一個彙總的規則，因此支持在多個彙總之間取得最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-220">Many DDD authors like Eric Evans and Vaughn Vernon advocate the rule that one transaction = one aggregate and therefore argue for eventual consistency across aggregates.</span></span> <span data-ttu-id="2fcb7-221">例如，Eric Evans 在 *Domain-Driven Design* 一書中表示：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-221">For example, in his book *Domain-Driven Design*, Eric Evans says this:</span></span>

<span data-ttu-id="2fcb7-222">任何跨彙總的規則不必總是處於最新狀態。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-222">Any rule that spans Aggregates will not be expected to be up-to-date at all times.</span></span> <span data-ttu-id="2fcb7-223">透過事件處理、批次處理或其他更新機制，即可解析一段特定時間內的其他相依性</span><span class="sxs-lookup"><span data-stu-id="2fcb7-223">Through event processing, batch processing, or other update mechanisms, other dependencies can be resolved within some specific time.</span></span> <span data-ttu-id="2fcb7-224">(第 128 頁)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-224">(page 128)</span></span>

<span data-ttu-id="2fcb7-225">Vaughn Vernon 在 [Effective Aggregate DesignPart II: Making Aggregates Work Together](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf) (有效彙總設計第二部分：讓彙總搭配運作) 中表示：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-225">Vaughn Vernon says the following in [Effective Aggregate Design. Part II: Making Aggregates Work Together](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):</span></span>

<span data-ttu-id="2fcb7-226">因此，如果在一個彙總執行個體上執行命令需要在一或多個彙總上執行其他商務規則，請使用最終一致性 \[...\]沒有支援 DDD 模型中最終一致性的可行方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-226">Thus, if executing a command on one aggregate instance requires that additional business rules execute on one or more aggregates, use eventual consistency \[...\] There is a practical way to support eventual consistency in a DDD model.</span></span> <span data-ttu-id="2fcb7-227">彙總方法會發行領域事件，及時傳遞至一或多個非同步訂閱者。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-227">An aggregate method publishes a domain event that is in time delivered to one or more asynchronous subscribers.</span></span>

<span data-ttu-id="2fcb7-228">此原理是以更細緻的交易為基礎，而不是以跨許多彙總或實體的交易為基礎。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-228">This rationale is based on embracing fine-grained transactions instead of transactions spanning many aggregates or entities.</span></span> <span data-ttu-id="2fcb7-229">其概念是在第二個案例中，資料庫鎖定數目在具有高延展性需求的大型應用程式中會很大。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-229">The idea is that in the second case, the number of database locks will be substantial in large-scale applications with high scalability needs.</span></span> <span data-ttu-id="2fcb7-230">可高度擴充的應用程式不需要在多個彙總之間有立即交易一致性，認清這點事實有助於接受最終一致性概念。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-230">Embracing the fact that high-scalable applications need not have instant transactional consistency between multiple aggregates helps with accepting the concept of eventual consistency.</span></span> <span data-ttu-id="2fcb7-231">企業通常不需要不可部分完成變更，而且在任何情況下，領域專家都有責任指出特定作業是否需要不可部分完成交易。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-231">Atomic changes are often not needed by the business, and it is in any case the responsibility of the domain experts to say whether particular operations need atomic transactions or not.</span></span> <span data-ttu-id="2fcb7-232">如果作業一律需要在多個彙總之間有不可部分完成交易，您可能會詢問彙總是否應該更大或設計是否不正確。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-232">If an operation always needs an atomic transaction between multiple aggregates, you might ask whether your aggregate should be larger or was not correctly designed.</span></span>

<span data-ttu-id="2fcb7-233">不過，其他開發人員以及像是 Jimmy Bogard 的架構設計人員接受單一交易橫跨數個彙總，但僅限於這些額外的彙總與相同原始命令的副作用相關時。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-233">However, other developers and architects like Jimmy Bogard are okay with spanning a single transaction across several aggregates—but only when those additional aggregates are related to side effects for the same original command.</span></span> <span data-ttu-id="2fcb7-234">例如，Bogard 在 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/) (更佳的領域事件模式) 中表示：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-234">For instance, in [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard says this:</span></span>

<span data-ttu-id="2fcb7-235">一般而言，我希望領域事件的副作用出現在相同的邏輯交易內，但不一定要在引發領域事件的相同範圍內 \[...\]在我們認可交易之前，我們會將事件分派至其各自的處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-235">Typically, I want the side effects of a domain event to occur within the same logical transaction, but not necessarily in the same scope of raising the domain event \[...\] Just before we commit our transaction, we dispatch our events to their respective handlers.</span></span>

<span data-ttu-id="2fcb7-236">如果您在認可原始交易「之前」分派領域事件，這是因為您想要將這些事件的副作用包含在相同的交易中。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-236">If you dispatch the domain events right *before* committing the original transaction, it is because you want the side effects of those events to be included in the same transaction.</span></span> <span data-ttu-id="2fcb7-237">例如，如果 EF DbContext SaveChanges 方法失敗，交易將會復原所有變更，包括相關領域事件處理常式所實作之任何副作用作業的結果。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-237">For example, if the EF DbContext SaveChanges method fails, the transaction will roll back all changes, including the result of any side effect operations implemented by the related domain event handlers.</span></span> <span data-ttu-id="2fcb7-238">這是因為 DbContext 存留期範圍預設會定義為 "scoped"。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-238">This is because the DbContext life scope is by default defined as "scoped."</span></span> <span data-ttu-id="2fcb7-239">因此，DbContext 物件會在相同範圍或物件圖形內要具現化的多個儲存機制物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-239">Therefore, the DbContext object is shared across multiple repository objects being instantiated within the same scope or object graph.</span></span> <span data-ttu-id="2fcb7-240">開發 Web API 或 MVC 應用程式時，這會與 HttpRequest 範圍一致。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-240">This coincides with the HttpRequest scope when developing Web API or MVC apps.</span></span>

<span data-ttu-id="2fcb7-241">事實上，這兩種方法 (單一不可部分完成交易和最終一致性) 都正確。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-241">In reality, both approaches (single atomic transaction and eventual consistency) can be right.</span></span> <span data-ttu-id="2fcb7-242">它其實取決於您的領域或商務需求，以及領域專家給您的建議。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-242">It really depends on your domain or business requirements and what the domain experts tell you.</span></span> <span data-ttu-id="2fcb7-243">它也取決於您需要的服務延展性 (交易越細緻，對資料庫鎖定的影響越低)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-243">It also depends on how scalable you need the service to be (more granular transactions have less impact with regard to database locks).</span></span> <span data-ttu-id="2fcb7-244">此外，它取決您願意對程式碼的投資，因為最終一致性需要更複雜的程式碼，才能偵測彙總之間可能不一致性的情況，並需要實作補償動作。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-244">And it depends on how much investment you are willing to make in your code, since eventual consistency requires more complex code in order to detect possible inconsistencies across aggregates and the need to implement compensatory actions.</span></span> <span data-ttu-id="2fcb7-245">請考慮下列情況，如果您將變更認可至原始彙總，之後當分派事件時發生問題，而且事件處理常式無法認可其副作用，則彙總之間會有不一致的情況。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-245">Take into account that if you commit changes to the original aggregate and afterwards, when the events are being dispatched, there is an issue and the event handlers cannot commit their side effects, you will have inconsistencies between aggregates.</span></span>

<span data-ttu-id="2fcb7-246">一個允許補償動作的方法是將領域事件儲存在其他資料庫資料表中，讓它們可以成為原始交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-246">A way to allow compensatory actions would be to store the domain events in additional database tables so they can be part of the original transaction.</span></span> <span data-ttu-id="2fcb7-247">之後，您可以有一個批次程序，藉由比較事件清單與彙總的目前狀態，來偵測不一致性的情況並執行補償動作。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-247">Afterwards, you could have a batch process that detects inconsistencies and runs compensatory actions by comparing the list of events with the current state of the aggregates.</span></span> <span data-ttu-id="2fcb7-248">補償動作屬於複雜主題，需要您深入分析，包括與企業用戶以及領域專家進行討論。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-248">The compensatory actions are part of a complex topic that will require deep analysis from your side, which includes discussing it with the business user and domain experts.</span></span>

<span data-ttu-id="2fcb7-249">在任何情況下，您都可以選擇所需的方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-249">In any case, you can choose the approach you need.</span></span> <span data-ttu-id="2fcb7-250">但初始延後方法 (在認可前引發事件以便您使用單一交易) 是使用 EF Core 和關聯式資料庫時的最簡單方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-250">But the initial deferred approach—raising the events before committing, so you use a single transaction—is the simplest approach when using EF Core and a relational database.</span></span> <span data-ttu-id="2fcb7-251">實作起來更容易，而且在許多商務案例中很有效。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-251">It is easier to implement and valid in many business cases.</span></span> <span data-ttu-id="2fcb7-252">這也是 eShopOnContainers 中的訂購微服務所使用的方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-252">It is also the approach used in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="2fcb7-253">但您實際上如何將這些事件分派至其各自的事件處理常式？</span><span class="sxs-lookup"><span data-stu-id="2fcb7-253">But how do you actually dispatch those events to their respective event handlers?</span></span> <span data-ttu-id="2fcb7-254">您在上一個範例中看到的 \_mediator 物件是什麼？</span><span class="sxs-lookup"><span data-stu-id="2fcb7-254">What is the \_mediator object that you see in the previous example?</span></span> <span data-ttu-id="2fcb7-255">這與您可以用來對應事件與其事件處理常式的技術和成品有關。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-255">That has to do with the techniques and artifacts you can use to map between events and their event handlers.</span></span>

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a><span data-ttu-id="2fcb7-256">領域事件發送器：事件與事件處理常式的對應</span><span class="sxs-lookup"><span data-stu-id="2fcb7-256">The domain event dispatcher: mapping from events to event handlers</span></span>

<span data-ttu-id="2fcb7-257">一旦您可以分派或發行事件，您需要某種會發行事件的成品，讓每個相關的處理常式可以取得它，並根據該事件來處理副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-257">Once you're able to dispatch or publish the events, you need some kind of artifact that will publish the event, so that every related handler can get it and process side effects based on that event.</span></span>

<span data-ttu-id="2fcb7-258">一個方法是即時傳訊系統或甚至事件匯流排，可能會根據服務匯流排，而不是記憶體內部事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-258">One approach is a real messaging system or even an event bus, possibly based on a service bus as opposed to in-memory events.</span></span> <span data-ttu-id="2fcb7-259">不過，在第一個案例中，即時傳訊對處理領域事件會過當，因為您只需要處理相同處理序 (也就是相同領域和應用程式層) 中的這些事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-259">However, for the first case, real messaging would be overkill for processing domain events, since you just need to process those events within the same process (that is, within the same domain and application layer).</span></span>

<span data-ttu-id="2fcb7-260">另一個方法是藉由在 IoC 容器中使用類型登錄，將事件對應至多個事件處理常式，讓您可以動態推斷分派事件的目的地。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-260">Another way to map events to multiple event handlers is by using types registration in an IoC container so that you can dynamically infer where to dispatch the events.</span></span> <span data-ttu-id="2fcb7-261">換句話說，您需要知道需要取得特定事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-261">In other words, you need to know what event handlers need to get a specific event.</span></span> <span data-ttu-id="2fcb7-262">圖 9-16 顯示經過簡化的方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-262">Figure 9-16 shows a simplified approach for that.</span></span>

![](./media/image17.png)

<span data-ttu-id="2fcb7-263">**圖 9-16**：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-263">**Figure 9-16**.</span></span> <span data-ttu-id="2fcb7-264">使用 IoC 的領域事件發送器</span><span class="sxs-lookup"><span data-stu-id="2fcb7-264">Domain event dispatcher using IoC</span></span>

<span data-ttu-id="2fcb7-265">您可以建立所有連接和成品，自行實作該方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-265">You can build all the plumbing and artifacts to implement that approach by yourself.</span></span> <span data-ttu-id="2fcb7-266">不過，您也可以使用 [MediatR](https://github.com/jbogard/MediatR) 等可用的程式庫，這些程式庫基本上會使用您的 IoC 容器。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-266">However, you can also use available libraries like [MediatR](https://github.com/jbogard/MediatR), which underneath the covers uses your IoC container.</span></span> <span data-ttu-id="2fcb7-267">因此，您可以直接使用預先定義的介面和中繼程序物件的發行/分派方法。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-267">You can therefore directly use the predefined interfaces and the mediator object’s publish/dispatch methods.</span></span>

<span data-ttu-id="2fcb7-268">在程式碼中，您必須先在 IoC 容器中登錄事件處理常式類型，如 [eShopOnContainers 訂購微服務](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)的下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-268">In code, you first need to register the event handler types in your IoC container, as shown in the following example at [eShopOnContainers Ordering microservice](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):</span></span>

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

<span data-ttu-id="2fcb7-269">此程式碼會先尋找保留任何處理常式的組件，以識別包含領域事件處理常式的組件 (使用 typeof(ValidateOrAddBuyerAggregateWhenXxxx)，但您可以選擇任何其他事件處理常式來尋找組件)。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-269">The code first identifies the assembly that contains the domain event handlers by locating the assembly that holds any of the handlers (using typeof(ValidateOrAddBuyerAggregateWhenXxxx), but you could have chosen any other event handler to locate the assembly).</span></span> <span data-ttu-id="2fcb7-270">由於所有事件處理常式都會實作 IAsyncNotificationHandler 介面，因此程式碼會接著直接搜尋這些類型並登錄所有事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-270">Since all the event handlers implement the IAsyncNotificationHandler interface, the code then just searches for those types and registers all the event handlers.</span></span>

### <a name="how-to-subscribe-to-domain-events"></a><span data-ttu-id="2fcb7-271">如何訂閱領域事件</span><span class="sxs-lookup"><span data-stu-id="2fcb7-271">How to subscribe to domain events</span></span>

<span data-ttu-id="2fcb7-272">當您使用 MediatR 時，每個事件處理常式必須使用 INotificationHandler 介面的泛型參數所提供的事件類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="2fcb7-272">When you use MediatR, each event handler must use an event type that is provided on the generic parameter of the INotificationHandler interface, as you can see in the following code:</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

<span data-ttu-id="2fcb7-273">根據事件與事件處理常式之間的關聯性 (可視為訂閱)，MediatR 成品可探索每個事件的所有事件處理常式，並觸發每個事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-273">Based on the relationship between event and event handler, which can be considered the subscription, the MediatR artifact can discover all the event handlers for each event and trigger each of those event handlers.</span></span>

### <a name="how-to-handle-domain-events"></a><span data-ttu-id="2fcb7-274">如何處理領域事件</span><span class="sxs-lookup"><span data-stu-id="2fcb7-274">How to handle domain events</span></span>

<span data-ttu-id="2fcb7-275">最後，事件處理常式通常會實作應用程式層程式碼，該程式碼使用基礎結構儲存機制來取得所需的額外彙總，並執行副作用領域邏輯。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-275">Finally, the event handler usually implements application layer code that uses infrastructure repositories to obtain the required additional aggregates and to execute side-effect domain logic.</span></span> <span data-ttu-id="2fcb7-276">下列 [eShopOnContainers 領域事件處理常式程式碼](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)顯示一個實作範例。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-276">The following [domain event handler code at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), shows an implementation example.</span></span>

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

<span data-ttu-id="2fcb7-277">上述領域事件處理常式程式碼會視為應用程式層程式碼，因此它使用基礎結構儲存機制，如下一節的基礎結構持續性層中所述。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-277">The previous domain event handler code is considered application layer code because it uses infrastructure repositories, as explained in the next section on the infrastructure-persistence layer.</span></span> <span data-ttu-id="2fcb7-278">事件處理常式也可以使用其他基礎結構元件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-278">Event handlers could also use other infrastructure components.</span></span>

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a><span data-ttu-id="2fcb7-279">領域事件可以產生要在微服務界限以外發行的整合事件</span><span class="sxs-lookup"><span data-stu-id="2fcb7-279">Domain events can generate integration events to be published outside of the microservice boundaries</span></span>

<span data-ttu-id="2fcb7-280">最後值得一提的是，您有時可能會想要在多個微服務之間傳播事件。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-280">Finally, it is important to mention that you might sometimes want to propagate events across multiple microservices.</span></span> <span data-ttu-id="2fcb7-281">這會視為整合事件，而且可透過事件匯流排從特定領域事件處理常式發行。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-281">That is considered an integration event, and it could be published through an event bus from any specific domain event handler.</span></span>

## <a name="conclusions-on-domain-events"></a><span data-ttu-id="2fcb7-282">領域事件結論</span><span class="sxs-lookup"><span data-stu-id="2fcb7-282">Conclusions on domain events</span></span>

<span data-ttu-id="2fcb7-283">如前所述，使用領域事件可明確實作您領域中變更的副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-283">As stated, use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="2fcb7-284">以 DDD 術語來說，使用領域事件可在一或多個彙總之間明確實作副作用。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-284">To use DDD terminology, use domain events to explicitly implement side effects across one or multiple aggregates.</span></span> <span data-ttu-id="2fcb7-285">此外，為了提高延展性並降低資料庫鎖定的影響，請在相同領域中的多個彙總之間使用最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2fcb7-285">Additionally, and for better scalability and less impact on database locks, use eventual consistency between aggregates within the same domain.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2fcb7-286">其他資源</span><span class="sxs-lookup"><span data-stu-id="2fcb7-286">Additional resources</span></span>

-   <span data-ttu-id="2fcb7-287">**Greg Young。什麼是領域事件？**
    [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-287">**Greg Young. What is a Domain Event?**
[*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span></span>

-   <span data-ttu-id="2fcb7-288">**Jan Stenberg：領域事件與最終一致性**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-288">**Jan Stenberg. Domain Events and Eventual Consistency**
[*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span></span>

-   <span data-ttu-id="2fcb7-289">**Jimmy Bogard：更佳的領域事件模式**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-289">**Jimmy Bogard. A better domain events pattern**
[*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span></span>

-   <span data-ttu-id="2fcb7-290">**Vaughn Vernon：Effective Aggregate Design Part II: Making Aggregates Work Together (有效彙總設計第二部分：使彙總共同作業)**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-290">**Vaughn Vernon. Effective Aggregate Design Part II: Making Aggregates Work Together**
[*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span></span>

-   <span data-ttu-id="2fcb7-291">**Jimmy Bogard：加強您的領域：領域事件**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *</span><span class="sxs-lookup"><span data-stu-id="2fcb7-291">**Jimmy Bogard. Strengthening your domain: Domain Events**
*<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *</span></span>

-   <span data-ttu-id="2fcb7-292">**Tony Truong：領域事件模式範例**
    [*https://www.tonytruong.net/domain-events-pattern-example/*](https://www.tonytruong.net/domain-events-pattern-example/)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-292">**Tony Truong. Domain Events Pattern Example**
[*https://www.tonytruong.net/domain-events-pattern-example/*](https://www.tonytruong.net/domain-events-pattern-example/)</span></span>

-   <span data-ttu-id="2fcb7-293">**Udi Dahan.如何建立完整封裝式領域模型**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-293">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>

-   <span data-ttu-id="2fcb7-294">**Udi Dahan.領域事件 - 第 2 步**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-294">**Udi Dahan. Domain Events – Take 2**
[*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span></span>

-   <span data-ttu-id="2fcb7-295">**Udi Dahan.領域事件 - 解答**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-295">**Udi Dahan. Domain Events – Salvation**
[*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span></span>

-   <span data-ttu-id="2fcb7-296">**Jan Kronquist：別發佈領域事件，傳回它們！**
    [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-296">**Jan Kronquist. Don't publish Domain Events, return them!**
[*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span></span>

-   <span data-ttu-id="2fcb7-297">**Cesar de la Torre：Domain Events vs.DDD 與微服務架構中的整合事件**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-297">**Cesar de la Torre. Domain Events vs. Integration Events in DDD and microservices architectures**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2fcb7-298">[上一頁](client-side-validation.md)
[下一頁](infrastructure-persistence-layer-design.md)</span><span class="sxs-lookup"><span data-stu-id="2fcb7-298">[Previous](client-side-validation.md)
[Next](infrastructure-persistence-layer-design.md)</span></span>
