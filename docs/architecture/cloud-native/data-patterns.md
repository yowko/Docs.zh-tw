---
title: 雲端原生資料模式
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生資料模式
ms.date: 06/30/2019
ms.openlocfilehash: 8fc5a09dca61e6644fdcaa692ff1a21f40ebf179
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183410"
---
# <a name="cloud-native-data-patterns"></a><span data-ttu-id="d14fb-103">雲端原生資料模式</span><span class="sxs-lookup"><span data-stu-id="d14fb-103">Cloud-native data patterns</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d14fb-104">雖然分散的資料可能會導致效能、擴充性和節省成本，但也會帶來許多挑戰。</span><span class="sxs-lookup"><span data-stu-id="d14fb-104">While decentralized data can lead to improved performance, scalability, and cost savings, it also presents many challenges.</span></span> <span data-ttu-id="d14fb-105">跨微服務查詢資料是很複雜的。</span><span class="sxs-lookup"><span data-stu-id="d14fb-105">Querying for data across microservices is complex.</span></span> <span data-ttu-id="d14fb-106">跨微服務的交易必須以程式設計方式管理，因為雲端原生應用程式中不支援分散式交易。</span><span class="sxs-lookup"><span data-stu-id="d14fb-106">A transaction that spans microservices must be managed programmatically as distributed transactions aren't supported in cloud-native applications.</span></span> <span data-ttu-id="d14fb-107">您可以從*立即一致性*的世界轉移到*最終一致性*。</span><span class="sxs-lookup"><span data-stu-id="d14fb-107">You  move from a world of *immediate consistency* to *eventual consistency*.</span></span>

<span data-ttu-id="d14fb-108">我們現在會討論這些挑戰。</span><span class="sxs-lookup"><span data-stu-id="d14fb-108">We discuss these challenges now.</span></span>

## <a name="cross-service-queries"></a><span data-ttu-id="d14fb-109">跨服務查詢</span><span class="sxs-lookup"><span data-stu-id="d14fb-109">Cross-service queries</span></span>

<span data-ttu-id="d14fb-110">應用程式如何查詢分散到多個獨立微服務的資料？</span><span class="sxs-lookup"><span data-stu-id="d14fb-110">How does an application query data that is spread across many independent microservices?</span></span>

<span data-ttu-id="d14fb-111">圖5-4 顯示這種情況。</span><span class="sxs-lookup"><span data-stu-id="d14fb-111">Figure 5-4 shows this scenario.</span></span>

![跨微服務查詢](./media/cross-service-query.png)

<span data-ttu-id="d14fb-113">**圖 5-4**。</span><span class="sxs-lookup"><span data-stu-id="d14fb-113">**Figure 5-4**.</span></span> <span data-ttu-id="d14fb-114">跨微服務查詢</span><span class="sxs-lookup"><span data-stu-id="d14fb-114">Querying across microservices</span></span>

<span data-ttu-id="d14fb-115">請注意，在上圖中，我們會看到 [購物籃] 微服務，將專案新增至使用者的購物車。</span><span class="sxs-lookup"><span data-stu-id="d14fb-115">Note how in the previous figure we see a shopping basket microservice that adds an item to a user's shopping cart.</span></span> <span data-ttu-id="d14fb-116">雖然購物籃的資料存放區包含購物籃和 lineItem 資料表，但它不包含產品或定價資料，因為在產品和價格微服務中找到這些專案。</span><span class="sxs-lookup"><span data-stu-id="d14fb-116">While the shopping basket's data store contains a basket and lineItem table, it doesn't contain product or pricing data as those items are found in the product and price microservices.</span></span> <span data-ttu-id="d14fb-117">若要新增專案，購物籃微服務需要產品資料和定價資料。</span><span class="sxs-lookup"><span data-stu-id="d14fb-117">To add an item, the shopping basket microservice needs product data and pricing data.</span></span> <span data-ttu-id="d14fb-118">取得產品和定價資料的選項有哪些？</span><span class="sxs-lookup"><span data-stu-id="d14fb-118">What are options to obtain the product and pricing data?</span></span>

<span data-ttu-id="d14fb-119">圖5-5 顯示購物籃微服務對產品目錄和定價微服務進行直接的 HTTP 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d14fb-119">Figure 5-5 shows the shopping basket microservice making a direct HTTP call to both the product catalog and pricing microservices.</span></span>

![直接 HTTP 通訊](./media/direct-http-communication.png)

<span data-ttu-id="d14fb-121">**圖 5-5**。</span><span class="sxs-lookup"><span data-stu-id="d14fb-121">**Figure 5-5**.</span></span> <span data-ttu-id="d14fb-122">直接 HTTP 通訊</span><span class="sxs-lookup"><span data-stu-id="d14fb-122">Direct HTTP communication</span></span>

<span data-ttu-id="d14fb-123">雖然可以實現，但在第4章中，我們討論了如何在微服務之間進行 HTTP 呼叫，而不是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="d14fb-123">While feasible to implement, in chapter 4 we discussed how direct HTTP calls across microservices couple the system and aren't considered a good practice.</span></span>

<span data-ttu-id="d14fb-124">我們可以執行如圖5-6 所示的匯總工具微服務。</span><span class="sxs-lookup"><span data-stu-id="d14fb-124">We could implement an aggregator microservice shown in Figure 5-6.</span></span>

![匯總工具微服務](./media/aggregator-microservice.png)

<span data-ttu-id="d14fb-126">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="d14fb-126">**Figure 5-6.**</span></span> <span data-ttu-id="d14fb-127">匯總工具微服務</span><span class="sxs-lookup"><span data-stu-id="d14fb-127">Aggregator microservice</span></span>

<span data-ttu-id="d14fb-128">雖然這種方法會在個別微服務中封裝商務作業工作流程，但它會增加複雜性，而且仍然會產生直接的 HTTP 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d14fb-128">While this approach encapsulates the business operation workflow in an individual microservice, it adds complexity and still results in direct HTTP calls.</span></span>

<span data-ttu-id="d14fb-129">執行跨服務查詢的常見方法是使用[具體化視圖模式](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)，如圖5-7 所示。</span><span class="sxs-lookup"><span data-stu-id="d14fb-129">A common approach for executing cross-service queries uses the [Materialized View Pattern](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), shown in Figure 5-7.</span></span>

![具體化視圖模式](./media/materialized-view-pattern.png)

<span data-ttu-id="d14fb-131">**Figure5-7**。</span><span class="sxs-lookup"><span data-stu-id="d14fb-131">**Figure5-7**.</span></span> <span data-ttu-id="d14fb-132">具體化視圖模式</span><span class="sxs-lookup"><span data-stu-id="d14fb-132">Materialized View Pattern</span></span>

<span data-ttu-id="d14fb-133">使用此模式時，您可以直接將本機資料表（稱為「*讀取模型*」）放在「購物籃」服務中，其中包含「產品」和「定價微服務所需之資料的反正規化複本。</span><span class="sxs-lookup"><span data-stu-id="d14fb-133">With this pattern, you directly place a local table (known as a *read model*) in the shopping basket service that contains a denormalized copy of the data that is needed from the product and pricing microservices.</span></span> <span data-ttu-id="d14fb-134">將該資料放在 [購物籃] 微服務中，就不需要叫用昂貴的跨服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="d14fb-134">Placing that data inside the shopping basket microservice eliminates the need for invoking expensive cross-service calls.</span></span> <span data-ttu-id="d14fb-135">在服務的本機資料中，您可以改善回應時間和可靠性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-135">With the data local to the service, you improve response time and reliability.</span></span>

<span data-ttu-id="d14fb-136">這種方法的 catch 是您的系統中現在有重複的資料。</span><span class="sxs-lookup"><span data-stu-id="d14fb-136">The catch with this approach is you now have duplicate data in your system.</span></span> <span data-ttu-id="d14fb-137">在雲端原生系統中，重複的資料不會被視為[反模式](https://en.wikipedia.org/wiki/Anti-pattern)，而且通常會在雲端原生系統中執行。</span><span class="sxs-lookup"><span data-stu-id="d14fb-137">In cloud-native systems, duplicate data isn't considered an [anti-pattern](https://en.wikipedia.org/wiki/Anti-pattern) and is commonly implemented in cloud-native systems.</span></span> <span data-ttu-id="d14fb-138">不過，只有一個系統可以是任何資料集的擁有者，而且您必須針對記錄的系統執行同步處理機制，以便在每次變更基礎資料時，更新所有相關聯的讀取模型。</span><span class="sxs-lookup"><span data-stu-id="d14fb-138">However, one and only one system can be the owner of any dataset, and you'll need to implement a synchronization mechanism for the system of record to update all of the associated read models, whenever a change to its underlying data occurs.</span></span>

## <a name="transactional-support"></a><span data-ttu-id="d14fb-139">交易式支援</span><span class="sxs-lookup"><span data-stu-id="d14fb-139">Transactional support</span></span>

<span data-ttu-id="d14fb-140">雖然跨微服務的查詢很具挑戰性，但跨微服務執行交易可能會很複雜。</span><span class="sxs-lookup"><span data-stu-id="d14fb-140">While queries across microservices are challenging, implementing a transaction across microservices can be complex.</span></span> <span data-ttu-id="d14fb-141">維護位於不同微服務之資料來源間資料一致性的固有挑戰，無法 understated。</span><span class="sxs-lookup"><span data-stu-id="d14fb-141">The inherent challenge of maintaining data consistency across data sources that reside in different microservices can't be understated.</span></span> <span data-ttu-id="d14fb-142">圖5-8 顯示問題。</span><span class="sxs-lookup"><span data-stu-id="d14fb-142">Figure 5-8 shows the problem.</span></span>

![Saga 模式中的交易](./media/saga-transaction-operation.png)

<span data-ttu-id="d14fb-144">**圖 5-8**。</span><span class="sxs-lookup"><span data-stu-id="d14fb-144">**Figure 5-8**.</span></span> <span data-ttu-id="d14fb-145">跨微服務執行交易</span><span class="sxs-lookup"><span data-stu-id="d14fb-145">Implementing a transaction across microservices</span></span>

<span data-ttu-id="d14fb-146">請注意上圖中的五個獨立微服務如何參與分散式的「*建立訂單*」交易。</span><span class="sxs-lookup"><span data-stu-id="d14fb-146">Note how in the previous figure five independent microservices all participate in a distributed *Create Order* transaction.</span></span> <span data-ttu-id="d14fb-147">不過，五個個別微服務的每個都必須成功，或全部都必須中止和復原作業。</span><span class="sxs-lookup"><span data-stu-id="d14fb-147">However, the transaction for each of the five individual microservices must succeed, or all must abort and roll-back the operation.</span></span> <span data-ttu-id="d14fb-148">雖然內建交易支援在每個微服務中都有提供，但並不支援這五個服務中的分散式交易。</span><span class="sxs-lookup"><span data-stu-id="d14fb-148">While built-in transactional support is available inside each of the microservices, there's no support for a distributed transaction across all five services.</span></span>

<span data-ttu-id="d14fb-149">由於交易式支援對於這項作業而言是不可或缺的，因此在每個微服務中保持資料一致，您必須以程式設計方式建立分散式交易。</span><span class="sxs-lookup"><span data-stu-id="d14fb-149">Since transactional support is essential for this operation to keep the data consistent in each of the microservices, you have to programmatically construct a distributed transaction.</span></span>

<span data-ttu-id="d14fb-150">以程式設計方式加入交易式支援的常用模式是[Saga 模式](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)。</span><span class="sxs-lookup"><span data-stu-id="d14fb-150">A popular pattern for programmatically adding transactional support is the [Saga pattern](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/).</span></span> <span data-ttu-id="d14fb-151">其執行方式是將本機交易分組在一起，並依序叫用每一個。</span><span class="sxs-lookup"><span data-stu-id="d14fb-151">It's implemented by grouping local transactions together and sequentially invoking each one.</span></span> <span data-ttu-id="d14fb-152">如果本機交易失敗，Saga 會中止作業，並叫用一組[補償交易](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)來復原前一個本機交易所做的變更。</span><span class="sxs-lookup"><span data-stu-id="d14fb-152">If a local transaction fails, the Saga aborts the operation and invokes a set of [compensating transactions](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction) to undo the changes made by the preceding local transactions.</span></span> <span data-ttu-id="d14fb-153">圖5-9 顯示具有 Saga 模式的失敗交易。</span><span class="sxs-lookup"><span data-stu-id="d14fb-153">Figure 5-9 shows a failed transaction with the Saga pattern.</span></span>

![在 saga 模式中復原](./media/saga-rollback-operation.png)

<span data-ttu-id="d14fb-155">**圖 5-9**。</span><span class="sxs-lookup"><span data-stu-id="d14fb-155">**Figure 5-9**.</span></span> <span data-ttu-id="d14fb-156">復原交易</span><span class="sxs-lookup"><span data-stu-id="d14fb-156">Rolling back a transaction</span></span>

<span data-ttu-id="d14fb-157">請注意上圖中的*GenerateContent*作業在 [音樂] 微服務中失敗的情況。</span><span class="sxs-lookup"><span data-stu-id="d14fb-157">Note how in the previous figure the *GenerateContent* operation has failed in the music microservice.</span></span> <span data-ttu-id="d14fb-158">Saga 會叫用補償交易（以紅色表示）以移除內容、取消付款並取消訂單，並將每個微服務的資料傳回一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="d14fb-158">The Saga invokes compensating transactions (in red) to remove the content, cancel the payment, and cancel the order, returning the data for each microservice back to a consistent state.</span></span>

<span data-ttu-id="d14fb-159">Saga 模式通常會單純為一系列相關的事件，或協調成一組相關的命令。</span><span class="sxs-lookup"><span data-stu-id="d14fb-159">Saga patterns are typically choreographed as a series of related events or orchestrated as a set of related commands.</span></span>

## <a name="cqrs-pattern"></a><span data-ttu-id="d14fb-160">CQRS 模式</span><span class="sxs-lookup"><span data-stu-id="d14fb-160">CQRS pattern</span></span>

<span data-ttu-id="d14fb-161">CQRS 或[命令與查詢責任隔離](https://docs.microsoft.com/azure/architecture/patterns/cqrs)是一種架構模式，可將讀取資料的作業與寫入資料的工作分開。</span><span class="sxs-lookup"><span data-stu-id="d14fb-161">CQRS, or [Command and Query Responsibility Segregation](https://docs.microsoft.com/azure/architecture/patterns/cqrs), is an architectural pattern that separate operations that read data from those that write data.</span></span> <span data-ttu-id="d14fb-162">此模式可協助最大化效能、擴充性和安全性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-162">This pattern can help maximize performance, scalability, and security.</span></span>

<span data-ttu-id="d14fb-163">在一般的資料存取案例中，您會執行單一模型（實體和儲存機制物件），*以執行讀取*和寫入資料作業。</span><span class="sxs-lookup"><span data-stu-id="d14fb-163">In normal data access scenarios, you implement a single model (entity and repository object) that perform *both* read and write data operations.</span></span>

<span data-ttu-id="d14fb-164">不過，更先進的資料存取案例可能受益于不同的模型，以及用於讀取和寫入的資料表。</span><span class="sxs-lookup"><span data-stu-id="d14fb-164">However, a more advanced data access scenario might benefit from separate models and data tables for reads and writes.</span></span> <span data-ttu-id="d14fb-165">為了改善效能，讀取作業（稱為「*查詢*」）可能會查詢資料的高度反正規化標記法，以避免產生昂貴的重複性資料表聯結。</span><span class="sxs-lookup"><span data-stu-id="d14fb-165">To improve performance, the read operation, known as a *query*, might query against a highly denormalized representation of the data to avoid expensive repetitive table joins.</span></span> <span data-ttu-id="d14fb-166">雖然*寫入*作業（也稱為*命令*）可能會針對資料的完全正規化表示進行更新。</span><span class="sxs-lookup"><span data-stu-id="d14fb-166">Whereas the *write* operation, known as a *command*, might update against a fully normalized representation of the data.</span></span> <span data-ttu-id="d14fb-167">接著，您必須執行機制，讓這兩種標記法保持同步。一般來說，每當修改寫入資料表時，就會引發事件，將資料修改複寫到讀取資料表。</span><span class="sxs-lookup"><span data-stu-id="d14fb-167">You would then need to implement a mechanism to keep both representations in sync. Typically, whenever the write table is modified, it raises an event that replicates the data modification to the read table.</span></span>

<span data-ttu-id="d14fb-168">圖5-10 顯示 CQRS 模式的執行。</span><span class="sxs-lookup"><span data-stu-id="d14fb-168">Figure 5-10 shows an implementation of the CQRS pattern.</span></span>

![CQRS 執行](./media/cqrs-implementation.png)

<span data-ttu-id="d14fb-170">**圖 5-10**。</span><span class="sxs-lookup"><span data-stu-id="d14fb-170">**Figure 5-10**.</span></span> <span data-ttu-id="d14fb-171">CQRS 執行</span><span class="sxs-lookup"><span data-stu-id="d14fb-171">CQRS implementation</span></span>

<span data-ttu-id="d14fb-172">請注意上圖中如何執行個別的命令和查詢模型。</span><span class="sxs-lookup"><span data-stu-id="d14fb-172">Note how in the previous figure separate command and query models are implemented.</span></span> <span data-ttu-id="d14fb-173">此外，每個資料寫入作業都會儲存到寫入存放區，然後傳播到讀取存放區。</span><span class="sxs-lookup"><span data-stu-id="d14fb-173">Moreover, each data write operation is saved to the write store and then propagated to the read store.</span></span> <span data-ttu-id="d14fb-174">請密切注意傳播程式如何在[最終一致性](https://www.cloudcomputingpatterns.org/eventual_consistency/)原則上運作，而讀取模型最終會與寫入模型進行同步處理，但進程中可能會有一些延遲。</span><span class="sxs-lookup"><span data-stu-id="d14fb-174">Pay close attention to how the propagation process operates on the principle of [eventual consistency](https://www.cloudcomputingpatterns.org/eventual_consistency/), whereas the read model eventually synchronizes with the write model, but there may be some lag in the process.</span></span>

<span data-ttu-id="d14fb-175">藉由執行分隔，您可以個別調整讀取和寫入的能力。</span><span class="sxs-lookup"><span data-stu-id="d14fb-175">By implementing separation, you have the ability to scale reads and writes separately.</span></span> <span data-ttu-id="d14fb-176">同樣地，您可能會對寫入作業施加更緊密的安全性，而不是讀取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d14fb-176">As well, you might impose tighter security on write operations than those concerning reads.</span></span>

<span data-ttu-id="d14fb-177">根據特定需求，CQRS 模式通常會套用至系統的有限區段。</span><span class="sxs-lookup"><span data-stu-id="d14fb-177">Typically, CQRS patterns are applied to limited sections of your system based upon specific needs.</span></span>

## <a name="relational-vs-nosql"></a><span data-ttu-id="d14fb-178">關聯式與 NoSQL</span><span class="sxs-lookup"><span data-stu-id="d14fb-178">Relational vs NoSQL</span></span>

<span data-ttu-id="d14fb-179">[NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/)技術的影響無法十分出色，特別是針對分散式雲端原生系統。</span><span class="sxs-lookup"><span data-stu-id="d14fb-179">The impact of [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) technologies can't be overstated, especially for distributed cloud-native systems.</span></span> <span data-ttu-id="d14fb-180">這個空間中的新資料技術激增，有一次只依賴關係資料庫而中斷的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d14fb-180">The proliferation of new data technologies in this space has disrupted solutions that once exclusively relied on relational databases.</span></span>

<span data-ttu-id="d14fb-181">一側，關係資料庫在數十年已經是一項普遍的技術。</span><span class="sxs-lookup"><span data-stu-id="d14fb-181">On the one side, relational databases have been a prevalent technology for decades.</span></span> <span data-ttu-id="d14fb-182">這些是成熟、經過證明且廣泛實行的。</span><span class="sxs-lookup"><span data-stu-id="d14fb-182">They're mature, proven, and widely implemented.</span></span> <span data-ttu-id="d14fb-183">競爭資料庫產品、專業知識和工具 abounds。</span><span class="sxs-lookup"><span data-stu-id="d14fb-183">Competing database products, expertise and tooling abounds.</span></span> <span data-ttu-id="d14fb-184">關係資料庫會提供相關資料表的存放區。</span><span class="sxs-lookup"><span data-stu-id="d14fb-184">Relational databases provide a store of related data tables.</span></span> <span data-ttu-id="d14fb-185">這些資料表具有固定的架構，使用 SQL （結構化查詢語言 (SQL)）來管理資料，並具有[ACID](https://www.geeksforgeeks.org/acid-properties-in-dbms/) （也稱為不可部分完成性、一致性、隔離和耐久性）保證。</span><span class="sxs-lookup"><span data-stu-id="d14fb-185">These tables have a fixed schema, use SQL (Structured Query Language) to manage data and have [ACID](https://www.geeksforgeeks.org/acid-properties-in-dbms/) (also known as Atomicity, Consistency, Isolation, and Durability) guarantees.</span></span>

<span data-ttu-id="d14fb-186">另一方面，非 SQL 資料庫則是指高效能、非關聯式資料存放區。</span><span class="sxs-lookup"><span data-stu-id="d14fb-186">No-SQL databases, on the other side, refer to high-performance, non-relational data stores.</span></span> <span data-ttu-id="d14fb-187">他們在 excel 中使用易用性、擴充性、彈性和可用性等特性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-187">They excel in their ease-of-use, scalability, resilience, and availability characteristics.</span></span> <span data-ttu-id="d14fb-188">NoSQL 會將自我描述（無架構）資料儲存在 JSON 檔中，而不是聯結正規化資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="d14fb-188">Instead of joining tables of normalized data, NoSQL stores self-describing (schemaless) data typically in JSON documents.</span></span> <span data-ttu-id="d14fb-189">它們不提供[ACID](https://www.geeksforgeeks.org/acid-properties-in-dbms/)保證。</span><span class="sxs-lookup"><span data-stu-id="d14fb-189">They don't offer [ACID](https://www.geeksforgeeks.org/acid-properties-in-dbms/) guarantees.</span></span>

<span data-ttu-id="d14fb-190">如需瞭解這些資料庫類型之間差異的方法，請參閱[CAP 定理](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e)，這是一組可套用至儲存狀態之分散式系統的原則。</span><span class="sxs-lookup"><span data-stu-id="d14fb-190">A way to understand the differences between these types of databases can be found in the [CAP theorem](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e), a set of principles that can be applied to distributed systems that store state.</span></span> <span data-ttu-id="d14fb-191">圖5-11 顯示 CAP 定理的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-191">Figure 5-11 shows the three properties of the CAP theorem.</span></span>

![CAP 定理](./media/cap-theorem.png)

<span data-ttu-id="d14fb-193">**圖 5-11**。</span><span class="sxs-lookup"><span data-stu-id="d14fb-193">**Figure 5-11**.</span></span> <span data-ttu-id="d14fb-194">CAP 定理</span><span class="sxs-lookup"><span data-stu-id="d14fb-194">The CAP theorem</span></span>

<span data-ttu-id="d14fb-195">定理說明任何分散式資料系統都能在一致性、可用性及分割區容錯之間提供取捨，而且任何資料庫只能保證三個屬性的其中兩個：</span><span class="sxs-lookup"><span data-stu-id="d14fb-195">The theorem states that any distributed data system will offer a trade-off between consistency, availability, and partition tolerance, and that any database can only guarantee two of the three properties:</span></span>

- <span data-ttu-id="d14fb-196">*一致性*：叢集中的每個節點都會回應最新的資料，即使它需要封鎖要求，直到所有複本都已正確更新為止。</span><span class="sxs-lookup"><span data-stu-id="d14fb-196">*Consistency*: every node in the cluster will respond with the most recent data, even if it requires blocking a request until all replicas are correctly updated.</span></span>

- <span data-ttu-id="d14fb-197">*可用性*：每個節點都會在合理的時間內傳迴響應，即使該回應不是最新的資料也一樣。</span><span class="sxs-lookup"><span data-stu-id="d14fb-197">*Availability*: every node will return a response in a reasonable amount of time, even if that response isn't the most recent data.</span></span>

- <span data-ttu-id="d14fb-198">*分割區容錯*：保證如果節點失敗或失去與其他節點的連線，系統將會繼續運作。</span><span class="sxs-lookup"><span data-stu-id="d14fb-198">*Partition Tolerance*: guarantees that the system will continue operating if a node fails or loses connectivity with another.</span></span>

<span data-ttu-id="d14fb-199">關係資料庫呈現一致性和可用性，但不會顯示分割區容錯。</span><span class="sxs-lookup"><span data-stu-id="d14fb-199">Relational databases exhibit consistency and availability, but not partition tolerance.</span></span> <span data-ttu-id="d14fb-200">分割關係資料庫（例如分區化）很艱難，而且可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="d14fb-200">Partitioning a relational database, such as sharding, is difficult and can impact performance.</span></span>

<span data-ttu-id="d14fb-201">另一方面，NoSQL 資料庫通常會展現資料分割容錯，又稱為水準擴充性和高可用性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-201">On the other hand, NoSQL databases typically exhibit partition tolerance, known as horizontal scalability, and high availability.</span></span> <span data-ttu-id="d14fb-202">當 CAP 定理指定時，您只能有三個原則中的兩個，而您會遺失一致性屬性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-202">As the CAP theorem specifies, you can only have two of the three principles, and you lose the  consistency property.</span></span>

<span data-ttu-id="d14fb-203">NoSQL 資料庫會散佈在不同的商用伺服器上，而且通常會相應放大。</span><span class="sxs-lookup"><span data-stu-id="d14fb-203">NoSQL databases are distributed and commonly scaled out across commodity servers.</span></span> <span data-ttu-id="d14fb-204">這麼做可以降低成本，同時在地理區域內外提供絕佳的可用性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-204">Doing so can provide great availability, both within and across geographical regions at a reduced cost.</span></span> <span data-ttu-id="d14fb-205">資料可以在這些機器或節點之間進行分割和複寫，以提供冗余和容錯功能。</span><span class="sxs-lookup"><span data-stu-id="d14fb-205">Data can be partitioned and replicated across these machines, or nodes, providing redundancy and fault tolerance.</span></span> <span data-ttu-id="d14fb-206">缺點是一致的。</span><span class="sxs-lookup"><span data-stu-id="d14fb-206">The downside is consistency.</span></span> <span data-ttu-id="d14fb-207">對某個 NoSQL 節點上的資料所做的變更，可能需要一些時間才能傳播至其他節點。</span><span class="sxs-lookup"><span data-stu-id="d14fb-207">A change to data on one NoSQL node can take some time to propagate to other nodes.</span></span> <span data-ttu-id="d14fb-208">一般來說，即使呈現的資料已過時而且尚未更新，NoSQL 資料庫節點還是會立即對查詢提供回應。</span><span class="sxs-lookup"><span data-stu-id="d14fb-208">Typically, a NoSQL database node will provide an immediate response to a query, even if the data that it is presenting is stale and has not been updated yet.</span></span>

<span data-ttu-id="d14fb-209">這是已知的[最終一致性](https://www.cloudcomputingpatterns.org/eventual_consistency/)，也就是不支援 ACID 交易的分散式資料系統特性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-209">This is known [eventual consistency](https://www.cloudcomputingpatterns.org/eventual_consistency/), a characteristic of distributed data systems where ACID transactions aren't supported.</span></span> <span data-ttu-id="d14fb-210">資料項目目的更新和將該更新傳播到每個複本節點所需的時間之間，會有短暫的延遲。</span><span class="sxs-lookup"><span data-stu-id="d14fb-210">It's a brief delay between the update of a data item and time that it takes to propagate that update to each of the replica nodes.</span></span> <span data-ttu-id="d14fb-211">如果您在美國的 NoSQL 資料庫中更新產品專案，但同時從歐洲的複本節點查詢該相同資料項目，您可能會抓取先前的產品資訊-直到歐洲節點已更新產品變更為止。</span><span class="sxs-lookup"><span data-stu-id="d14fb-211">If you update a product item in a NoSQL database in the United States, but at same time query that same data item from a replica node in Europe, you might retrieve the earlier product information - until the European node has been updated with product change.</span></span> <span data-ttu-id="d14fb-212">取捨是藉由提供[強式一致性](https://en.wikipedia.org/wiki/Strong_consistency)，等待所有複本節點更新後，再傳回查詢結果，您可以支援龐大的規模和流量，但可能會呈現較舊的資料。</span><span class="sxs-lookup"><span data-stu-id="d14fb-212">The trade-off is that by giving up [strong consistency](https://en.wikipedia.org/wiki/Strong_consistency),  waiting for all replica nodes to update before returning a query result, you can support enormous scale and traffic volume, but with the possibility of presenting older data.</span></span>

<span data-ttu-id="d14fb-213">NoSQL 資料庫可透過下列四個模型來分類：</span><span class="sxs-lookup"><span data-stu-id="d14fb-213">NoSQL databases can be categorized by the following four models:</span></span> 

- <span data-ttu-id="d14fb-214">*檔存放區*（MongoDB、CouchDB、Couchbase）：資料（和對應的中繼資料）會在資料庫內以不正規化 JSON 為基礎的檔中儲存非 relationally。</span><span class="sxs-lookup"><span data-stu-id="d14fb-214">*Document Store* (MongoDB, CouchDB, Couchbase): data (and corresponding metadata) is stored non-relationally in denormalized JSON-based documents inside the database.</span></span>

- <span data-ttu-id="d14fb-215">索引*鍵/值存放區*（Redis，Riak，memcached）：資料會儲存為簡單的索引鍵/值組，並針對對應至使用者資料值的唯一存取金鑰來執行系統作業。</span><span class="sxs-lookup"><span data-stu-id="d14fb-215">*Key/Value Store* (Redis, Riak, memcached): data is stored in simple key-value pairs with system operations performed against a unique access key that is mapped to a value of user data.</span></span>

- <span data-ttu-id="d14fb-216">*寬資料行存放區*（HBase，Cassandra）：相關資料會以單欄式格式儲存為單一資料行中的一組嵌套索引鍵/值組，其中資料通常會以單一單位的形式抓取，而不需要將多個資料表聯結在一起。</span><span class="sxs-lookup"><span data-stu-id="d14fb-216">*Wide-Column Store* (HBase, Cassandra): related Data is stored in a columnar format as a set of nested-key/value pairs within a single column with data typically retrieved as a single unit without having to join multiple tables together.</span></span>

- <span data-ttu-id="d14fb-217">*圖形商店*（neo4j，titan）：資料會儲存為節點內的圖形表示，以及指定節點之間關聯性的邊緣。</span><span class="sxs-lookup"><span data-stu-id="d14fb-217">*Graph stores* (neo4j, titan): data is stored as a graphical representation within a node along with edges that specify the relationship between the nodes.</span></span>

<span data-ttu-id="d14fb-218">NoSQL 資料庫可以優化來處理大規模的資料，特別是當資料相當簡單時。</span><span class="sxs-lookup"><span data-stu-id="d14fb-218">NoSQL databases can be optimized to deal with large-scale data, especially when the data is relatively simple.</span></span> <span data-ttu-id="d14fb-219">當下列情況時，請考慮 NoSQL 資料庫：</span><span class="sxs-lookup"><span data-stu-id="d14fb-219">Consider a NoSQL database when:</span></span>

- <span data-ttu-id="d14fb-220">您的工作負載需要大規模和高並行。</span><span class="sxs-lookup"><span data-stu-id="d14fb-220">Your workload requires large-scale and high-concurrency.</span></span>
- <span data-ttu-id="d14fb-221">您有大量的使用者。</span><span class="sxs-lookup"><span data-stu-id="d14fb-221">You have large numbers of users.</span></span>
- <span data-ttu-id="d14fb-222">您的資料可以單純地表示，而不需要關聯性。</span><span class="sxs-lookup"><span data-stu-id="d14fb-222">Your data can be expressed simply without relationships.</span></span>
- <span data-ttu-id="d14fb-223">您必須將資料分散在不同的地理位置。</span><span class="sxs-lookup"><span data-stu-id="d14fb-223">You need to geographically distribute your data.</span></span>
- <span data-ttu-id="d14fb-224">您不需要 ACID 保證。</span><span class="sxs-lookup"><span data-stu-id="d14fb-224">You don't need ACID guarantees.</span></span>
- <span data-ttu-id="d14fb-225">將會部署到商用硬體。</span><span class="sxs-lookup"><span data-stu-id="d14fb-225">Will be deployed to commodity hardware.</span></span>

<span data-ttu-id="d14fb-226">然後，在下列情況考慮關係資料庫：</span><span class="sxs-lookup"><span data-stu-id="d14fb-226">Then, consider a relational database when:</span></span>

- <span data-ttu-id="d14fb-227">您的工作負載需要中型到大規模的規模。</span><span class="sxs-lookup"><span data-stu-id="d14fb-227">Your workloads require medium to large scale.</span></span>
- <span data-ttu-id="d14fb-228">平行存取並不是主要的考慮。</span><span class="sxs-lookup"><span data-stu-id="d14fb-228">Concurrency isn't a major concern.</span></span>
- <span data-ttu-id="d14fb-229">需要 ACID 保證。</span><span class="sxs-lookup"><span data-stu-id="d14fb-229">ACID guarantees are needed.</span></span>
- <span data-ttu-id="d14fb-230">資料最適合以 relationally 表示。</span><span class="sxs-lookup"><span data-stu-id="d14fb-230">Data is best expressed relationally.</span></span>
- <span data-ttu-id="d14fb-231">您的應用程式將會部署到大型的高階硬體。</span><span class="sxs-lookup"><span data-stu-id="d14fb-231">Your application will be deployed to large, high-end hardware.</span></span>

<span data-ttu-id="d14fb-232">接下來，我們會查看 Azure 雲端中的資料儲存體。</span><span class="sxs-lookup"><span data-stu-id="d14fb-232">Next, we look at data storage in the Azure cloud.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d14fb-233">[上一頁](distributed-data.md)
>[下一頁](azure-data-storage.md)</span><span class="sxs-lookup"><span data-stu-id="d14fb-233">[Previous](distributed-data.md)
[Next](azure-data-storage.md)</span></span>
