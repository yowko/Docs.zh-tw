---
title: 在 eShopOnContainers 的 DDD 微服務中套用 CQRS 和 CQS 方法
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 在 eShopOnContainers 的 DDD 微服務中套用 CQRS 和 CQS 方法
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6be8b52f42e3e37ff03e561af45c46f4dd283d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a><span data-ttu-id="e3461-103">在 eShopOnContainers 的 DDD 微服務中套用 CQRS 和 CQS 方法</span><span class="sxs-lookup"><span data-stu-id="e3461-103">Applying CQRS and CQS approaches in a DDD microservice in eShopOnContainers</span></span>

<span data-ttu-id="e3461-104">eShopOnContainers 參考應用程式中訂購微服務的設計是基於 CQRS 準則。</span><span class="sxs-lookup"><span data-stu-id="e3461-104">The design of the ordering microservice at the eShopOnContainers reference application is based on CQRS principles.</span></span> <span data-ttu-id="e3461-105">然而，它使用了最簡單的方法，即單純將查詢與命令分開，以及針對這兩個動作使用相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e3461-105">However, it uses the simplest approach, which is just separating the queries from the commands and using the same database for both actions.</span></span>

<span data-ttu-id="e3461-106">這些模式的精髓以及重點在於查詢是等冪的：無論您查詢系統多少次，系統的狀態都不會變更。您甚至可以使用不同的 “reads” 資料模型，而非交易邏輯的 “writes” 領域模型，雖然訂購微服務使用的是相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e3461-106">The essence of those patterns, and the important point here, is that queries are idempotent: no matter how many times you query a system, the state of that system will not change You could even use a different “reads” data model than the transactional logic “writes” domain model, although the ordering microservices is using the same database.</span></span> <span data-ttu-id="e3461-107">因此，這是簡化過後的 CQRS 方法。</span><span class="sxs-lookup"><span data-stu-id="e3461-107">Hence this is a simplified CQRS approach.</span></span>

<span data-ttu-id="e3461-108">另一方面，觸發交易及資料更新的命令會變更系統的狀態。</span><span class="sxs-lookup"><span data-stu-id="e3461-108">On the other hand, commands, which trigger transactions and data updates, change state in the system.</span></span> <span data-ttu-id="e3461-109">使用命令時，您必須在處理複雜性及不斷變更的商務規則時多加小心。</span><span class="sxs-lookup"><span data-stu-id="e3461-109">With commands, you need to be careful when dealing with complexity and ever-changing business rules.</span></span> <span data-ttu-id="e3461-110">這正是您希望套用 DDD 技術以獲得更良好之模型化系統的場合。</span><span class="sxs-lookup"><span data-stu-id="e3461-110">This is the where you want to apply DDD techniques to have a better modeled system.</span></span>

<span data-ttu-id="e3461-111">本指南中呈現的 DDD 模式不應適用於所有情況。</span><span class="sxs-lookup"><span data-stu-id="e3461-111">The DDD patterns presented in this guide should not be applied universally.</span></span> <span data-ttu-id="e3461-112">他們可能會為您的設計帶來條件約束。</span><span class="sxs-lookup"><span data-stu-id="e3461-112">They introduce constraints on your design.</span></span> <span data-ttu-id="e3461-113">這些條件約束會隨著時間帶來像是更高品質等的優點，尤其是在修改系統狀態的命令及其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="e3461-113">Those constraints provide benefits such as higher quality over time, especially in commands and other code that modifies system state.</span></span> <span data-ttu-id="e3461-114">然而，這些條件約束也會為讀取及查詢資料新增複雜度，卻只能帶來較小的優點。</span><span class="sxs-lookup"><span data-stu-id="e3461-114">However, those constraints add complexity with fewer benefits for reading and querying data.</span></span>

<span data-ttu-id="e3461-115">其中一個模式便是彙總模式，我們會在稍後的章節中檢查。</span><span class="sxs-lookup"><span data-stu-id="e3461-115">One such pattern is the Aggregate pattern, which we examine more in later sections.</span></span> <span data-ttu-id="e3461-116">簡而言之，在彙總模式中，您會將許多領域物件視為其在領域內關聯性結果的單一單位。</span><span class="sxs-lookup"><span data-stu-id="e3461-116">Briefly, in the Aggregate pattern, you treat many domain objects as a single unit as a result of their relationship in the domain.</span></span> <span data-ttu-id="e3461-117">您不一定會想要在查詢中利用這種模式，因為它可能會增加查詢邏輯的複雜度。</span><span class="sxs-lookup"><span data-stu-id="e3461-117">You might not always gain advantages from this pattern in queries; it can increase the complexity of query logic.</span></span> <span data-ttu-id="e3461-118">針對唯讀查詢，您無法藉由將多個物件視為單一彙總而取得好處。</span><span class="sxs-lookup"><span data-stu-id="e3461-118">For read-only queries, you do not get the advantages of treating multiple objects as a single Aggregate.</span></span> <span data-ttu-id="e3461-119">您只會增加複雜度。</span><span class="sxs-lookup"><span data-stu-id="e3461-119">You only get the complexity.</span></span>

<span data-ttu-id="e3461-120">如圖 9-2 中所示，本指南建議您只在您微服務的交易/更新區域內使用 DDD 模式 (即使用命令觸發)。</span><span class="sxs-lookup"><span data-stu-id="e3461-120">As shown in Figure 9-2, this guide suggests using DDD patterns only in the transactional/updates area of your microservice (that is, as triggered by commands).</span></span> <span data-ttu-id="e3461-121">查詢可遵循更簡單的方法，並且與命令分離，遵循 CQRS 方法。</span><span class="sxs-lookup"><span data-stu-id="e3461-121">Queries can follow a simpler approach and should be separated from commands, following a CQRS approach.</span></span>

<span data-ttu-id="e3461-122">若要實作「查詢端」，您可以從您完全成熟的 ORM，像是 EF Core、AutoMapper 投影、預存程序、檢視、具體化檢視或微型 ORM 等許多方法中選擇。</span><span class="sxs-lookup"><span data-stu-id="e3461-122">For implementing the “queries side”, you can choose between many approaches, from your full-blown ORM like EF Core, AutoMapper projections, stored procedures, views, materialized views or a micro ORM.</span></span>

<span data-ttu-id="e3461-123">本指南及 eShopOnContainers 中 (特別是訂購微服務)，我們選擇使用像是 [Dapper](https://github.com/StackExchange/dapper-dot-net) 的微型 ORM 來實作直接查詢。</span><span class="sxs-lookup"><span data-stu-id="e3461-123">In this guide and in eShopOnContainers (specifically the ordering microservice) we chose to implement straight queries using a micro ORM like [Dapper](https://github.com/StackExchange/dapper-dot-net).</span></span> <span data-ttu-id="e3461-124">多虧了輕型架構所帶來的極少負荷，這可讓您實作任何基於查詢的 SQL 陳述式，以取得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="e3461-124">This lets you implement any query based on SQL statements to get the best performance, thanks to a light framework with very little overhead.</span></span>

<span data-ttu-id="e3461-125">請注意，當您使用這種方法時，任何對您模型進行的，會影響到實體永續儲存於 SQL 資料庫的更新都需要另外對 Dapper 或任何其他分離 (非 EF) 的查詢方法所使用的查詢進行更新。</span><span class="sxs-lookup"><span data-stu-id="e3461-125">Note that when you use this approach, any updates to your model that impact how entities are persisted to a SQL database also need separate updates to SQL queries used by Dapper or any other separate (non-EF) approaches to querying.</span></span>

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a><span data-ttu-id="e3461-126">CQRS 及 DDD 模式並非頂層架構</span><span class="sxs-lookup"><span data-stu-id="e3461-126">CQRS and DDD patterns are not top-level architectures</span></span>

<span data-ttu-id="e3461-127">了解 CQRS 和大多數的 DDD 模式 (例如 DDD 層或使用彙總的領域模型) 都不是架構樣式，而只是架構模式是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="e3461-127">It important to understand that CQRS and most DDD patterns (like DDD layers or a domain model with aggregates) are not architectural styles, but only architecture patterns.</span></span> <span data-ttu-id="e3461-128">微服務、SOA，以及事件驅動架構 (EDA) 才是架構樣式的範例。</span><span class="sxs-lookup"><span data-stu-id="e3461-128">Microservices, SOA, and event-driven architecture (EDA) are examples of architectural styles.</span></span> <span data-ttu-id="e3461-129">他們描述了由許多元件組成的系統，例如許多微服務。</span><span class="sxs-lookup"><span data-stu-id="e3461-129">They describe a system of many components, such as many microservices.</span></span> <span data-ttu-id="e3461-130">CQRS 和 DDD 模式描述了單一系統或元件中的某些事物。在此範例中，即是微服務中的某些事物。</span><span class="sxs-lookup"><span data-stu-id="e3461-130">CQRS and DDD patterns describe something inside a single system or component; in this case, something inside a microservice.</span></span>

<span data-ttu-id="e3461-131">不同的限定內容 (BC) 會採用不同的模式。</span><span class="sxs-lookup"><span data-stu-id="e3461-131">Different Bounded Contexts (BCs) will employ different patterns.</span></span> <span data-ttu-id="e3461-132">他們都有著不同的責任，並會導致不同的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e3461-132">They have different responsibilities, and that leads to different solutions.</span></span> <span data-ttu-id="e3461-133">值得強調的是，強制在所有場合下使用相同的模式會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="e3461-133">It is worth emphasizing that forcing the same pattern everywhere leads to failure.</span></span> <span data-ttu-id="e3461-134">請不要在每個地方都使用 CQRS 和 DDD 模式。</span><span class="sxs-lookup"><span data-stu-id="e3461-134">Do not use CQRS and DDD patterns everywhere.</span></span> <span data-ttu-id="e3461-135">許多子系統、 BC 或微服務都更為簡單，並且可使用簡單的 CRUD 服務或使用其他方法來輕鬆的實作。</span><span class="sxs-lookup"><span data-stu-id="e3461-135">Many subsystems, BCs, or microservices are simpler and can be implemented more easily using simple CRUD services or using another approach.</span></span>

<span data-ttu-id="e3461-136">只有一種應用程式架構：您正在設計之系統或端點對端點應用程式的架構 (例如微服務架構)。</span><span class="sxs-lookup"><span data-stu-id="e3461-136">There is only one application architecture: the architecture of the system or end-to-end application you are designing (for example, the microservices architecture).</span></span> <span data-ttu-id="e3461-137">然而，該應用程式中每個限定內容或微服務的設計都會反映其自身的取捨和架構模式層級中的內部設計決策。</span><span class="sxs-lookup"><span data-stu-id="e3461-137">However, the design of each Bounded Context or microservice within that application reflects its own tradeoffs and internal design decisions at an architecture patterns level.</span></span> <span data-ttu-id="e3461-138">請勿嘗試將相同的架構模式，例如 CQRS 或 DDD 套用到所有地方。</span><span class="sxs-lookup"><span data-stu-id="e3461-138">Do not try to apply the same architectural patterns like CQRS or DDD everywhere.</span></span>

####  <a name="additional-resources"></a><span data-ttu-id="e3461-139">其他資源</span><span class="sxs-lookup"><span data-stu-id="e3461-139">Additional resources</span></span>

-   <span data-ttu-id="e3461-140">**Martin Fowler：CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span><span class="sxs-lookup"><span data-stu-id="e3461-140">**Martin Fowler. CQRS**
[*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span></span>

-   <span data-ttu-id="e3461-141">**Greg Young。CQS 與CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span><span class="sxs-lookup"><span data-stu-id="e3461-141">**Greg Young. CQS vs. CQRS**
[*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span></span>

-   <span data-ttu-id="e3461-142">**Greg Young。CQRS Documents**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span><span class="sxs-lookup"><span data-stu-id="e3461-142">**Greg Young. CQRS Documents**
[*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span></span>

-   <span data-ttu-id="e3461-143">**Greg Young。CQRS，以工作為基礎的 UI 和事件來源**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span><span class="sxs-lookup"><span data-stu-id="e3461-143">**Greg Young. CQRS, Task Based UIs and Event Sourcing**
[*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span></span>

-   <span data-ttu-id="e3461-144">**Udi Dahan.已釐清的 CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="e3461-144">**Udi Dahan. Clarified CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="e3461-145">**CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="e3461-145">**CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="e3461-146">**事件來源 (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span><span class="sxs-lookup"><span data-stu-id="e3461-146">**Event-Sourcing (ES)**
[*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e3461-147">[上一頁] (apply-simplified-microservice-cqrs-ddd-patterns.md) [下一頁] (cqrs-microservice-reads.md)</span><span class="sxs-lookup"><span data-stu-id="e3461-147">[Previous] (apply-simplified-microservice-cqrs-ddd-patterns.md) [Next] (cqrs-microservice-reads.md)</span></span>
