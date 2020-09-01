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
# <a name="elasticsearch-in-a-cloud-native-app"></a>雲端原生應用程式中的 Elasticsearch

Elasticsearch 是分散式搜尋和分析系統，可在各種不同類型的資料上啟用複雜的搜尋功能。 它是開放原始碼且很普遍。 請考慮下列公司如何將 Elasticsearch 整合到應用程式中：

- 當您輸入) 搜尋時，用來進行全文檢索和增量 (搜尋的[維琪百科](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)。
- [GitHub](https://www.elastic.co/customers/github) 可編制索引並公開超過8000000的程式碼存放庫。  
- [Docker](https://www.elastic.co/customers/docker) 可讓其容器程式庫可供探索。

Elasticsearch 建置於 [Apache Lucene](https://lucene.apache.org/core/) 全文搜尋引擎的最上層。 Lucene 提供高效能的檔編制索引和查詢。 它會使用反向索引編制配置來編制資料的索引，而不是將頁面對應至關鍵字，而是將關鍵字對應至頁面，就像書籍結尾的詞彙一樣。 Lucene 具有強大的查詢語法功能，並可透過下列方式來查詢資料：

- 全字 (詞彙) 
- 前置詞 (啟動-with word) 
- 萬用字元 (使用 " \* " 或 "？" 篩選) 
- 片語 (檔中的一連串文字) 
-  (複雜搜尋合併查詢的布林值) 

雖然 Lucene 提供用於搜尋的低層級的配量，但 Elasticsearch 會提供位於 Lucene 之上的伺服器。 Elasticsearch 新增了較高層級的功能，以簡化 Lucene 的工作，包括 RESTful API 來存取 Lucene 的索引編制和搜尋功能。 它也提供可大規模調整、容錯和高可用性的分散式基礎結構。

針對較大型的雲端原生應用程式與複雜的搜尋需求，Elasticsearch 可作為 Azure 中的受控服務。 Microsoft Azure Marketplace 功能預先設定的範本，可供開發人員用來在 Azure 上部署 Elasticsearch 叢集。

從 Microsoft Azure Marketplace，開發人員可以使用預先設定的範本，在 Azure 上快速部署 Elasticsearch 叢集。 您可以使用 Azure 管理的供應專案，部署最多50個數據節點、20個協調節點，以及三個專用的主要節點。

## <a name="summary"></a>總結

本章提供雲端原生系統中資料的詳細資料。 我們一開始會將整合型應用程式中的資料儲存體與雲端原生系統中的資料儲存模式進行對比。 我們探討了在雲端原生系統中實作為的資料模式，包括跨服務查詢、分散式交易，以及處理高容量系統的模式。 我們對比 SQL 與 NoSQL 資料。 我們探討了 Azure 中的資料儲存體選項，其中包括以 Microsoft 為中心的開放原始碼選項。 最後，我們討論了在雲端原生應用程式中的快取和 Elasticsearch。

### <a name="references"></a>參考資料

- [命令與查詢責任隔離 (CQRS) 模式](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [事件來源模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [為什麼在 CAP 定理中不能容忍 RDBMS 分割區的能力，以及它為何可供使用？](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [具體化檢視模式](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [您真正需要知道的是開放原始碼資料庫](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [補償交易模式](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Saga 模式](https://microservices.io/patterns/data/saga.html)

- [Saga 模式 |如何使用微服務來執行商務交易](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [補償交易模式](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [進入9球： Cosmos DB 的一致性層級進行說明](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [探索不同類型的 NoSQL 資料庫第二部分](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [在 RDBMS、NoSQL 和 NewSQL 資料庫上。與 John Ryan 訪談](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL 與 NoSQL vs NewSQL：完整的比較](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [虛線： Kubernetes 的四個屬性-原生資料庫](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [CockroachDB](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elasticsearch：完全指南](https://shop.oreilly.com/product/0636920028505.do)
  
- [Apache Lucene 簡介](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[上一個](azure-caching.md) 
>[下一步](resiliency.md) <!-- Next Chapter -->
