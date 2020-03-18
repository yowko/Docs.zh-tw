---
title: 雲原生應用程式中的彈性搜索
description: 瞭解如何將彈性搜索功能添加到雲本機應用程式。
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 1bce255b6315006b11e0b6ac77040300f67ed984
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141285"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="a260c-103">雲原生應用程式中的彈性搜索</span><span class="sxs-lookup"><span data-stu-id="a260c-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a260c-104">彈性搜索是一個分散式搜索和分析系統，能夠跨不同類型的資料實現複雜的搜索功能。</span><span class="sxs-lookup"><span data-stu-id="a260c-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="a260c-105">它是開源的，很受歡迎。</span><span class="sxs-lookup"><span data-stu-id="a260c-105">It's open source and widely popular.</span></span> <span data-ttu-id="a260c-106">考慮以下公司如何將彈性搜索集成到其應用程式中：</span><span class="sxs-lookup"><span data-stu-id="a260c-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="a260c-107">[維琪百科](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)用於全文和增量（搜索，你鍵入）搜索。</span><span class="sxs-lookup"><span data-stu-id="a260c-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="a260c-108">[GitHub](https://www.elastic.co/customers/github)用於索引和公開超過 800 萬個代碼存儲庫。</span><span class="sxs-lookup"><span data-stu-id="a260c-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="a260c-109">[用於](https://www.elastic.co/customers/docker)使其容器庫可發現。</span><span class="sxs-lookup"><span data-stu-id="a260c-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="a260c-110">彈性搜索是建立在[阿帕奇盧塞內](https://lucene.apache.org/core/)全文搜尋引擎的頂部。</span><span class="sxs-lookup"><span data-stu-id="a260c-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="a260c-111">Lucene 提供高性能的文檔索引和查詢。</span><span class="sxs-lookup"><span data-stu-id="a260c-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="a260c-112">它使用倒置索引方案對資料進行索引 - 它不是將頁面映射到關鍵字，而是將關鍵字映射到頁面，就像書尾的詞彙表一樣。</span><span class="sxs-lookup"><span data-stu-id="a260c-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="a260c-113">Lucene 具有強大的查詢語法功能，可以通過以下功能查詢資料：</span><span class="sxs-lookup"><span data-stu-id="a260c-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="a260c-114">術語（完整單詞）</span><span class="sxs-lookup"><span data-stu-id="a260c-114">Term (a full word)</span></span>
- <span data-ttu-id="a260c-115">首碼（以單詞開頭）</span><span class="sxs-lookup"><span data-stu-id="a260c-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="a260c-116">萬用字元（使用\*""或""篩選器）</span><span class="sxs-lookup"><span data-stu-id="a260c-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="a260c-117">短語（文檔中的文本序列）</span><span class="sxs-lookup"><span data-stu-id="a260c-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="a260c-118">布林值（合併查詢的複雜搜索）</span><span class="sxs-lookup"><span data-stu-id="a260c-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="a260c-119">雖然 Lucene 提供用於搜索的低級管道，但 Elasticsearch 提供位於 Lucene 頂部的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a260c-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="a260c-120">Elasticsearch 增加了更高級別的功能來簡化工作 Lucene，包括用於訪問 Lucene 索引和搜索功能的 RESTful API。</span><span class="sxs-lookup"><span data-stu-id="a260c-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene’s indexing and searching functionality.</span></span> <span data-ttu-id="a260c-121">它還提供了能夠大規模可擴充性、容錯性和高可用性的分散式基礎架構。</span><span class="sxs-lookup"><span data-stu-id="a260c-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="a260c-122">對於具有複雜搜索要求的大型雲本機應用程式，彈性搜索在 Azure 中作為託管服務提供。</span><span class="sxs-lookup"><span data-stu-id="a260c-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="a260c-123">Microsoft Azure 應用商店具有預先配置的範本，開發人員可以使用這些範本在 Azure 上部署彈性搜索群集。</span><span class="sxs-lookup"><span data-stu-id="a260c-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="a260c-124">在 Microsoft Azure 應用商店中，開發人員可以使用構建的預配置範本在 Azure 上快速部署彈性搜索群集。</span><span class="sxs-lookup"><span data-stu-id="a260c-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="a260c-125">使用 Azure 管理的產品，您最多可以部署 50 個數據節點、20 個協調節點和 3 個專用主節點。</span><span class="sxs-lookup"><span data-stu-id="a260c-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="a260c-126">摘要</span><span class="sxs-lookup"><span data-stu-id="a260c-126">Summary</span></span>

<span data-ttu-id="a260c-127">本章詳細介紹了雲本機系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="a260c-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="a260c-128">我們首先將單片應用程式中的資料存儲與雲原生系統中的資料存儲模式進行對比。</span><span class="sxs-lookup"><span data-stu-id="a260c-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="a260c-129">我們研究了在雲本機系統中實現的資料模式，包括跨服務查詢、分散式交易和處理大容量系統的模式。</span><span class="sxs-lookup"><span data-stu-id="a260c-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="a260c-130">我們將 SQL 與 NoSQL 資料進行了對比。</span><span class="sxs-lookup"><span data-stu-id="a260c-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="a260c-131">我們查看了 Azure 中提供的資料存儲選項，這些選項包括以 Microsoft 為中心的開源選項。</span><span class="sxs-lookup"><span data-stu-id="a260c-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="a260c-132">最後，我們在雲本機應用程式中討論了緩存和彈性搜索。</span><span class="sxs-lookup"><span data-stu-id="a260c-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="a260c-133">參考</span><span class="sxs-lookup"><span data-stu-id="a260c-133">References</span></span>

- [<span data-ttu-id="a260c-134">命令與查詢責任隔離 (CQRS) 模式</span><span class="sxs-lookup"><span data-stu-id="a260c-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="a260c-135">事件採購模式</span><span class="sxs-lookup"><span data-stu-id="a260c-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="a260c-136">RDBMS vs. NoSQL 資料庫：概述</span><span class="sxs-lookup"><span data-stu-id="a260c-136">RDBMSs vs. NoSQL Databases: Overview</span></span>](https://maxivak.com/rdbms-vs-nosql-databases/)

- [<span data-ttu-id="a260c-137">為什麼在 CAP 定理中 RDBMS 分區容錯，為什麼它可用？</span><span class="sxs-lookup"><span data-stu-id="a260c-137">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="a260c-138">具體化視圖</span><span class="sxs-lookup"><span data-stu-id="a260c-138">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="a260c-139">您真正需要知道的關於開源資料庫的所有資訊</span><span class="sxs-lookup"><span data-stu-id="a260c-139">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="a260c-140">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="a260c-140">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="a260c-141">佐賀模式</span><span class="sxs-lookup"><span data-stu-id="a260c-141">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="a260c-142">佐賀模式 |如何使用微服務實現業務事務</span><span class="sxs-lookup"><span data-stu-id="a260c-142">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="a260c-143">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="a260c-143">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="a260c-144">在 9 球後面：解釋宇宙 DB 一致性級別</span><span class="sxs-lookup"><span data-stu-id="a260c-144">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="a260c-145">探索不同類型的NoSQL資料庫第二部分</span><span class="sxs-lookup"><span data-stu-id="a260c-145">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="a260c-146">在 RDBMS、NoSQL 和 NewSQL 資料庫中。採訪約翰·里安</span><span class="sxs-lookup"><span data-stu-id="a260c-146">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="a260c-147">SQL vs NoSQL vs NewSQL：完整比較</span><span class="sxs-lookup"><span data-stu-id="a260c-147">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="a260c-148">DASH：庫伯內斯-本機資料庫的四個屬性</span><span class="sxs-lookup"><span data-stu-id="a260c-148">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="a260c-149">蟑螂DB</span><span class="sxs-lookup"><span data-stu-id="a260c-149">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="a260c-150">提亞布</span><span class="sxs-lookup"><span data-stu-id="a260c-150">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="a260c-151">尤加位元組開發銀行</span><span class="sxs-lookup"><span data-stu-id="a260c-151">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="a260c-152">維特斯</span><span class="sxs-lookup"><span data-stu-id="a260c-152">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="a260c-153">Elasticsearch：完全指南</span><span class="sxs-lookup"><span data-stu-id="a260c-153">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="a260c-154">阿帕奇·盧塞內簡介</span><span class="sxs-lookup"><span data-stu-id="a260c-154">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="a260c-155">[上一個](azure-caching.md)
>[下一個](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="a260c-155">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
