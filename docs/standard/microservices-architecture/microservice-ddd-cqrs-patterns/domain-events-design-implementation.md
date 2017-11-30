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
# <a name="domain-events-design-and-implementation"></a><span data-ttu-id="2acce-105">網域事件： 設計和實作</span><span class="sxs-lookup"><span data-stu-id="2acce-105">Domain events: design and implementation</span></span>

<span data-ttu-id="2acce-106">使用網域事件來明確地實作您的網域中的變更的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-106">Use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="2acce-107">在其他字，和使用 DDD 術語中，使用網域事件以明確實作跨多個彙總的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-107">In other words, and using DDD terminology, use domain events to explicitly implement side effects across multiple aggregates.</span></span> <span data-ttu-id="2acce-108">（選擇性） 更好的延展性較資料庫鎖定的影響，請使用相同的網域中的彙總之間的最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2acce-108">Optionally, for better scalability and less impact in database locks, use eventual consistency between aggregates within the same domain.</span></span>

## <a name="what-is-a-domain-event"></a><span data-ttu-id="2acce-109">什麼是網域事件？</span><span class="sxs-lookup"><span data-stu-id="2acce-109">What is a domain event?</span></span>

<span data-ttu-id="2acce-110">事件是發生在過去的項目。</span><span class="sxs-lookup"><span data-stu-id="2acce-110">An event is something that has happened in the past.</span></span> <span data-ttu-id="2acce-111">網域事件以邏輯方式，是發生在特定網域的項目，項目您想要注意和可能反應的相同網域 （同處理序） 的其他部分。</span><span class="sxs-lookup"><span data-stu-id="2acce-111">A domain event is, logically, something that happened in a particular domain, and something you want other parts of the same domain (in-process) to be aware of and potentially react to.</span></span>

<span data-ttu-id="2acce-112">網域事件中的重要優點是之後在網域中發生問題的副作用可能會明確地以而不是以隱含方式。</span><span class="sxs-lookup"><span data-stu-id="2acce-112">An important benefit of domain events is that side effects after something happened in a domain can be expressed explicitly instead of implicitly.</span></span> <span data-ttu-id="2acce-113">這些效果必須一致，因此所有作業與商務工作相關的情形可能發生的側邊或無一。</span><span class="sxs-lookup"><span data-stu-id="2acce-113">Those side effects must be consistent so either all the operations related to the business task happen, or none of them.</span></span> <span data-ttu-id="2acce-114">此外，網域事件可讓更好的考量，在相同網域中的類別之間的分隔。</span><span class="sxs-lookup"><span data-stu-id="2acce-114">In addition, domain events enable a better separation of concerns among classes within the same domain.</span></span>

<span data-ttu-id="2acce-115">比方說，如果您只要使用只是 Entity Framework 和實體或甚至是彙總，如果必須有一個使用案例所觸發的副作用，這些會實作為繫結的程式碼中的隱含概念之後發生。</span><span class="sxs-lookup"><span data-stu-id="2acce-115">For example, if you are just using just Entity Framework and entities or even aggregates, if there have to be side effects provoked by a use case, those will be implemented as an implicit concept in the coupled code after something happened.</span></span> <span data-ttu-id="2acce-116">但是，如果您只看到該程式碼，您可能不知道該程式碼 （副作用） 有主要作業的一部分，或如果這是真的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-116">But, if you just see that code, you might not know if that code (the side effect) is part of the main operation or if it really is a side effect.</span></span> <span data-ttu-id="2acce-117">相反地，使用網域事件可讓概念明確和通用語言的一部分。</span><span class="sxs-lookup"><span data-stu-id="2acce-117">On the other hand, using domain events makes the concept explicit and part of the ubiquitous language.</span></span> <span data-ttu-id="2acce-118">比方說，eShopOnContainers 應用程式中建立訂單不幾乎的順序。它會更新，或建立買方彙總根據原始的使用者，因為使用者不是買方就地訂單之前。</span><span class="sxs-lookup"><span data-stu-id="2acce-118">For example, in the eShopOnContainers application, creating an order is not just about the order; it updates or creates a buyer aggregate based on the original user, because the user is not a buyer until there is an order in place.</span></span> <span data-ttu-id="2acce-119">如果您使用網域事件時，您可以明確地表示該網域以規則為基礎的通用網域專家所提供的語言。</span><span class="sxs-lookup"><span data-stu-id="2acce-119">If you use domain events, you can explicitly express that domain rule based in the ubiquitous language provided by the domain experts.</span></span>

<span data-ttu-id="2acce-120">網域事件是有點像訊息樣式事件，但有一個重要的差異。</span><span class="sxs-lookup"><span data-stu-id="2acce-120">Domain events are somewhat similar to messaging-style events, with one important difference.</span></span> <span data-ttu-id="2acce-121">實際的訊息、 訊息佇列，訊息代理程式，或使用 AMPQ 服務匯流排，訊息一律以非同步方式傳送，並跨程序和機器通訊。</span><span class="sxs-lookup"><span data-stu-id="2acce-121">With real messaging, message queuing, message brokers, or a service bus using AMPQ, a message is always sent asynchronously and communicated across processes and machines.</span></span> <span data-ttu-id="2acce-122">這是適用於多個繫結內容、 microservices 或甚至不同的應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="2acce-122">This is useful for integrating multiple Bounded Contexts, microservices, or even different applications.</span></span> <span data-ttu-id="2acce-123">然而，有網域事件中，您想要引發事件，從網域作業目前正在執行，但您想要在相同網域中發生任何副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-123">However, with domain events, you want to raise an event from the domain operation you are currently running, but you want any side effects to occur within the same domain.</span></span>

<span data-ttu-id="2acce-124">網域事件和其副作用 （所觸發的動作之後所管理的事件處理常式） 應該幾乎會立即發生，通常是同處理序，並在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="2acce-124">The domain events and their side effects (the actions triggered afterwards that are managed by event handlers) should occur almost immediately, usually in-process, and within the same domain.</span></span> <span data-ttu-id="2acce-125">因此，網域事件可以同步或非同步。</span><span class="sxs-lookup"><span data-stu-id="2acce-125">Thus, domain events could be synchronous or asynchronous.</span></span> <span data-ttu-id="2acce-126">整合事件，不過，應該一律為非同步。</span><span class="sxs-lookup"><span data-stu-id="2acce-126">Integration events, however, should always be asynchronous.</span></span>

## <a name="domain-events-versus-integration-events"></a><span data-ttu-id="2acce-127">網域與整合事件的事件</span><span class="sxs-lookup"><span data-stu-id="2acce-127">Domain events versus integration events</span></span>

<span data-ttu-id="2acce-128">網域和整合事件語意上來說，是相同的東西： 項目剛好的通知。</span><span class="sxs-lookup"><span data-stu-id="2acce-128">Semantically, domain and integration events are the same thing: notifications about something that just happened.</span></span> <span data-ttu-id="2acce-129">不過，其實作必須不同。</span><span class="sxs-lookup"><span data-stu-id="2acce-129">However, their implementation must be different.</span></span> <span data-ttu-id="2acce-130">定義域事件是只推入到網域事件發送器，這可能會實作為 IoC 容器或任何其他方法為基礎的記憶體中傳遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="2acce-130">Domain events are just messages pushed to a domain event dispatcher, which could be implemented as an in-memory mediator based on an IoC container or any other method.</span></span>

<span data-ttu-id="2acce-131">相反地，整合事件的目的是傳播已認可的交易與更新其他子系統，無論是其他 microservices、 繫結的內容或外部的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2acce-131">On the other hand, the purpose of integration events is to propagate committed transactions and updates to additional subsystems, whether they are other microservices, Bounded Contexts or even external applications.</span></span> <span data-ttu-id="2acce-132">因此，它們應該只当成功保存實體，因為在許多情況下如果失敗，整個作業實際上永遠不會發生。</span><span class="sxs-lookup"><span data-stu-id="2acce-132">Hence, they should occur only if the entity is successfully persisted, since in many scenarios if this fails, the entire operation effectively never happened.</span></span>

<span data-ttu-id="2acce-133">此外，以及所述，整合事件必須以多個 microservices （其他繫結內容中） 或外部系統/應用程式之間的非同步通訊。</span><span class="sxs-lookup"><span data-stu-id="2acce-133">In addition, and as mentioned, integration events must be based on asynchronous communication between multiple microservices (other Bounded Contexts) or even external systems/applications.</span></span> <span data-ttu-id="2acce-134">因此，事件匯流排介面需要一些基礎結構間的程序及發佈潛在遠端服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="2acce-134">Thus, the event bus interface needs some infrastructure that allows inter-process and distributed communication between potentially remote services.</span></span> <span data-ttu-id="2acce-135">它可以根據商業服務匯流排、 佇列、 共用的資料庫做為信箱，或任何其他分散式，並在理想情況下發送架構的傳訊系統。</span><span class="sxs-lookup"><span data-stu-id="2acce-135">It can be based on a commercial service bus, queues, a shared database used as a mailbox, or any other distributed and ideally push based messaging system.</span></span>

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a><span data-ttu-id="2acce-136">網域事件中當做觸發副作用跨多個相同的網域中的彙總的慣用方法</span><span class="sxs-lookup"><span data-stu-id="2acce-136">Domain events as a preferred way to trigger side effects across multiple aggregates within the same domain</span></span>

<span data-ttu-id="2acce-137">如果執行命令相關的其中一個彙總的執行個體都需要額外的定義域規則執行一個或多個其他彙總，您應該設計並實作網域事件所觸發的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-137">If executing a command related to one aggregate instance requires additional domain rules to be run on one or more additional aggregates, you should design and implement those side effects to be triggered by domain events.</span></span> <span data-ttu-id="2acce-138">顯示在圖 9-14，以及其中一個最重要的使用案例，網域事件應該用來散佈在相同的網域模型中的多個彙總的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="2acce-138">As shown in Figure 9-14, and as one of the most important use cases, a domain event should be used to propagate state changes across multiple aggregates within the same domain model.</span></span>

![](./media/image15.png)

<span data-ttu-id="2acce-139">**圖 9-14**。</span><span class="sxs-lookup"><span data-stu-id="2acce-139">**Figure 9-14**.</span></span> <span data-ttu-id="2acce-140">若要強制執行相同的網域中的多個彙總之間的一致性定義域事件</span><span class="sxs-lookup"><span data-stu-id="2acce-140">Domain events to enforce consistency between multiple aggregates within the same domain</span></span>

<span data-ttu-id="2acce-141">在圖中，當使用者啟動的順序，OrderStarted 網域事件觸發程序建立買方物件在排序的微服務，根據原始使用者資訊識別微服務從 （與 CreateOrder 命令中提供的資訊）。</span><span class="sxs-lookup"><span data-stu-id="2acce-141">In the figure, when the user initiates an order, the OrderStarted domain event triggers creation of a Buyer object in the ordering microservice, based on the original user info from the identity microservice (with information provided in the CreateOrder command).</span></span> <span data-ttu-id="2acce-142">在第一次建立時，會產生順序彙總所網域事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-142">The domain event is generated by the order aggregate when it is created in the first place.</span></span>

<span data-ttu-id="2acce-143">或者，您可以讓彙總根訂閱以供其彙總 （子實體） 的成員所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-143">Alternately, you can have the aggregate root subscribed for events raised by members of its aggregates (child entities).</span></span> <span data-ttu-id="2acce-144">比方說，每個 OrderItem 子實體可以引發事件，當項目價格高於特定容量，或產品項目數量太高。</span><span class="sxs-lookup"><span data-stu-id="2acce-144">For instance, each OrderItem child entity can raise an event when the item price is higher than a specific amount, or when the product item amount is too high.</span></span> <span data-ttu-id="2acce-145">彙總根可以接收這些事件並執行全域的計算或彙總。</span><span class="sxs-lookup"><span data-stu-id="2acce-145">The aggregate root can then receive those events and perform a global calculation or aggregation.</span></span>

<span data-ttu-id="2acce-146">請務必了解，此事件為基礎的通訊不會實作直接在彙總; 內您需要實作網域事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-146">It is important to understand that this event-based communication is not implemented directly within the aggregates; you need to implement domain event handlers.</span></span> <span data-ttu-id="2acce-147">處理網域事件是應用程式考量。</span><span class="sxs-lookup"><span data-stu-id="2acce-147">Handling the domain events is an application concern.</span></span> <span data-ttu-id="2acce-148">網域模型層應該只著重於網域邏輯 — 網域專家瞭解的重點，不像處理常式，並使用儲存機制的副作用是持續性動作的應用程式基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2acce-148">The domain model layer should only focus on the domain logic—things that a domain expert would understand, not application infrastructure like handlers and side-effect persistence actions using repositories.</span></span> <span data-ttu-id="2acce-149">因此，應用程式層級是您應該在其中有網域網域事件引發時，觸發動作的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-149">Therefore, the application layer level is where you should have domain event handlers triggering actions when a domain event is raised.</span></span>

<span data-ttu-id="2acce-150">網域事件也可用來觸發任何數目的應用程式的動作，並更重要的是，必須開啟才能解除解合的方式增加未來該數字。</span><span class="sxs-lookup"><span data-stu-id="2acce-150">Domain events can also be used to trigger any number of application actions, and what is more important, must be open to increase that number in the future in a decoupled way.</span></span> <span data-ttu-id="2acce-151">比方說，當啟動順序時，您可以發佈網域事件傳播至其他彙總該資訊或甚至引發通知之類的應用程式動作。</span><span class="sxs-lookup"><span data-stu-id="2acce-151">For instance, when the order is started, you might want to publish a domain event to propagate that info to other aggregates or even to raise application actions like notifications.</span></span>

<span data-ttu-id="2acce-152">重點是開啟的網域事件發生時要執行的動作數目。</span><span class="sxs-lookup"><span data-stu-id="2acce-152">The key point is the open number of actions to be executed when a domain event occurs.</span></span> <span data-ttu-id="2acce-153">最後，將會成長的動作和網域和應用程式中的規則。</span><span class="sxs-lookup"><span data-stu-id="2acce-153">Eventually, the actions and rules in the domain and application will grow.</span></span> <span data-ttu-id="2acce-154">複雜度或一些副作用動作發生情況時將會成長，但如果您的程式碼結合 「 黏附 」 (也就只具現化新的關鍵字在 C 中的物件\#)，則每當您需要加入新的動作，您必須變更原始的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2acce-154">The complexity or number of side-effect actions when something happens will grow, but if your code were coupled with “glue” (that is, just instantiating objects with the new keyword in C\#), then every time you needed to add a new action you would need to change the original code.</span></span> <span data-ttu-id="2acce-155">因為每個新的需求，您可能需要變更原始碼流程，這可能導致新的 bug。</span><span class="sxs-lookup"><span data-stu-id="2acce-155">This could result in new bugs, because with each new requirement you would need to change the original code flow.</span></span> <span data-ttu-id="2acce-156">這會針對[開啟/關閉原則](https://en.wikipedia.org/wiki/Open/closed_principle)從[實心](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))。</span><span class="sxs-lookup"><span data-stu-id="2acce-156">This goes against the [Open/Closed principle](https://en.wikipedia.org/wiki/Open/closed_principle) from [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)).</span></span> <span data-ttu-id="2acce-157">不僅如此，原始的協調作業的類別會成長，成長時，它會針對[單一責任原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)。</span><span class="sxs-lookup"><span data-stu-id="2acce-157">Not only that, the original class that was orchestrating the operations would grow and grow, which goes against the [Single Responsibility Principle (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).</span></span>

<span data-ttu-id="2acce-158">相反地，如果您使用網域事件時，您可以建立更細緻和低耦合實作將分別存放於責任使用這種方法：</span><span class="sxs-lookup"><span data-stu-id="2acce-158">On the other hand, if you use domain events, you can create a fine-grained and decoupled implementation by segregating responsibilities using this approach:</span></span>

1.  <span data-ttu-id="2acce-159">傳送命令 (例如，CreateOrder)。</span><span class="sxs-lookup"><span data-stu-id="2acce-159">Send a command (for example, CreateOrder).</span></span>
2.  <span data-ttu-id="2acce-160">接收命令的命令處理常式中。</span><span class="sxs-lookup"><span data-stu-id="2acce-160">Receive the command in a command handler.</span></span>
    -   <span data-ttu-id="2acce-161">執行的單一彙總的交易。</span><span class="sxs-lookup"><span data-stu-id="2acce-161">Execute a single aggregate’s transaction.</span></span>
    -   <span data-ttu-id="2acce-162">（選擇性）引發網域副作用 (例如，OrderStartedDomainDvent) 事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-162">(Optional) Raise domain events for side effects (for example, OrderStartedDomainDvent).</span></span>
1.  <span data-ttu-id="2acce-163">控制代碼網域 （在目前的處理序） 內的事件 thast 中多個彙總或應用程式動作，將執行副作用中開啟的數目。</span><span class="sxs-lookup"><span data-stu-id="2acce-163">Handle domain events (within the current process) thast will execute an open number of side effects in multiple aggregates or application actions.</span></span> <span data-ttu-id="2acce-164">例如: </span><span class="sxs-lookup"><span data-stu-id="2acce-164">For example:</span></span>
    -   <span data-ttu-id="2acce-165">請確認，或建立買方 」 和 「 付款方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-165">Verify or create buyer and payment method.</span></span>
    -   <span data-ttu-id="2acce-166">建立並傳送到事件匯流排散佈 microservices 或觸發程序外部的動作，例如傳送電子郵件給買方的狀態相關的整合事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-166">Create and send a related integration event to the event bus to propagate states across microservices or trigger external actions like sending an email to the buyer.</span></span>
    -   <span data-ttu-id="2acce-167">處理其他副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-167">Handle other side effects.</span></span>

<span data-ttu-id="2acce-168">所示圖 9-15，從相同的網域事件中，您可以處理多個網域或您要執行跨 microservices 與整合事件和事件匯流排連線的其他應用程式動作中的其他彙總相關的動作。</span><span class="sxs-lookup"><span data-stu-id="2acce-168">As shown in Figure 9-15, starting from the same domain event, you can handle multiple actions related to other aggregates in the domain or additional application actions you need to perform across microservices connecting with integration events and the event bus.</span></span>

![](./media/image16.png)

<span data-ttu-id="2acce-169">**圖 9-15**。</span><span class="sxs-lookup"><span data-stu-id="2acce-169">**Figure 9-15**.</span></span> <span data-ttu-id="2acce-170">處理每個網域的多個動作</span><span class="sxs-lookup"><span data-stu-id="2acce-170">Handling multiple actions per domain</span></span>

<span data-ttu-id="2acce-171">事件處理常式通常是在應用程式層中，因為您將使用應用程式 API 等儲存機制的基礎結構物件的微服務的行為。</span><span class="sxs-lookup"><span data-stu-id="2acce-171">The event handlers are typically in the application layer, because you will use infrastructure objects like repositories or an application API for the microservice’s behavior.</span></span> <span data-ttu-id="2acce-172">該意義而言，事件處理常式如下命令處理常式，因此兩者都是應用程式層的一部分。</span><span class="sxs-lookup"><span data-stu-id="2acce-172">In that sense, event handlers are similar to command handlers, so both are part of the application layer.</span></span> <span data-ttu-id="2acce-173">重要的差異在於命令應該就可以一次處理。</span><span class="sxs-lookup"><span data-stu-id="2acce-173">The important difference is that a command should be processed just once.</span></span> <span data-ttu-id="2acce-174">網域事件可能是處理零或* n *逾時，因為如果可以由多個接收者或有不同的用途，每個處理常式的事件處理常式接收。</span><span class="sxs-lookup"><span data-stu-id="2acce-174">A domain event could be processed zero or *n* times, because if can be received by multiple receivers or event handlers with a different purpose for each handler.</span></span>

<span data-ttu-id="2acce-175">開啟數目的每個網域事件處理常式的可能性，可讓您新增許多更多的定義域規則，而不會影響您目前的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2acce-175">The possibility of an open number of handlers per domain event allows you to add many more domain rules without impacting your current code.</span></span> <span data-ttu-id="2acce-176">比方說，實作下列的商務規則必須在發生事件之後，就可能發生權限可能是，只要加入幾個事件處理常式 （或甚至只是其中一個）：</span><span class="sxs-lookup"><span data-stu-id="2acce-176">For instance, implementing the following business rule that has to happen right after an event might be as easy as adding a few event handlers (or even just one):</span></span>

<span data-ttu-id="2acce-177">當客戶購買的存放區中任何數目的訂單之間的總金額超過 $6000 時，10%折扣關閉套用於每個新的訂單，並通知未來訂單該折扣的相關電子郵件與客戶。</span><span class="sxs-lookup"><span data-stu-id="2acce-177">When the total amount purchased by a customer in the store, across any number of orders, exceeds $6,000, apply a 10% off discount to every new order and notify the customer with an email about that discount for future orders.</span></span>

## <a name="implementing-domain-events"></a><span data-ttu-id="2acce-178">實作定義域事件</span><span class="sxs-lookup"><span data-stu-id="2acce-178">Implementing domain events</span></span>

<span data-ttu-id="2acce-179">在 C# 中，只需的網域事件是保存資料之結構或類別，例如 DTO，相關項目剛好在網域中，如下列範例所示的所有資訊：</span><span class="sxs-lookup"><span data-stu-id="2acce-179">In C#, a domain event is simply a data-holding structure or class, like a DTO, with all the information related to what just happened in the domain, as shown in the following example:</span></span>

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

<span data-ttu-id="2acce-180">這是基本上保留 OrderStarted 事件相關的所有資料的類別。</span><span class="sxs-lookup"><span data-stu-id="2acce-180">This is essentially a class that holds all the data related to the OrderStarted event.</span></span>

<span data-ttu-id="2acce-181">根據網域的通用語言事件是發生在過去，因為事件的類別名稱應該表示成過去式時態動詞命令，例如 OrderStartedDomainEvent 或 OrderShippedDomainEvent。</span><span class="sxs-lookup"><span data-stu-id="2acce-181">In terms of the ubiquitous language of the domain, since an event is something that happened in the past, the class name of the event should be represented as a past-tense verb, like OrderStartedDomainEvent or OrderShippedDomainEvent.</span></span> <span data-ttu-id="2acce-182">這是網域事件中 eShopOnContainers 中順序的微服務的實作方式。</span><span class="sxs-lookup"><span data-stu-id="2acce-182">That is how the domain event is implemented in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="2acce-183">如我們所述，重要的特性的事件是因為事件是發生在過去，不應該變更的項目。</span><span class="sxs-lookup"><span data-stu-id="2acce-183">As we have noted, an important characteristic of events is that since an event is something that happened in the past, it should not change.</span></span> <span data-ttu-id="2acce-184">因此，它必須是不可變的類別。</span><span class="sxs-lookup"><span data-stu-id="2acce-184">Therefore it must be an immutable class.</span></span> <span data-ttu-id="2acce-185">您可以看到上述的屬性是唯讀狀態從外部物件的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="2acce-185">You can see in the preceding code that the properties are read-only from outside of the object.</span></span> <span data-ttu-id="2acce-186">更新物件的唯一方式是透過建構函式，當您建立事件物件。</span><span class="sxs-lookup"><span data-stu-id="2acce-186">The only way to update the object is through the constructor when you create the event object.</span></span>

### <a name="raising-domain-events"></a><span data-ttu-id="2acce-187">引發定義域事件</span><span class="sxs-lookup"><span data-stu-id="2acce-187">Raising domain events</span></span>

<span data-ttu-id="2acce-188">下一個問題是如何引發網域事件，讓它達到其相關的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-188">The next question is how to raise a domain event so it reaches its related event handlers.</span></span> <span data-ttu-id="2acce-189">您可以使用多個方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-189">You can use multiple approaches.</span></span>

<span data-ttu-id="2acce-190">Udi Dahan 原本 (例如，在幾個相關的文章，例如[網域事件 – 採用 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) 使用靜態類別，用於管理和引發事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-190">Udi Dahan originally proposed (for example, in several related posts, such as [Domain Events – Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) using a static class for managing and raising the events.</span></span> <span data-ttu-id="2acce-191">這可能包括名為 DomainEvents，就會引發網域事件立即時呼叫它時，使用類似下面的 DomainEvents.Raise (事件 myEvent) 語法的靜態類別。</span><span class="sxs-lookup"><span data-stu-id="2acce-191">This might include a static class named DomainEvents that would raise domain events immediately when it is called, using syntax like DomainEvents.Raise(Event myEvent).</span></span> <span data-ttu-id="2acce-192">Jimmy Bogard 所撰寫的部落格文章 ([加強您的網域： 定義域事件](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) 的建議有類似的方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-192">Jimmy Bogard wrote a blog post ([Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) that recommends a similar approach.</span></span>

<span data-ttu-id="2acce-193">不過，靜態網域事件類別時，它也會分派至處理常式立即。</span><span class="sxs-lookup"><span data-stu-id="2acce-193">However, when the domain events class is static, it also dispatches to handlers immediately.</span></span> <span data-ttu-id="2acce-194">這使得測試和偵錯更加困難，因為具有副作用邏輯的事件處理常式就會引發事件之後立即執行。</span><span class="sxs-lookup"><span data-stu-id="2acce-194">This makes testing and debugging more difficult, because the event handlers with side-effects logic are executed immediately after the event is raised.</span></span> <span data-ttu-id="2acce-195">當您測試和偵錯時，您想要在焦點時，就為什麼在目前的彙總類別。您不想突然重新導向至其他的事件處理常式與其他彙總或應用程式邏輯相關的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-195">When you are testing and debugging, you want to focus on and just what is happening in the current aggregate classes; you do not want to suddenly be redirected to other event handlers for side effects related to other aggregates or application logic.</span></span> <span data-ttu-id="2acce-196">這就是為什麼進化其他方法下, 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="2acce-196">This is why other approaches have evolved, as explained in the next section.</span></span>

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a><span data-ttu-id="2acce-197">延後的方法，引發及分派事件</span><span class="sxs-lookup"><span data-stu-id="2acce-197">The deferred approach for raising and dispatching events</span></span>

<span data-ttu-id="2acce-198">更好的方法是將網域事件加入至集合而不是立即分派給網域的事件處理常式，然後再分派這些網域事件*前*或*右* *之後*（如同在 EF SaveChanges) 認可交易。</span><span class="sxs-lookup"><span data-stu-id="2acce-198">Instead of dispatching to a domain event handler immediately, a better approach is to add the domain events to a collection and then to dispatch those domain events *right before* or *right* *after* committing the transaction (as with SaveChanges in EF).</span></span> <span data-ttu-id="2acce-199">(這種方法所述的 Jimmy Bogard 這篇文章[更好的網域事件模式](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)。)</span><span class="sxs-lookup"><span data-stu-id="2acce-199">(This approach was described by Jimmy Bogard in this post [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)</span></span>

<span data-ttu-id="2acce-200">決定是否網域事件傳送右或向右之前認可交易之後是交易的很重要，因為它會決定是否將包含副作用包含做為相同或在不同的交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="2acce-200">Deciding if you send the domain events right before or right after committing the transaction is important, since it determines whether you will include the side effects as part of the same transaction or in different transactions.</span></span> <span data-ttu-id="2acce-201">在後者的情況下，您需要跨多個彙總處理最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2acce-201">In the latter case, you need to deal with eventual consistency across multiple aggregates.</span></span> <span data-ttu-id="2acce-202">本主題下一節中討論。</span><span class="sxs-lookup"><span data-stu-id="2acce-202">This topic is discussed in the next section.</span></span>

<span data-ttu-id="2acce-203">延後的方法是何種 eShopOnContainers 使用。</span><span class="sxs-lookup"><span data-stu-id="2acce-203">The deferred approach is what eShopOnContainers uses.</span></span> <span data-ttu-id="2acce-204">首先，您將事件加入至集合或每個實體的事件清單中實體的情況。</span><span class="sxs-lookup"><span data-stu-id="2acce-204">First, you add the events happening in your entities into a collection or list of events per entity.</span></span> <span data-ttu-id="2acce-205">該清單應使用屬於的實體物件，或更好的是，您的基底實體類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2acce-205">That list should be part of the entity object, or even better, part of your base entity class, as shown in the following example:</span></span>

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

<span data-ttu-id="2acce-206">當您想要引發事件時，您只將它加入至事件的集合，以便放置在彙總實體方法中，下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="2acce-206">When you want to raise an event, you just add it to the event collection to be placed within an aggregate entity method, as the following code shows:</span></span>

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
    cardTypeId,
    cardNumber,
    cardSecurityNumber,
    cardHolderName,
    cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

<span data-ttu-id="2acce-207">請注意唯一 AddDomainEvent 方法正在進行的事情將事件加入至清單。</span><span class="sxs-lookup"><span data-stu-id="2acce-207">Notice that the only thing that the AddDomainEvent method is doing is adding an event to the list.</span></span> <span data-ttu-id="2acce-208">不會引發事件，以及尚未叫用事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-208">No event is raised yet, and no event handler is invoked yet.</span></span>

<span data-ttu-id="2acce-209">您實際想要分派事件之後，當您認可資料庫交易。</span><span class="sxs-lookup"><span data-stu-id="2acce-209">You actually want to dispatch the events later on, when you commit the transaction to the database.</span></span> <span data-ttu-id="2acce-210">如果您使用 Entity Framework Core，就表示您 EF DbContext，如下列程式碼所示的 SaveChanges 方法：</span><span class="sxs-lookup"><span data-stu-id="2acce-210">If you are using Entity Framework Core, that means in the SaveChanges method of your EF DbContext, as in the following code:</span></span>

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

<span data-ttu-id="2acce-211">使用此程式碼中，您分派至其各自的事件處理常式的實體事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-211">With this code, you dispatch the entity events to their respective event handlers.</span></span>

<span data-ttu-id="2acce-212">整體結果是，您必須分開 （簡單新增到清單中，在記憶體中） 的網域事件的引發分派給事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-212">The overall result is that you have decoupled the raising of a domain event (a simple add into a list in memory) from dispatching it to an event handler.</span></span> <span data-ttu-id="2acce-213">此外，根據您使用何種發送器，以同步或非同步方式無法分派事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-213">In addition, depending on what kind of dispatcher you are using, you could dispatch the events synchronously or asynchronously.</span></span>

<span data-ttu-id="2acce-214">請注意交易界限進入重大這裡播放。</span><span class="sxs-lookup"><span data-stu-id="2acce-214">Be aware that transactional boundaries come into significant play here.</span></span> <span data-ttu-id="2acce-215">如果您的工作和交易的單位可以跨越多個彙總 （如同使用 EF 核心和關聯式資料庫時），這可以正常運作。</span><span class="sxs-lookup"><span data-stu-id="2acce-215">If your unit of work and transaction can span more than one aggregate (as when using EF Core and a relational database), this can work well.</span></span> <span data-ttu-id="2acce-216">但是，如果交易無法跨越彙總，例如當您使用類似 Azure DocumentDB 的 NoSQL 資料庫您必須實作額外的步驟，以達到一致性。</span><span class="sxs-lookup"><span data-stu-id="2acce-216">But if the transaction cannot span aggregates, such as when you are using a NoSQL database like Azure DocumentDB, you have to implement additional steps to achieve consistency.</span></span> <span data-ttu-id="2acce-217">這是另一個原因永續性無知之不通用。這取決於您使用的儲存系統。</span><span class="sxs-lookup"><span data-stu-id="2acce-217">This is another reason why persistence ignorance is not universal; it depends on the storage system you use.</span></span>

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a><span data-ttu-id="2acce-218">單一交易上與最終一致性彙總的彙總</span><span class="sxs-lookup"><span data-stu-id="2acce-218">Single transaction across aggregates versus eventual consistency across aggregates</span></span>

<span data-ttu-id="2acce-219">是否要執行跨與信賴憑證者最終一致性跨這些彙總的彙總的單一交易的問題是爭議一個。</span><span class="sxs-lookup"><span data-stu-id="2acce-219">The question of whether to perform a single transaction across aggregates versus relying on eventual consistency across those aggregates is a controversial one.</span></span> <span data-ttu-id="2acce-220">許多 DDD 作者像 Eric Evans 和 Vaughn Vernon 主張規則的一筆交易 = 一個彙總，並因此主張最終一致性跨彙總。</span><span class="sxs-lookup"><span data-stu-id="2acce-220">Many DDD authors like Eric Evans and Vaughn Vernon advocate the rule that one transaction = one aggregate and therefore argue for eventual consistency across aggregates.</span></span> <span data-ttu-id="2acce-221">例如，在他的書*Domain-Driven 設計*，Eric Evans 表示：</span><span class="sxs-lookup"><span data-stu-id="2acce-221">For example, in his book *Domain-Driven Design*, Eric Evans says this:</span></span>

<span data-ttu-id="2acce-222">跨越彙總任何規則就不應該在任何時間都保持最新狀態。</span><span class="sxs-lookup"><span data-stu-id="2acce-222">Any rule that spans Aggregates will not be expected to be up-to-date at all times.</span></span> <span data-ttu-id="2acce-223">事件處理、 批次的處理或其他的更新機制，透過其他相依性可以解決一些特定的時間內。</span><span class="sxs-lookup"><span data-stu-id="2acce-223">Through event processing, batch processing, or other update mechanisms, other dependencies can be resolved within some specific time.</span></span> <span data-ttu-id="2acce-224">(pg。</span><span class="sxs-lookup"><span data-stu-id="2acce-224">(pg.</span></span> <span data-ttu-id="2acce-225">128)</span><span class="sxs-lookup"><span data-stu-id="2acce-225">128)</span></span>

<span data-ttu-id="2acce-226">Vaughn Vernon 說明中的下列[有效彙總設計。第 II 部分︰ 進行彙總工作一起](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):</span><span class="sxs-lookup"><span data-stu-id="2acce-226">Vaughn Vernon says the following in [Effective Aggregate Design. Part II: Making Aggregates Work Together](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):</span></span>

<span data-ttu-id="2acce-227">因此，如果其中一個彙總的執行個體都需要額外的商務規則執行一個或多個彙總上執行命令，使用 [最終一致性\[...\]沒有可行的方式，可支援 DDD 模型中的最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2acce-227">Thus, if executing a command on one aggregate instance requires that additional business rules execute on one or more aggregates, use eventual consistency \[...\] There is a practical way to support eventual consistency in a DDD model.</span></span> <span data-ttu-id="2acce-228">彙總的方法發行時間傳遞給一個或多個非同步訂閱者的網域事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-228">An aggregate method publishes a domain event that is in time delivered to one or more asynchronous subscribers.</span></span>

<span data-ttu-id="2acce-229">這根據對照採用更細緻的交易，而不是跨越多個彙總或實體的交易。</span><span class="sxs-lookup"><span data-stu-id="2acce-229">This rationale is based on embracing fine-grained transactions instead of transactions spanning many aggregates or entities.</span></span> <span data-ttu-id="2acce-230">作法是在第二個案例中，資料庫鎖定數目將會相當高的延展性需求的大型應用程式中。</span><span class="sxs-lookup"><span data-stu-id="2acce-230">The idea is that in the second case, the number of database locks will be substantial in large-scale applications with high scalability needs.</span></span> <span data-ttu-id="2acce-231">採用高可擴充的應用程式需要具有多個彙總之間的即時交易一致性的事實會協助接受最終一致性的概念。</span><span class="sxs-lookup"><span data-stu-id="2acce-231">Embracing the fact that high-scalable applications need not have instant transactional consistency between multiple aggregates helps with accepting the concept of eventual consistency.</span></span> <span data-ttu-id="2acce-232">企業通常不需要不可部分完成的變更，它負責在任何情況下網域專家說出特定作業是否需要不可部分完成交易，或不。</span><span class="sxs-lookup"><span data-stu-id="2acce-232">Atomic changes are often not needed by the business, and it is in any case the responsibility of the domain experts to say whether particular operations need atomic transactions or not.</span></span> <span data-ttu-id="2acce-233">如果作業一律需要多個彙總之間的不可部分完成交易，您可能會要求您彙總是否應該是較大，或設計不正確。</span><span class="sxs-lookup"><span data-stu-id="2acce-233">If an operation always needs an atomic transaction between multiple aggregates, you might ask whether your aggregate should be larger or was not correctly designed.</span></span>

<span data-ttu-id="2acce-234">不過，其他開發人員和架構設計人員 Jimmy Bogard 像要橫跨數個彙總的單一交易，但只有當這些額外的彙總相關相同原始命令的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-234">However, other developers and architects like Jimmy Bogard are okay with spanning a single transaction across several aggregates—but only when those additional aggregates are related to side effects for the same original command.</span></span> <span data-ttu-id="2acce-235">例如，在[更好的網域事件模式](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)，Bogard 表示：</span><span class="sxs-lookup"><span data-stu-id="2acce-235">For instance, in [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard says this:</span></span>

<span data-ttu-id="2acce-236">一般而言，我想網域事件發生在相同的邏輯交易內，但不是一定相同範圍的乘冪，網域事件中的副作用\[...\]我們只認可我們交易之前，我們會分派至其個別的處理常式我們事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-236">Typically, I want the side effects of a domain event to occur within the same logical transaction, but not necessarily in the same scope of raising the domain event \[...\] Just before we commit our transaction, we dispatch our events to their respective handlers.</span></span>

<span data-ttu-id="2acce-237">如果分派網域事件右邊*之前*認可原始交易，這是因為您想要在相同交易中包含這些事件產生的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-237">If you dispatch the domain events right *before* committing the original transaction, it is because you want the side effects of those events to be included in the same transaction.</span></span> <span data-ttu-id="2acce-238">例如，如果 EF DbContext SaveChanges 方法失敗，交易將會回復所有變更，包括任何相關的網域的事件處理常式所實作的副作用作業的結果。</span><span class="sxs-lookup"><span data-stu-id="2acce-238">For example, if the EF DbContext SaveChanges method fails, the transaction will roll back all changes, including the result of any side effect operations implemented by the related domain event handlers.</span></span> <span data-ttu-id="2acce-239">這是因為 DbContext 生命範圍定義為預設 「 範圍限定。 」</span><span class="sxs-lookup"><span data-stu-id="2acce-239">This is because the DbContext life scope is by default defined as "scoped."</span></span> <span data-ttu-id="2acce-240">因此，將 DbContext 物件共用跨多個具現化相同範圍或物件圖形內的儲存機制物件。</span><span class="sxs-lookup"><span data-stu-id="2acce-240">Therefore, the DbContext object is shared across multiple repository objects being instantiated within the same scope or object graph.</span></span> <span data-ttu-id="2acce-241">這會伴隨 HttpRequest 範圍，開發 Web 應用程式開發介面或 MVC 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="2acce-241">This coincides with the HttpRequest scope when developing Web API or MVC apps.</span></span>

<span data-ttu-id="2acce-242">事實上，這兩種方法 （「 單一不可部分完成交易 」 和 「 最終一致性 」） 可以是權限。</span><span class="sxs-lookup"><span data-stu-id="2acce-242">In reality, both approaches (single atomic transaction and eventual consistency) can be right.</span></span> <span data-ttu-id="2acce-243">它其實取決於您的網域或商務需求和目標網域專家告訴您。</span><span class="sxs-lookup"><span data-stu-id="2acce-243">It really depends on your domain or business requirements and what the domain experts tell you.</span></span> <span data-ttu-id="2acce-244">它也取決於您需要的服務如何擴充 （更細微的交易都有較不會影響資料庫鎖定方面）。</span><span class="sxs-lookup"><span data-stu-id="2acce-244">It also depends on how scalable you need the service to be (more granular transactions have less impact with regard to database locks).</span></span> <span data-ttu-id="2acce-245">同時，取決於多少投資您願意，讓您的程式碼中，因為最終一致性需要更複雜的程式碼，以便在彙總的需要實作的補償動作，以及偵測可能不一致。</span><span class="sxs-lookup"><span data-stu-id="2acce-245">And it depends on how much investment you are willing to make in your code, since eventual consistency requires more complex code in order to detect possible inconsistencies across aggregates and the need to implement compensatory actions.</span></span> <span data-ttu-id="2acce-246">請考量您與原始的彙總之後，當發送事件認可變更，如果沒有問題和事件處理常式無法認可其副作用，您必須彙總之間的不一致。</span><span class="sxs-lookup"><span data-stu-id="2acce-246">Take into account that if you commit changes to the original aggregate and afterwards, when the events are being dispatched, there is an issue and the event handlers cannot commit their side effects, you will have inconsistencies between aggregates.</span></span>

<span data-ttu-id="2acce-247">可補償動作的方法是在其他資料庫資料表中儲存網域事件，以便它們可以是原始交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="2acce-247">A way to allow compensatory actions would be to store the domain events in additional database tables so they can be part of the original transaction.</span></span> <span data-ttu-id="2acce-248">之後，您可能會有批次程序偵測到不一致，並藉由比較事件的目前狀態的彙總清單中執行的補償動作。</span><span class="sxs-lookup"><span data-stu-id="2acce-248">Afterwards, you could have a batch process that detects inconsistencies and runs compensatory actions by comparing the list of events with the current state of the aggregates.</span></span> <span data-ttu-id="2acce-249">補償動作是主題的一個複雜將會需要從端，其中包括討論與商務使用者 」 和 「 網域專家的深入分析的一部分。</span><span class="sxs-lookup"><span data-stu-id="2acce-249">The compensatory actions are part of a complex topic that will require deep analysis from your side, which includes discussing it with the business user and domain experts.</span></span>

<span data-ttu-id="2acce-250">在任何情況下，您可以選擇您需要的方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-250">In any case, you can choose the approach you need.</span></span> <span data-ttu-id="2acce-251">初始延遲方法，但是 — 認可之前，引發事件，讓您使用單一交易 — 使用 EF 核心和關聯式資料庫時，是最簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-251">But the initial deferred approach—raising the events before committing, so you use a single transaction—is the simplest approach when using EF Core and a relational database.</span></span> <span data-ttu-id="2acce-252">它是您更輕鬆地實作和許多商業案例中有效。</span><span class="sxs-lookup"><span data-stu-id="2acce-252">It is easier to implement and valid in many business cases.</span></span> <span data-ttu-id="2acce-253">它也是 eShopOnContainers 中順序的微服務中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-253">It is also the approach used in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="2acce-254">不過，如何執行您實際分派至其各自的事件處理常式的事件嗎？</span><span class="sxs-lookup"><span data-stu-id="2acce-254">But how do you actually dispatch those events to their respective event handlers?</span></span> <span data-ttu-id="2acce-255">什麼是\_暫留處理器物件，您在上述範例中，請參閱？</span><span class="sxs-lookup"><span data-stu-id="2acce-255">What is the \_mediator object that you see in the previous example?</span></span> <span data-ttu-id="2acce-256">具有要執行動作的技術和成品，您可以使用事件和其事件處理常式之間進行對應。</span><span class="sxs-lookup"><span data-stu-id="2acce-256">That has to do with the techniques and artifacts you can use to map between events and their event handlers.</span></span>

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a><span data-ttu-id="2acce-257">網域事件發送器： 從事件對應到事件處理常式</span><span class="sxs-lookup"><span data-stu-id="2acce-257">The domain event dispatcher: mapping from events to event handlers</span></span>

<span data-ttu-id="2acce-258">一旦您能夠分派或發行事件時，您需要某種類型的成品，讓每個相關的處理常式可以取得它，並根據該事件的處理程序的副作用，將發行事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-258">Once you are able to dispatch or publish the events, you need some kind of artifact that will publish the event so that every related handler can get it and process side effects based on that event.</span></span>

<span data-ttu-id="2acce-259">其中一個方法是真正的傳訊系統或甚至事件匯流排，可能會根據服務匯流排，而不是記憶體中的事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-259">One approach is a real messaging system or even an event bus, possibly based on a service bus as opposed to in-memory events.</span></span> <span data-ttu-id="2acce-260">不過，第一個案例中，實際傳訊有點大材小用處理網域事件，因為您只需要處理這些相同的程序內的事件 (也就是相同的網域和應用程式層中)。</span><span class="sxs-lookup"><span data-stu-id="2acce-260">However, for the first case, real messaging would be overkill for processing domain events, since you just need to process those events within the same process (that is, within the same domain and application layer).</span></span>

<span data-ttu-id="2acce-261">將事件對應至多個事件處理常式的另一種方式是使用 IoC 容器中的型別註冊，讓您以動態方式可以推斷分派事件的位置。</span><span class="sxs-lookup"><span data-stu-id="2acce-261">Another way to map events to multiple event handlers is by using types registration in an IoC container so that you can dynamically infer where to dispatch the events.</span></span> <span data-ttu-id="2acce-262">換句話說，您需要知道需要取得的特定事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-262">In other words, you need to know what event handlers need to get a specific event.</span></span> <span data-ttu-id="2acce-263">圖 9 到 16 個顯示的簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-263">Figure 9-16 shows a simplified approach for that.</span></span>

![](./media/image17.png)

<span data-ttu-id="2acce-264">**圖 9 到 16 個**。</span><span class="sxs-lookup"><span data-stu-id="2acce-264">**Figure 9-16**.</span></span> <span data-ttu-id="2acce-265">網域事件發送器使用 IoC</span><span class="sxs-lookup"><span data-stu-id="2acce-265">Domain event dispatcher using IoC</span></span>

<span data-ttu-id="2acce-266">您可以建立所有的配管和方法實作自己的成品。</span><span class="sxs-lookup"><span data-stu-id="2acce-266">You can build all the plumbing and artifacts to implement that approach by yourself.</span></span> <span data-ttu-id="2acce-267">不過，您也可以使用可用的程式庫，例如[MediatR](https://github.com/jbogard/MediatR)，基本上它會使用您的 IoT 容器。</span><span class="sxs-lookup"><span data-stu-id="2acce-267">However, you can also use available libraries like [MediatR](https://github.com/jbogard/MediatR), which underneath the covers uses your IoT container.</span></span> <span data-ttu-id="2acce-268">因此，您可以直接使用預先定義的介面和暫留處理器物件的發行/分派方法。</span><span class="sxs-lookup"><span data-stu-id="2acce-268">You can therefore directly use the predefined interfaces and the mediator object’s publish/dispatch methods.</span></span>

<span data-ttu-id="2acce-269">程式碼中，您必須先註冊事件處理常式型別在 IoC 容器中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2acce-269">In code, you first need to register the event handler types in your IoC container, as shown in the following example:</span></span>

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

<span data-ttu-id="2acce-270">程式碼會先識別包含網域事件處理常式，找出保存任何處理常式的組件的組件 （使用 typeof(ValidateOrAddBuyerAggregateWhenXxxx)，但您也可以選擇任何其他事件處理常式來找出組件）。</span><span class="sxs-lookup"><span data-stu-id="2acce-270">The code first identifies the assembly that contains the domain event handlers by locating the assembly that holds any of the handlers (using typeof(ValidateOrAddBuyerAggregateWhenXxxx), but you could have chosen any other event handler to locate the assembly).</span></span> <span data-ttu-id="2acce-271">因為所有的事件處理常式實作 IAsyncNotificationHandler 介面，然後只搜尋那些，程式碼類型和註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-271">Since all the event handlers implement the IAsyncNotificationHandler interface, the code then just searches for those types and registers all the event handlers.</span></span>

### <a name="how-to-subscribe-to-domain-events"></a><span data-ttu-id="2acce-272">如何訂閱定義域事件</span><span class="sxs-lookup"><span data-stu-id="2acce-272">How to subscribe to domain events</span></span>

<span data-ttu-id="2acce-273">當您使用 MediatR 時，每個事件處理常式必須使用提供 IAsyncNotificationHandler 介面的泛型參數的事件類型，您可以在下列程式碼中看到如下：</span><span class="sxs-lookup"><span data-stu-id="2acce-273">When you use MediatR, each event handler must use an event type that is provided on the generic parameter of the IAsyncNotificationHandler interface, as you can see in the following code:</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

<span data-ttu-id="2acce-274">根據事件和事件處理常式，可視為訂用帳戶，之間的關聯性 MediatR 成品可以探索每個事件的所有事件處理常式，並觸發每個這些事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acce-274">Based on the relationship between event and event handler, which can be considered the subscription, the MediatR artifact can discover all the event handlers for each event and trigger each of those event handlers.</span></span>

### <a name="how-to-handle-domain-events"></a><span data-ttu-id="2acce-275">如何處理定義域事件</span><span class="sxs-lookup"><span data-stu-id="2acce-275">How to handle domain events</span></span>

<span data-ttu-id="2acce-276">最後，此事件處理常式通常會實作會使用基礎結構的儲存機制，來取得所需的其他彙總，並執行副作用網域邏輯的應用程式層程式碼。</span><span class="sxs-lookup"><span data-stu-id="2acce-276">Finally, the event handler usually implements application layer code that uses infrastructure repositories to obtain the required additional aggregates and to execute side-effect domain logic.</span></span> <span data-ttu-id="2acce-277">下列程式碼示範範例。</span><span class="sxs-lookup"><span data-stu-id="2acce-277">The following code shows an example.</span></span>

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

<span data-ttu-id="2acce-278">此事件處理常式程式碼應用程式層程式碼，因此視為它會使用基礎結構儲存機制中，基礎結構保存層中下一節所說明。</span><span class="sxs-lookup"><span data-stu-id="2acce-278">This event handler code is considered application layer code because it uses infrastructure repositories, as explained in the next section on the infrastructure-persistence layer.</span></span> <span data-ttu-id="2acce-279">事件處理常式也可以使用其他基礎結構元件。</span><span class="sxs-lookup"><span data-stu-id="2acce-279">Event handlers could also use other infrastructure components.</span></span>

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a><span data-ttu-id="2acce-280">可以產生整合事件發佈微服務界限以外的網域事件</span><span class="sxs-lookup"><span data-stu-id="2acce-280">Domain events can generate integration events to be published outside of the microservice boundaries</span></span>

<span data-ttu-id="2acce-281">最後，請務必提到，您有時可能會想要跨多個 microservices 傳播事件。</span><span class="sxs-lookup"><span data-stu-id="2acce-281">Finally, is important to mention that you might sometimes want to propagate events across multiple microservices.</span></span> <span data-ttu-id="2acce-282">這即視為整合事件，並無法從任何特定網域的事件處理常式的事件匯流排透過已發佈。</span><span class="sxs-lookup"><span data-stu-id="2acce-282">That is considered an integration event, and it could be published through an event bus from any specific domain event handler.</span></span>

## <a name="conclusions-on-domain-events"></a><span data-ttu-id="2acce-283">結論定義域事件</span><span class="sxs-lookup"><span data-stu-id="2acce-283">Conclusions on domain events</span></span> 

<span data-ttu-id="2acce-284">如所述，使用網域事件明確實作您的網域中的變更的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-284">As stated, use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="2acce-285">若要使用 DDD 術語，用於網域事件明確實作跨一個或多個彙總的副作用。</span><span class="sxs-lookup"><span data-stu-id="2acce-285">To use DDD terminology, use domain events to explicitly implement side effects across one or multiple aggregates.</span></span> <span data-ttu-id="2acce-286">此外，取得更好的延展性和較不影響資料庫鎖定，使用相同的網域中的彙總之間的最終一致性。</span><span class="sxs-lookup"><span data-stu-id="2acce-286">Additionally, and for better scalability and less impact on database locks, use eventual consistency between aggregates within the same domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2acce-287">其他資源</span><span class="sxs-lookup"><span data-stu-id="2acce-287">Additional resources</span></span>

-   <span data-ttu-id="2acce-288">**Greg Young。什麼是網域事件？** 
     [ *http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span><span class="sxs-lookup"><span data-stu-id="2acce-288">**Greg Young. What is a Domain Event?**
[*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span></span>

-   <span data-ttu-id="2acce-289">**Jan Stenberg。網域事件和最終一致性**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span><span class="sxs-lookup"><span data-stu-id="2acce-289">**Jan Stenberg. Domain Events and Eventual Consistency**
[*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span></span>

-   <span data-ttu-id="2acce-290">**Jimmy Bogard：更好的網域事件模式**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span><span class="sxs-lookup"><span data-stu-id="2acce-290">**Jimmy Bogard. A better domain events pattern**
[*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span></span>

-   <span data-ttu-id="2acce-291">**Vaughn Vernon：有效彙總設計第 2 部分： 一起彙總工作進行**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_文章/Vernon\_2011\_2.pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span><span class="sxs-lookup"><span data-stu-id="2acce-291">**Vaughn Vernon. Effective Aggregate Design Part II: Making Aggregates Work Together**
[*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span></span>

-   <span data-ttu-id="2acce-292">**Jimmy Bogard：加強您的網域： 定義域事件**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>*</span><span class="sxs-lookup"><span data-stu-id="2acce-292">**Jimmy Bogard. Strengthening your domain: Domain Events**
*<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *</span></span>

-   <span data-ttu-id="2acce-293">**Tong Truong。網域事件模式範例**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)</span><span class="sxs-lookup"><span data-stu-id="2acce-293">**Tony Truong. Domain Events Pattern Example**
[*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)</span></span>

-   <span data-ttu-id="2acce-294">**Udi Dahan。如何建立完整封裝網域模型**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="2acce-294">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>

-   <span data-ttu-id="2acce-295">**Udi Dahan。網域事件 – 採用 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span><span class="sxs-lookup"><span data-stu-id="2acce-295">**Udi Dahan. Domain Events – Take 2**
[*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span></span>

-   <span data-ttu-id="2acce-296">**Udi Dahan。網域事件 – 拯救**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span><span class="sxs-lookup"><span data-stu-id="2acce-296">**Udi Dahan. Domain Events – Salvation**
[*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span></span>

-   <span data-ttu-id="2acce-297">**Jan Kronquist。不發行網域事件，將其傳回 ！** 
     [ *https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span><span class="sxs-lookup"><span data-stu-id="2acce-297">**Jan Kronquist. Don't publish Domain Events, return them!**
[*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span></span>

-   <span data-ttu-id="2acce-298">**Cesar de la Torre：網域事件 vs。DDD 和 microservices 架構中的整合事件**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span><span class="sxs-lookup"><span data-stu-id="2acce-298">**Cesar de la Torre. Domain Events vs. Integration Events in DDD and microservices architectures**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2acce-299">[上一個](用戶端-側邊-validation.md) [下一步] (基礎結構-持續性-層-design.md)</span><span class="sxs-lookup"><span data-stu-id="2acce-299">[Previous] (client-side-validation.md) [Next] (infrastructure-persistence-layer-design.md)</span></span>
