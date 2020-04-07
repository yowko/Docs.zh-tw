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
# <a name="elasticsearch-in-a-cloud-native-app"></a>雲原生應用程式中的彈性搜尋

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

彈性搜索是一個分散式搜索和分析系統,能夠跨不同類型的數據實現複雜的搜索功能。 它是開源的,很受歡迎。 考慮以下公司如何將彈性搜索整合到其應用程式中:

- [維琪百科](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)用於全文和增量(搜索,你鍵入)搜索。
- [GitHub](https://www.elastic.co/customers/github)用於索引和公開超過 800 萬個代碼存儲庫。  
- [用於](https://www.elastic.co/customers/docker)使其容器庫可發現。

彈性搜索是建立在[阿帕奇盧塞內](https://lucene.apache.org/core/)全文搜尋引擎的頂部。 Lucene 提供高性能的文檔索引和查詢。 它使用倒置索引方案對數據進行索引 - 它不是將頁面映射到關鍵字,而是將關鍵字映射到頁面,就像書尾的詞彙表一樣。 Lucene 具有強大的查詢語法功能,可以通過以下功能查詢數據:

- 字語 (完整單字)
- 前置字(以單字開頭)
- 通配符(使用\*""或「『篩選器)
- 短文 (文件中的文字序列)
- 布林值 (合併查詢的複雜搜尋)

雖然 Lucene 提供用於搜尋的低級管道,但 Elasticsearch 提供位於 Lucene 頂部的伺服器。 Elasticsearch 增加了更高級別的功能來簡化工作 Lucene,包括用於存取 Lucene 索引和搜尋功能的 RESTful API。 它還提供了能夠大規模可擴充性、容錯性和高可用性的分散式基礎架構。

對於具有複雜搜索要求的大型雲本機應用程式,彈性搜索在 Azure 中作為託管服務提供。 Microsoft Azure 應用商店具有預先配置的範本,開發人員可以使用這些範本在 Azure 上部署彈性搜索群集。

在 Microsoft Azure 應用商店中,開發人員可以使用構建的預配置範本在 Azure 上快速部署彈性搜索群集。 使用 Azure 管理的產品,您最多可以部署 50 個數據節點、20 個協調節點和 3 個專用主節點。

## <a name="summary"></a>摘要

本章詳細介紹了雲本機系統中的數據。 我們首先將單片應用程序中的數據存儲與雲原生系統中的資料存儲模式進行對比。 我們研究了在雲本機系統中實現的數據模式,包括跨服務查詢、分散式事務和處理大容量系統的模式。 我們將 SQL 與 NoSQL 數據進行了對比。 我們查看了 Azure 中提供的數據儲存選項,這些選項包括以 Microsoft 為中心的開源選項。 最後,我們在雲本機應用程式中討論了緩存和彈性搜索。

### <a name="references"></a>參考

- [命令與查詢責任隔離 (CQRS) 模式](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [事件採購模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [為什麼在 CAP 定理中 RDBMS 分區容錯,為什麼它可用?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [具體化檢視](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [您真正需要知道的關於開源資料庫的所有資訊](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [補償交易模式](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [佐賀模式](https://microservices.io/patterns/data/saga.html)

- [佐賀模式 |如何使用微服務實現業務事務](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [補償交易模式](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [在 9 球後面:解釋宇宙 DB 一致性級別](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [探索不同類型的NoSQL資料庫第二部分](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [在 RDBMS、NoSQL 和 NewSQL 資料庫中。採訪約翰·里安](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL:完整比較](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH:庫伯內斯-本機資料庫的四個屬性](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [蟑螂DB](https://www.cockroachlabs.com/)

- [提亞布](https://pingcap.com/en/)

- [尤加位元組開發銀行](https://www.yugabyte.com/)

- [維特斯](https://vitess.io/)

- [Elasticsearch：完全指南](http://shop.oreilly.com/product/0636920028505.do)
  
- [阿帕奇·盧塞內簡介](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[前一個](azure-caching.md)
>[下一個](resiliency.md) <!-- Next Chapter -->
