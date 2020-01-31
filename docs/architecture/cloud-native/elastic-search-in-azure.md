---
title: 雲端原生應用程式中的 Elasticsearch
description: 瞭解如何將彈性搜尋功能新增至雲端原生應用程式。
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 6ea237eddc89a8c6843d6b34b05b1b71515a99b6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794874"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>在雲端原生應用程式中 Elasticsearch

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elasticsearch 是分散式搜尋和分析系統，可跨各種類型的資料提供複雜的搜尋功能。 它是開放原始碼，而且很普遍。 請考慮下列公司如何將 Elasticsearch 整合到其應用程式：

- 適用于全文檢索和增量的[維琪百科](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)（搜尋類型）搜尋。
- [GitHub](https://www.elastic.co/customers/github)可編制索引並公開超過8000000個程式碼存放庫。  
- [Docker](https://www.elastic.co/customers/docker)讓其容器庫可供探索。

Elasticsearch 建置於[Apache Lucene](https://lucene.apache.org/core/)全文搜尋引擎之上。 Lucene 提供高效能的檔編制索引和查詢。 它會使用反向索引配置來編制資料的索引，而不是將頁面對應到關鍵字，而是將關鍵字對應到書籍結尾的詞彙，就像是書。 Lucene 具有強大的查詢語法功能，而且可以藉由下列方式查詢資料：

- 詞彙（全字組） 
- 前置詞（開頭-含單字）
- 萬用字元（使用 "\*" 或 "？" 篩選）
- 片語（檔中的一連串文字）
- 布林值（複雜搜尋結合查詢）

雖然 Lucene 提供用於搜尋的低層級檢測，但 Elasticsearch 會提供位於 Lucene 之上的伺服器。 Elasticsearch 新增較高層級的功能來簡化 Lucene 的工作，包括 RESTful API 來存取 Lucene 的索引和搜尋功能。 它也會提供能夠大規模擴充性、容錯和高可用性的分散式基礎結構。

針對具有複雜搜尋需求的較大型雲端原生應用程式，Elasticsearch 會以 Azure 中的受控服務形式提供。 Microsoft Azure Marketplace 功能預先設定的範本，可讓開發人員用來在 Azure 上部署 Elasticsearch 叢集。

從 Microsoft Azure Marketplace，開發人員可以使用專為在 Azure 上快速部署 Elasticsearch 叢集而建立的預先設定範本。 使用 Azure 管理的供應專案，您可以部署最多50個數據節點、20個協調節點，以及三個專用的主要節點。

## <a name="summary"></a>總結

本章將詳細探討雲端原生系統中的資料。 我們在整合型應用程式中的資料儲存區，與雲端原生系統中的資料儲存模式一併啟動。 我們探討了在雲端原生系統中所實行的資料模式，包括跨服務查詢、分散式交易，以及處理高容量系統的模式。 我們會將 SQL 與 NoSQL 資料進行對比。 我們探討了 Azure 中的資料儲存體選項，其中包括以 Microsoft 為中心的開放原始碼選項。 最後，我們在雲端原生應用程式中討論過快取和 Elasticsearch。

### <a name="references"></a>參考

- [命令與查詢責任隔離（CQRS）模式](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [事件來源模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [Rdbms 與 NoSQL 資料庫的比較：總覽](https://maxivak.com/rdbms-vs-nosql-databases/)

- [為什麼 RDBMS 資料分割在 CAP 定理中無法承受，為什麼它可以使用？](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [具體化視圖](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [您真正需要知道的開放原始碼資料庫](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [補償交易模式](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Saga 模式](https://microservices.io/patterns/data/saga.html)

- [Saga 模式 |如何使用微服務來執行商務交易](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [補償交易模式](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [開始進行9球：說明 Cosmos DB 一致性層級](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [探索不同類型的 NoSQL 資料庫第二部](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [在 RDBMS、NoSQL 和 NewSQL 資料庫上。與 John Ryan 訪談](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL 與 NewSQL：完整比較](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [破折號： Kubernetes 的四個屬性-原生資料庫](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [CockroachDB](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elasticsearch：最終指南](http://shop.oreilly.com/product/0636920028505.do)
  
- [Apache Lucene 簡介](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[上一頁](azure-caching.md)
>[下一頁](resiliency.md) <!-- Next Chapter -->
