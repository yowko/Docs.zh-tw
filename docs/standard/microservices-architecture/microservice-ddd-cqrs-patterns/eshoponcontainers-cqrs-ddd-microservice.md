---
title: "套用 CQRS 和 CQS 中 eShopOnContainers DDD 微服務方法"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |套用 CQRS 和 CQS 中 eShopOnContainers DDD 微服務方法"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a2c4429a75ca47d4fbcde868b95e76bc65ea2bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a><span data-ttu-id="df0c9-104">套用 CQRS 和 CQS 中 eShopOnContainers DDD 微服務方法</span><span class="sxs-lookup"><span data-stu-id="df0c9-104">Applying CQRS and CQS approaches in a DDD microservice in eShopOnContainers</span></span>

<span data-ttu-id="df0c9-105">排序的微服務 eShopOnContainers 參考的應用程式的設計根據 CQRS 原則。</span><span class="sxs-lookup"><span data-stu-id="df0c9-105">The design of the ordering microservice at the eShopOnContainers reference application is based on CQRS principles.</span></span> <span data-ttu-id="df0c9-106">不過，它會使用簡單的方法，其只分隔之命令的查詢，並使用相同的資料庫，這兩個動作的。</span><span class="sxs-lookup"><span data-stu-id="df0c9-106">However, it uses the simplest approach, which is just separating the queries from the commands and using the same database for both actions.</span></span>

<span data-ttu-id="df0c9-107">這些模式，並在這裡，很重要的一點的本質是查詢是等冪： 無論查詢系統時，該系統的狀態的多少次不會變更您甚至還可以使用不同的 「 讀取 」 資料模型比交易的邏輯 「 寫入 」網域模型，雖然排序 microservices 使用相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="df0c9-107">The essence of those patterns, and the important point here, is that queries are idempotent: no matter how many times you query a system, the state of that system will not change You could even use a different “reads” data model than the transactional logic “writes” domain model, although the ordering microservices is using the same database.</span></span> <span data-ttu-id="df0c9-108">因此，這是簡單的 CQRS 方法。</span><span class="sxs-lookup"><span data-stu-id="df0c9-108">Hence this is a simplified CQRS approach.</span></span>

<span data-ttu-id="df0c9-109">相反地，觸發程序的交易和資料更新的命令會將狀態變更系統中。</span><span class="sxs-lookup"><span data-stu-id="df0c9-109">On the other hand, commands, which trigger transactions and data updates, change state in the system.</span></span> <span data-ttu-id="df0c9-110">使用命令，您需要時請小心處理複雜和多變的商務規則。</span><span class="sxs-lookup"><span data-stu-id="df0c9-110">With commands, you need to be careful when dealing with complexity and ever-changing business rules.</span></span> <span data-ttu-id="df0c9-111">這正是您要套用至具有更好的模型化的系統 DDD 技術。</span><span class="sxs-lookup"><span data-stu-id="df0c9-111">This is the where you want to apply DDD techniques to have a better modeled system.</span></span>

<span data-ttu-id="df0c9-112">本指南中的 DDD 模式不應該套用通用。</span><span class="sxs-lookup"><span data-stu-id="df0c9-112">The DDD patterns presented in this guide should not be applied universally.</span></span> <span data-ttu-id="df0c9-113">它們會導致您的設計上的條件約束。</span><span class="sxs-lookup"><span data-stu-id="df0c9-113">They introduce constraints on your design.</span></span> <span data-ttu-id="df0c9-114">這些條件約束提供一段時間，特別是在命令和其他程式碼會修改系統狀態的優點，例如，較高的品質。</span><span class="sxs-lookup"><span data-stu-id="df0c9-114">Those constraints provide benefits such as higher quality over time, especially in commands and other code that modifies system state.</span></span> <span data-ttu-id="df0c9-115">不過，這些條件約束加入較少的優點，進行讀取和查詢資料的複雜性。</span><span class="sxs-lookup"><span data-stu-id="df0c9-115">However, those constraints add complexity with fewer benefits for reading and querying data.</span></span>

<span data-ttu-id="df0c9-116">其中一個這類模式是彙總的模式中，我們更檢查稍後的章節。</span><span class="sxs-lookup"><span data-stu-id="df0c9-116">One such pattern is the Aggregate pattern, which we examine more in later sections.</span></span> <span data-ttu-id="df0c9-117">簡言之，在彙總模式中，您將許多網域物件視為單一單位，因為其網域中的關聯性。</span><span class="sxs-lookup"><span data-stu-id="df0c9-117">Briefly, in the Aggregate pattern, you treat many domain objects as a single unit as a result of their relationship in the domain.</span></span> <span data-ttu-id="df0c9-118">您可能不一定能取得從查詢; 在此模式的優點它可以增加查詢邏輯的複雜度。</span><span class="sxs-lookup"><span data-stu-id="df0c9-118">You might not always gain advantages from this pattern in queries; it can increase the complexity of query logic.</span></span> <span data-ttu-id="df0c9-119">唯讀查詢，未取得多個物件視為單一的彙總的優點。</span><span class="sxs-lookup"><span data-stu-id="df0c9-119">For read-only queries, you do not get the advantages of treating multiple objects as a single Aggregate.</span></span> <span data-ttu-id="df0c9-120">您只能取得複雜性。</span><span class="sxs-lookup"><span data-stu-id="df0c9-120">You only get the complexity.</span></span>

<span data-ttu-id="df0c9-121">如下圖 9-2，本指南建議使用 DDD 模式只能在您的微服務的交易式/更新區域中 （也就觸發命令）。</span><span class="sxs-lookup"><span data-stu-id="df0c9-121">As shown in Figure 9-2, this guide suggests using DDD patterns only in the transactional/updates area of your microservice (that is, as triggered by commands).</span></span> <span data-ttu-id="df0c9-122">查詢可以依照更簡單的方法，而且應該分開之後 CQRS 方法的命令。</span><span class="sxs-lookup"><span data-stu-id="df0c9-122">Queries can follow a simpler approach and should be separated from commands, following a CQRS approach.</span></span>

<span data-ttu-id="df0c9-123">實作 「 查詢端 」，您可以選擇許多方式，從您完全成熟 ORM EF 核心、 AutoMapper 投影、 預存程序、 檢視、 具體化的檢視或微 ORM 等。</span><span class="sxs-lookup"><span data-stu-id="df0c9-123">For implementing the “queries side”, you can choose between many approaches, from your full-blown ORM like EF Core, AutoMapper projections, stored procedures, views, materialized views or a micro ORM.</span></span>

<span data-ttu-id="df0c9-124">本指南中，及我們選擇實作直接查詢使用微 eShopOnContainers （特別是順序微服務） 中，例如 ORM [Dapper](https://github.com/StackExchange/dapper-dot-net)。</span><span class="sxs-lookup"><span data-stu-id="df0c9-124">In this guide and in eShopOnContainers (specifically the ordering microservice) we chose to implement straight queries using a micro ORM like [Dapper](https://github.com/StackExchange/dapper-dot-net).</span></span> <span data-ttu-id="df0c9-125">這可讓您實作任何 SQL 陳述式，以取得最佳效能，這點受惠非常少的額外負荷的淺架構為基礎的查詢。</span><span class="sxs-lookup"><span data-stu-id="df0c9-125">This lets you implement any query based on SQL statements to get the best performance, thanks to a light framework with very little overhead.</span></span>

<span data-ttu-id="df0c9-126">請注意，當您使用這個方法時，實體保存至 SQL 資料庫的方式會影響的任何更新您的模型也需要個別更新 Dapper 或任何其他個別 (非 EF) 方法來查詢所使用的 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="df0c9-126">Note that when you use this approach, any updates to your model that impact how entities are persisted to a SQL database also need separate updates to SQL queries used by Dapper or any other separate (non-EF) approaches to querying.</span></span>

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a><span data-ttu-id="df0c9-127">CQRS 和 DDD 模式不是最上層的架構</span><span class="sxs-lookup"><span data-stu-id="df0c9-127">CQRS and DDD patterns are not top-level architectures</span></span>

<span data-ttu-id="df0c9-128">它一定要了解該 CQRS 和大部分 DDD 模式 （例如 DDD 層級或領域模型搭配彙總） 不是架構的樣式，而只是架構模式。</span><span class="sxs-lookup"><span data-stu-id="df0c9-128">It important to understand that CQRS and most DDD patterns (like DDD layers or a domain model with aggregates) are not architectural styles, but only architecture patterns.</span></span> <span data-ttu-id="df0c9-129">Microservices、 SOA 和事件驅動的架構 (EDA) 是的範例架構的樣式。</span><span class="sxs-lookup"><span data-stu-id="df0c9-129">Microservices, SOA, and event-driven architecture (EDA) are examples of architectural styles.</span></span> <span data-ttu-id="df0c9-130">這些主題說明許多元件，例如許多 microservices 系統。</span><span class="sxs-lookup"><span data-stu-id="df0c9-130">They describe a system of many components, such as many microservices.</span></span> <span data-ttu-id="df0c9-131">CQRS 和 DDD 模式描述的項目在單一系統或元件。在此情況下，項目內的微服務。</span><span class="sxs-lookup"><span data-stu-id="df0c9-131">CQRS and DDD patterns describe something inside a single system or component; in this case, something inside a microservice.</span></span>

<span data-ttu-id="df0c9-132">不同的繫結內容 (BCs) 會採用不同的模式。</span><span class="sxs-lookup"><span data-stu-id="df0c9-132">Different Bounded Contexts (BCs) will employ different patterns.</span></span> <span data-ttu-id="df0c9-133">它們有不同的責任，並會導致不同的解決方案。</span><span class="sxs-lookup"><span data-stu-id="df0c9-133">They have different responsibilities, and that leads to different solutions.</span></span> <span data-ttu-id="df0c9-134">值得強調的強制執行相同的模式，每個地方會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="df0c9-134">It is worth emphasizing that forcing the same pattern everywhere leads to failure.</span></span> <span data-ttu-id="df0c9-135">請勿 everywhere 使用 CQRS 和 DDD 模式。</span><span class="sxs-lookup"><span data-stu-id="df0c9-135">Do not use CQRS and DDD patterns everywhere.</span></span> <span data-ttu-id="df0c9-136">許多子系統、 BCs 或 microservices 更簡單，可以更輕鬆地使用簡單的 CRUD 服務，或使用另一種方法實作。</span><span class="sxs-lookup"><span data-stu-id="df0c9-136">Many subsystems, BCs, or microservices are simpler and can be implemented more easily using simple CRUD services or using another approach.</span></span>

<span data-ttu-id="df0c9-137">沒有一個應用程式架構： 您要設計的系統或端對端應用程式架構 （例如 microservices 架構）。</span><span class="sxs-lookup"><span data-stu-id="df0c9-137">There is only one application architecture: the architecture of the system or end-to-end application you are designing (for example, the microservices architecture).</span></span> <span data-ttu-id="df0c9-138">不過，每個繫結內容 」 或 「 微服務該應用程式中的設計會反映其本身的權衡取捨完全和架構模式層級的內部的設計決策。</span><span class="sxs-lookup"><span data-stu-id="df0c9-138">However, the design of each Bounded Context or microservice within that application reflects its own tradeoffs and internal design decisions at an architecture patterns level.</span></span> <span data-ttu-id="df0c9-139">請勿嘗試套用相同的架構模式 CQRS 或 DDD 等位置。</span><span class="sxs-lookup"><span data-stu-id="df0c9-139">Do not try to apply the same architectural patterns like CQRS or DDD everywhere.</span></span>

####  <a name="additional-resources"></a><span data-ttu-id="df0c9-140">其他資源</span><span class="sxs-lookup"><span data-stu-id="df0c9-140">Additional resources</span></span>

-   <span data-ttu-id="df0c9-141">**Martin Fowler：CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span><span class="sxs-lookup"><span data-stu-id="df0c9-141">**Martin Fowler. CQRS**
[*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span></span>

-   <span data-ttu-id="df0c9-142">**Greg Young。CQS vs。CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span><span class="sxs-lookup"><span data-stu-id="df0c9-142">**Greg Young. CQS vs. CQRS**
[*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span></span>

-   <span data-ttu-id="df0c9-143">**Greg Young。CQRS 文件**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span><span class="sxs-lookup"><span data-stu-id="df0c9-143">**Greg Young. CQRS Documents**
[*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span></span>

-   <span data-ttu-id="df0c9-144">**Greg Young。CQRS，工作基礎的 Ui 和事件來源**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span><span class="sxs-lookup"><span data-stu-id="df0c9-144">**Greg Young. CQRS, Task Based UIs and Event Sourcing**
[*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span></span>

-   <span data-ttu-id="df0c9-145">**Udi Dahan。已釐清 CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="df0c9-145">**Udi Dahan. Clarified CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="df0c9-146">**CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="df0c9-146">**CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="df0c9-147">**事件來源 (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span><span class="sxs-lookup"><span data-stu-id="df0c9-147">**Event-Sourcing (ES)**
[*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="df0c9-148">[上一個](apply-simplified-microservice-cqrs-ddd-patterns.md) [下一步] (cqrs-微服務-reads.md)</span><span class="sxs-lookup"><span data-stu-id="df0c9-148">[Previous] (apply-simplified-microservice-cqrs-ddd-patterns.md) [Next] (cqrs-microservice-reads.md)</span></span>
