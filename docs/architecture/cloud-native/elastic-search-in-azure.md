---
title: 雲端原生應用程式中的 Elasticsearch
description: 瞭解如何將彈性搜尋功能新增至雲端原生應用程式。
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 70d1925d6b8c7bbe515ee4f178513dc61212ebce
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271798"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="925ee-103">雲端原生應用程式中的 Elasticsearch</span><span class="sxs-lookup"><span data-stu-id="925ee-103">Elasticsearch in a cloud-native app</span></span>

<span data-ttu-id="925ee-104">Elasticsearch 是分散式搜尋和分析系統，可在各種不同類型的資料上啟用複雜的搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="925ee-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="925ee-105">它是開放原始碼且很普遍。</span><span class="sxs-lookup"><span data-stu-id="925ee-105">It's open source and widely popular.</span></span> <span data-ttu-id="925ee-106">請考慮下列公司如何將 Elasticsearch 整合到應用程式中：</span><span class="sxs-lookup"><span data-stu-id="925ee-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="925ee-107">當您輸入) 搜尋時，用來進行全文檢索和增量 (搜尋的[維琪百科](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)。</span><span class="sxs-lookup"><span data-stu-id="925ee-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="925ee-108">[GitHub](https://www.elastic.co/customers/github) 可編制索引並公開超過8000000的程式碼存放庫。</span><span class="sxs-lookup"><span data-stu-id="925ee-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="925ee-109">[Docker](https://www.elastic.co/customers/docker) 可讓其容器程式庫可供探索。</span><span class="sxs-lookup"><span data-stu-id="925ee-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="925ee-110">Elasticsearch 建置於 [Apache Lucene](https://lucene.apache.org/core/) 全文搜尋引擎的最上層。</span><span class="sxs-lookup"><span data-stu-id="925ee-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="925ee-111">Lucene 提供高效能的檔編制索引和查詢。</span><span class="sxs-lookup"><span data-stu-id="925ee-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="925ee-112">它會使用反向索引編制配置來編制資料的索引，而不是將頁面對應至關鍵字，而是將關鍵字對應至頁面，就像書籍結尾的詞彙一樣。</span><span class="sxs-lookup"><span data-stu-id="925ee-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="925ee-113">Lucene 具有強大的查詢語法功能，並可透過下列方式來查詢資料：</span><span class="sxs-lookup"><span data-stu-id="925ee-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="925ee-114">全字 (詞彙) </span><span class="sxs-lookup"><span data-stu-id="925ee-114">Term (a full word)</span></span>
- <span data-ttu-id="925ee-115">前置詞 (啟動-with word) </span><span class="sxs-lookup"><span data-stu-id="925ee-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="925ee-116">萬用字元 (使用 " \* " 或 "？" 篩選) </span><span class="sxs-lookup"><span data-stu-id="925ee-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="925ee-117">片語 (檔中的一連串文字) </span><span class="sxs-lookup"><span data-stu-id="925ee-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="925ee-118"> (複雜搜尋合併查詢的布林值) </span><span class="sxs-lookup"><span data-stu-id="925ee-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="925ee-119">雖然 Lucene 提供用於搜尋的低層級的配量，但 Elasticsearch 會提供位於 Lucene 之上的伺服器。</span><span class="sxs-lookup"><span data-stu-id="925ee-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="925ee-120">Elasticsearch 新增了較高層級的功能，以簡化 Lucene 的工作，包括 RESTful API 來存取 Lucene 的索引編制和搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="925ee-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="925ee-121">它也提供可大規模調整、容錯和高可用性的分散式基礎結構。</span><span class="sxs-lookup"><span data-stu-id="925ee-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="925ee-122">針對較大型的雲端原生應用程式與複雜的搜尋需求，Elasticsearch 可作為 Azure 中的受控服務。</span><span class="sxs-lookup"><span data-stu-id="925ee-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="925ee-123">Microsoft Azure Marketplace 功能預先設定的範本，可供開發人員用來在 Azure 上部署 Elasticsearch 叢集。</span><span class="sxs-lookup"><span data-stu-id="925ee-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="925ee-124">從 Microsoft Azure Marketplace，開發人員可以使用預先設定的範本，在 Azure 上快速部署 Elasticsearch 叢集。</span><span class="sxs-lookup"><span data-stu-id="925ee-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="925ee-125">您可以使用 Azure 管理的供應專案，部署最多50個數據節點、20個協調節點，以及三個專用的主要節點。</span><span class="sxs-lookup"><span data-stu-id="925ee-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="925ee-126">總結</span><span class="sxs-lookup"><span data-stu-id="925ee-126">Summary</span></span>

<span data-ttu-id="925ee-127">本章提供雲端原生系統中資料的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="925ee-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="925ee-128">我們一開始會將整合型應用程式中的資料儲存體與雲端原生系統中的資料儲存模式進行對比。</span><span class="sxs-lookup"><span data-stu-id="925ee-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="925ee-129">我們探討了在雲端原生系統中實作為的資料模式，包括跨服務查詢、分散式交易，以及處理高容量系統的模式。</span><span class="sxs-lookup"><span data-stu-id="925ee-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="925ee-130">我們對比 SQL 與 NoSQL 資料。</span><span class="sxs-lookup"><span data-stu-id="925ee-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="925ee-131">我們探討了 Azure 中的資料儲存體選項，其中包括以 Microsoft 為中心的開放原始碼選項。</span><span class="sxs-lookup"><span data-stu-id="925ee-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="925ee-132">最後，我們討論了在雲端原生應用程式中的快取和 Elasticsearch。</span><span class="sxs-lookup"><span data-stu-id="925ee-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="925ee-133">參考資料</span><span class="sxs-lookup"><span data-stu-id="925ee-133">References</span></span>

- [<span data-ttu-id="925ee-134">命令與查詢責任隔離 (CQRS) 模式</span><span class="sxs-lookup"><span data-stu-id="925ee-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="925ee-135">事件來源模式</span><span class="sxs-lookup"><span data-stu-id="925ee-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="925ee-136">為什麼在 CAP 定理中不能容忍 RDBMS 分割區的能力，以及它為何可供使用？</span><span class="sxs-lookup"><span data-stu-id="925ee-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="925ee-137">具體化檢視模式</span><span class="sxs-lookup"><span data-stu-id="925ee-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="925ee-138">您真正需要知道的是開放原始碼資料庫</span><span class="sxs-lookup"><span data-stu-id="925ee-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="925ee-139">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="925ee-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="925ee-140">Saga 模式</span><span class="sxs-lookup"><span data-stu-id="925ee-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="925ee-141">Saga 模式 |如何使用微服務來執行商務交易</span><span class="sxs-lookup"><span data-stu-id="925ee-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="925ee-142">補償交易模式</span><span class="sxs-lookup"><span data-stu-id="925ee-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="925ee-143">進入9球： Cosmos DB 的一致性層級進行說明</span><span class="sxs-lookup"><span data-stu-id="925ee-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="925ee-144">探索不同類型的 NoSQL 資料庫第二部分</span><span class="sxs-lookup"><span data-stu-id="925ee-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="925ee-145">在 RDBMS、NoSQL 和 NewSQL 資料庫上。與 John Ryan 訪談</span><span class="sxs-lookup"><span data-stu-id="925ee-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="925ee-146">SQL 與 NoSQL vs NewSQL：完整的比較</span><span class="sxs-lookup"><span data-stu-id="925ee-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="925ee-147">虛線： Kubernetes 的四個屬性-原生資料庫</span><span class="sxs-lookup"><span data-stu-id="925ee-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="925ee-148">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="925ee-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="925ee-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="925ee-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="925ee-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="925ee-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="925ee-151">Vitess</span><span class="sxs-lookup"><span data-stu-id="925ee-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="925ee-152">Elasticsearch：完全指南</span><span class="sxs-lookup"><span data-stu-id="925ee-152">Elasticsearch: The Definitive Guide</span></span>](https://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="925ee-153">Apache Lucene 簡介</span><span class="sxs-lookup"><span data-stu-id="925ee-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="925ee-154">[上一個](azure-caching.md) 
>[下一步](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="925ee-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
