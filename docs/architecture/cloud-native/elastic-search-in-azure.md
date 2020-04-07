---
title: 雲原生應用程式中的彈性搜尋
description: 瞭解如何將彈性搜索功能添加到雲本機應用程式。
author: robvet
ms.date: 03/02/2020
ms.openlocfilehash: da6b9402cf266f5a298b05cf837805b2377bc75a
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805558"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="ca9f5-103">雲原生應用程式中的彈性搜尋</span><span class="sxs-lookup"><span data-stu-id="ca9f5-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ca9f5-104">彈性搜索是一個分散式搜索和分析系統,能夠跨不同類型的數據實現複雜的搜索功能。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="ca9f5-105">它是開源的,很受歡迎。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-105">It's open source and widely popular.</span></span> <span data-ttu-id="ca9f5-106">考慮以下公司如何將彈性搜索整合到其應用程式中:</span><span class="sxs-lookup"><span data-stu-id="ca9f5-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="ca9f5-107">[維琪百科](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)用於全文和增量(搜索,你鍵入)搜索。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="ca9f5-108">[GitHub](https://www.elastic.co/customers/github)用於索引和公開超過 800 萬個代碼存儲庫。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="ca9f5-109">[用於](https://www.elastic.co/customers/docker)使其容器庫可發現。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="ca9f5-110">彈性搜索是建立在[阿帕奇盧塞內](https://lucene.apache.org/core/)全文搜尋引擎的頂部。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="ca9f5-111">Lucene 提供高性能的文檔索引和查詢。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="ca9f5-112">它使用倒置索引方案對數據進行索引 - 它不是將頁面映射到關鍵字,而是將關鍵字映射到頁面,就像書尾的詞彙表一樣。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="ca9f5-113">Lucene 具有強大的查詢語法功能,可以通過以下功能查詢數據:</span><span class="sxs-lookup"><span data-stu-id="ca9f5-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="ca9f5-114">字語 (完整單字)</span><span class="sxs-lookup"><span data-stu-id="ca9f5-114">Term (a full word)</span></span>
- <span data-ttu-id="ca9f5-115">前置字(以單字開頭)</span><span class="sxs-lookup"><span data-stu-id="ca9f5-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="ca9f5-116">通配符(使用\*""或「『篩選器)</span><span class="sxs-lookup"><span data-stu-id="ca9f5-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="ca9f5-117">短文 (文件中的文字序列)</span><span class="sxs-lookup"><span data-stu-id="ca9f5-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="ca9f5-118">布林值 (合併查詢的複雜搜尋)</span><span class="sxs-lookup"><span data-stu-id="ca9f5-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="ca9f5-119">雖然 Lucene 提供用於搜尋的低級管道,但 Elasticsearch 提供位於 Lucene 頂部的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="ca9f5-120">Elasticsearch 增加了更高級別的功能來簡化工作 Lucene,包括用於存取 Lucene 索引和搜尋功能的 RESTful API。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="ca9f5-121">它還提供了能夠大規模可擴充性、容錯性和高可用性的分散式基礎架構。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="ca9f5-122">對於具有複雜搜索要求的大型雲本機應用程式,彈性搜索在 Azure 中作為託管服務提供。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="ca9f5-123">Microsoft Azure 應用商店具有預先配置的範本,開發人員可以使用這些範本在 Azure 上部署彈性搜索群集。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="ca9f5-124">在 Microsoft Azure 應用商店中,開發人員可以使用構建的預配置範本在 Azure 上快速部署彈性搜索群集。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="ca9f5-125">使用 Azure 管理的產品,您最多可以部署 50 個數據節點、20 個協調節點和 3 個專用主節點。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="ca9f5-126">摘要</span><span class="sxs-lookup"><span data-stu-id="ca9f5-126">Summary</span></span>

<span data-ttu-id="ca9f5-127">本章詳細介紹了雲本機系統中的數據。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="ca9f5-128">我們首先將單片應用程序中的數據存儲與雲原生系統中的資料存儲模式進行對比。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="ca9f5-129">我們研究了在雲本機系統中實現的數據模式,包括跨服務查詢、分散式事務和處理大容量系統的模式。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="ca9f5-130">我們將 SQL 與 NoSQL 數據進行了對比。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="ca9f5-131">我們查看了 Azure 中提供的數據儲存選項,這些選項包括以 Microsoft 為中心的開源選項。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="ca9f5-132">最後,我們在雲本機應用程式中討論了緩存和彈性搜索。</span><span class="sxs-lookup"><span data-stu-id="ca9f5-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="ca9f5-133">參考</span><span class="sxs-lookup"><span data-stu-id="ca9f5-133">References</span></span>

- [<span data-ttu-id="ca9f5-134">命令與查詢責任隔離 (CQRS) 模式</span><span class="sxs-lookup"><span data-stu-id="ca9f5-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="ca9f5-135">事件採購模式</span><span class="sxs-lookup"><span data-stu-id="ca9f5-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="ca9f5-136">為什麼在 CAP 定理中 RDBMS 分區容錯,為什麼它可用?</span><span class="sxs-lookup"><span data-stu-id="ca9f5-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="ca9f5-137">具體化檢視</span><span class="sxs-lookup"><span data-stu-id="ca9f5-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="ca9f5-138">您真正需要知道的關於開源資料庫的所有資訊</span><span class="sxs-lookup"><span data-stu-id="ca9f5-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="ca9f5-139">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="ca9f5-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="ca9f5-140">佐賀模式</span><span class="sxs-lookup"><span data-stu-id="ca9f5-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="ca9f5-141">佐賀模式 |如何使用微服務實現業務事務</span><span class="sxs-lookup"><span data-stu-id="ca9f5-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="ca9f5-142">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="ca9f5-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="ca9f5-143">在 9 球後面:解釋宇宙 DB 一致性級別</span><span class="sxs-lookup"><span data-stu-id="ca9f5-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="ca9f5-144">探索不同類型的NoSQL資料庫第二部分</span><span class="sxs-lookup"><span data-stu-id="ca9f5-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="ca9f5-145">在 RDBMS、NoSQL 和 NewSQL 資料庫中。採訪約翰·里安</span><span class="sxs-lookup"><span data-stu-id="ca9f5-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="ca9f5-146">SQL vs NoSQL vs NewSQL:完整比較</span><span class="sxs-lookup"><span data-stu-id="ca9f5-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="ca9f5-147">DASH:庫伯內斯-本機資料庫的四個屬性</span><span class="sxs-lookup"><span data-stu-id="ca9f5-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="ca9f5-148">蟑螂DB</span><span class="sxs-lookup"><span data-stu-id="ca9f5-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="ca9f5-149">提亞布</span><span class="sxs-lookup"><span data-stu-id="ca9f5-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="ca9f5-150">尤加位元組開發銀行</span><span class="sxs-lookup"><span data-stu-id="ca9f5-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="ca9f5-151">維特斯</span><span class="sxs-lookup"><span data-stu-id="ca9f5-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="ca9f5-152">Elasticsearch：完全指南</span><span class="sxs-lookup"><span data-stu-id="ca9f5-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="ca9f5-153">阿帕奇·盧塞內簡介</span><span class="sxs-lookup"><span data-stu-id="ca9f5-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="ca9f5-154">[前一個](azure-caching.md)
>[下一個](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="ca9f5-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
