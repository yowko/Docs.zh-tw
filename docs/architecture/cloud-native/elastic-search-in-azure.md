---
title: 雲端原生應用程式中的 Elasticsearch
description: 瞭解如何將彈性搜尋功能新增至雲端原生應用程式。
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: e956f28877d88ce5279944964a877efc324918b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614080"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="aeefe-103">在雲端原生應用程式中 Elasticsearch</span><span class="sxs-lookup"><span data-stu-id="aeefe-103">Elasticsearch in a cloud-native app</span></span>

<span data-ttu-id="aeefe-104">Elasticsearch 是分散式搜尋和分析系統，可跨各種類型的資料提供複雜的搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="aeefe-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="aeefe-105">它是開放原始碼，而且很普遍。</span><span class="sxs-lookup"><span data-stu-id="aeefe-105">It's open source and widely popular.</span></span> <span data-ttu-id="aeefe-106">請考慮下列公司如何將 Elasticsearch 整合到其應用程式：</span><span class="sxs-lookup"><span data-stu-id="aeefe-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="aeefe-107">適用于全文檢索和增量的[維琪百科](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)（搜尋類型）搜尋。</span><span class="sxs-lookup"><span data-stu-id="aeefe-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="aeefe-108">[GitHub](https://www.elastic.co/customers/github)可編制索引並公開超過8000000個程式碼存放庫。</span><span class="sxs-lookup"><span data-stu-id="aeefe-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="aeefe-109">[Docker](https://www.elastic.co/customers/docker)讓其容器庫可供探索。</span><span class="sxs-lookup"><span data-stu-id="aeefe-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="aeefe-110">Elasticsearch 建置於[Apache Lucene](https://lucene.apache.org/core/)全文搜尋引擎之上。</span><span class="sxs-lookup"><span data-stu-id="aeefe-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="aeefe-111">Lucene 提供高效能的檔編制索引和查詢。</span><span class="sxs-lookup"><span data-stu-id="aeefe-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="aeefe-112">它會使用反向索引配置來編制資料的索引，而不是將頁面對應到關鍵字，而是將關鍵字對應到書籍結尾的詞彙，就像是書。</span><span class="sxs-lookup"><span data-stu-id="aeefe-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="aeefe-113">Lucene 具有強大的查詢語法功能，而且可以藉由下列方式查詢資料：</span><span class="sxs-lookup"><span data-stu-id="aeefe-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="aeefe-114">詞彙（全字組）</span><span class="sxs-lookup"><span data-stu-id="aeefe-114">Term (a full word)</span></span>
- <span data-ttu-id="aeefe-115">前置詞（開頭-含單字）</span><span class="sxs-lookup"><span data-stu-id="aeefe-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="aeefe-116">萬用字元（使用 " \* " 或 "？" 篩選）</span><span class="sxs-lookup"><span data-stu-id="aeefe-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="aeefe-117">片語（檔中的一連串文字）</span><span class="sxs-lookup"><span data-stu-id="aeefe-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="aeefe-118">布林值（複雜搜尋結合查詢）</span><span class="sxs-lookup"><span data-stu-id="aeefe-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="aeefe-119">雖然 Lucene 提供用於搜尋的低層級檢測，但 Elasticsearch 會提供位於 Lucene 之上的伺服器。</span><span class="sxs-lookup"><span data-stu-id="aeefe-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="aeefe-120">Elasticsearch 新增較高層級的功能來簡化 Lucene 的工作，包括 RESTful API 來存取 Lucene 的索引和搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="aeefe-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="aeefe-121">它也會提供能夠大規模擴充性、容錯和高可用性的分散式基礎結構。</span><span class="sxs-lookup"><span data-stu-id="aeefe-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="aeefe-122">針對具有複雜搜尋需求的較大型雲端原生應用程式，Elasticsearch 會以 Azure 中的受控服務形式提供。</span><span class="sxs-lookup"><span data-stu-id="aeefe-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="aeefe-123">Microsoft Azure Marketplace 功能預先設定的範本，可讓開發人員用來在 Azure 上部署 Elasticsearch 叢集。</span><span class="sxs-lookup"><span data-stu-id="aeefe-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="aeefe-124">從 Microsoft Azure Marketplace，開發人員可以使用專為在 Azure 上快速部署 Elasticsearch 叢集而建立的預先設定範本。</span><span class="sxs-lookup"><span data-stu-id="aeefe-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="aeefe-125">使用 Azure 管理的供應專案，您可以部署最多50個數據節點、20個協調節點，以及三個專用的主要節點。</span><span class="sxs-lookup"><span data-stu-id="aeefe-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="aeefe-126">摘要</span><span class="sxs-lookup"><span data-stu-id="aeefe-126">Summary</span></span>

<span data-ttu-id="aeefe-127">本章將詳細探討雲端原生系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="aeefe-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="aeefe-128">我們在整合型應用程式中的資料儲存區，與雲端原生系統中的資料儲存模式一併啟動。</span><span class="sxs-lookup"><span data-stu-id="aeefe-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="aeefe-129">我們探討了在雲端原生系統中所實行的資料模式，包括跨服務查詢、分散式交易，以及處理高容量系統的模式。</span><span class="sxs-lookup"><span data-stu-id="aeefe-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="aeefe-130">我們會將 SQL 與 NoSQL 資料進行對比。</span><span class="sxs-lookup"><span data-stu-id="aeefe-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="aeefe-131">我們探討了 Azure 中的資料儲存體選項，其中包括以 Microsoft 為中心的開放原始碼選項。</span><span class="sxs-lookup"><span data-stu-id="aeefe-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="aeefe-132">最後，我們在雲端原生應用程式中討論過快取和 Elasticsearch。</span><span class="sxs-lookup"><span data-stu-id="aeefe-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="aeefe-133">參考</span><span class="sxs-lookup"><span data-stu-id="aeefe-133">References</span></span>

- [<span data-ttu-id="aeefe-134">命令與查詢責任隔離 (CQRS) 模式</span><span class="sxs-lookup"><span data-stu-id="aeefe-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="aeefe-135">事件來源模式</span><span class="sxs-lookup"><span data-stu-id="aeefe-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="aeefe-136">為什麼 RDBMS 資料分割在 CAP 定理中無法承受，為什麼它可以使用？</span><span class="sxs-lookup"><span data-stu-id="aeefe-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="aeefe-137">具體化檢視模式</span><span class="sxs-lookup"><span data-stu-id="aeefe-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="aeefe-138">您真正需要知道的開放原始碼資料庫</span><span class="sxs-lookup"><span data-stu-id="aeefe-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="aeefe-139">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="aeefe-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="aeefe-140">Saga 模式</span><span class="sxs-lookup"><span data-stu-id="aeefe-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="aeefe-141">Saga 模式 |如何使用微服務來執行商務交易</span><span class="sxs-lookup"><span data-stu-id="aeefe-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="aeefe-142">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="aeefe-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="aeefe-143">開始進行9球：說明 Cosmos DB 一致性層級</span><span class="sxs-lookup"><span data-stu-id="aeefe-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="aeefe-144">探索不同類型的 NoSQL 資料庫第二部</span><span class="sxs-lookup"><span data-stu-id="aeefe-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="aeefe-145">在 RDBMS、NoSQL 和 NewSQL 資料庫上。與 John Ryan 訪談</span><span class="sxs-lookup"><span data-stu-id="aeefe-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="aeefe-146">SQL vs NoSQL 與 NewSQL：完整比較</span><span class="sxs-lookup"><span data-stu-id="aeefe-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="aeefe-147">破折號： Kubernetes 的四個屬性-原生資料庫</span><span class="sxs-lookup"><span data-stu-id="aeefe-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="aeefe-148">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="aeefe-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="aeefe-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="aeefe-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="aeefe-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="aeefe-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="aeefe-151">Vitess</span><span class="sxs-lookup"><span data-stu-id="aeefe-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="aeefe-152">Elasticsearch：完全指南</span><span class="sxs-lookup"><span data-stu-id="aeefe-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="aeefe-153">Apache Lucene 簡介</span><span class="sxs-lookup"><span data-stu-id="aeefe-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="aeefe-154">[上一個](azure-caching.md) 
>[下一步](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="aeefe-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
