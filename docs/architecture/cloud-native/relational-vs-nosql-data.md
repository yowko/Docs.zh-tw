---
title: 關聯式與NoSQL 資料
description: 瞭解雲原生應用程式中的關係數據和 NoSQL 資料
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 3fb3dcc3a87e278c05f3e15d261245f4d61453d1
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805802"
---
# <a name="relational-vs-nosql-data"></a>關聯式與NoSQL 資料

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

關係和 NoSQL 是兩種類型的資料庫系統,通常在雲本機應用程式中實現。 它們構建方式不同,存儲數據不同,訪問方式也不同。 在本節中,我們將介紹這兩個。 在本章的後面部分,我們將介紹一種名為*NewSQL*的新興資料庫技術。

*幾十年來,關係資料庫*一直是一種流行的技術。 它們成熟、成熟且廣泛實施。 競爭的資料庫產品、工具和專業知識比比皆是。 關係資料庫提供相關數據表的存儲。 這些表具有固定的架構,使用 SQL(結構化查詢語言)來管理數據,並支援 ACID 保證。

*無 SQL 資料庫*是指高性能、非關係數據存儲。 他們在易用性、可擴充性、彈性和可用性特性方面表現卓越。 NoSQL 不是聯接規範化數據的表,而是存儲非結構化或半結構化數據,通常存儲在鍵值對或 JSON 文檔中。 無 SQL 資料庫通常不提供超出單個資料庫分區範圍的 ACID 保證。 需要次秒回應時間的高容量服務有利於 NoSQL 資料存儲。

[NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/)技術對分散式雲本機系統的影響怎麼強調也不為過。 這一領域的新數據技術的激增打亂了曾經完全依賴關係資料庫的解決方案。

NoSQL 資料庫包括幾個用於訪問和管理數據的不同模型,每個模型都適合特定的用例。 圖 5-9 顯示了四種常見模型。

![無SQL資料模型](./media/types-of-nosql-datastores.png)

**圖 5-9**: NoSQL 資料庫的資料模型

| 模型 | 特性 |
| :-------- | :-------- |
| 文件儲存 | 數據和元數據在資料庫中基於 JSON 的文檔中分層存儲。 |
| 關鍵價值儲存 | 作為 NoSQL 資料庫中最簡單的數據,數據表示為鍵值對的集合。 |
| 寬柱商店 | 相關資料存儲在單個列中的一組嵌套鍵/值對中。 |
| 圖形儲存 | 數據存儲在圖形結構中作為節點、邊和數據屬性。 |

## <a name="the-cap-theorem"></a>CAP 定理

為了瞭解這些類型的資料庫之間的差異,請考慮 CAP 定理,這是一組應用於存儲狀態的分散式系統的原則。 圖 5-10 顯示了 CAP 定理的三個屬性。

![CAP 定理](./media/cap-theorem.png)

**圖 5-10**。 CAP 定理

該定理指出,分散式數據系統將在一致性、可用性和分區容差之間進行權衡。 而且,任何資料庫只能保證三個屬性中的*兩*個:

- *一致性。* 群集中的每個節點都回應最新的數據,即使系統必須阻止請求,直到所有副本更新。 如果查詢當前正在更新的專案的"一致系統",則將等待該回應,直到所有副本成功更新。 但是,您將收到最新的數據。

- *可用性。* 每個節點都會返回即時回應,即使該回應不是最新的數據。 如果查詢正在更新的專案的"可用系統",您將獲得該服務此時可以提供的最佳答案。

- *分區容差。* 保證即使複製的數據節點發生故障或失去與其他複製數據節點的連接,系統也能繼續運行。

關係資料庫通常提供一致性和可用性,但不提供分區容差。 它們通常預配到單個伺服器,並通過向計算機添加更多資源來垂直擴展。

許多關係資料庫系統都支援內建複製功能,其中主資料庫的副本可以製作到其他輔助伺服器實例。 寫入操作對主實例執行,並複製到每個輔助實例。 發生故障時,主實例可能會故障轉移到輔助實例以提供高可用性。 輔助資料庫還可用於分發讀取操作。 雖然寫入操作始終針對主副本,但讀取操作可以路由到任何輔助副本,以減少系統負載。

資料也可以跨多個節點水準分割區,例如分[片](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)。 但是,分片化通過將數據吐出許多不易通信的片段,大大增加了操作開銷。 管理可能既昂貴又耗時。 它最終可能會影響性能、表聯接和參考完整性。

如果資料複本在"高度一致"的關係資料庫群集中失去網路連接,您將無法寫入資料庫。 系統將拒絕寫入操作,因為它無法將該更改複製到其他數據副本。 每個數據副本都必須在事務完成之前進行更新。

NoSQL 資料庫通常支援高可用性和分區容差。 它們橫向擴展,通常跨商品伺服器擴展。 這種方法在地理區域內和跨地理區域之間提供巨大的可用性,成本降低。 跨這些計算機或節點對數據進行分區和複製,從而提供冗餘和容錯能力。 缺點是一致性。 更改一個 NoSQL 節點上的數據可能需要一些時間才能傳播到其他節點。 通常,NoSQL 資料庫節點會立即回應查詢 - 即使顯示的數據已過時且尚未更新。

如果資料複本在「高度可用」的 NoSQL 資料庫群集中失去連接,您仍然可以完成對資料庫的寫入操作。 資料庫群集將允許寫入操作,並在每個數據副本可用時更新它。

這種結果稱為最終一致性,這是不支援 ACID 事務的分散式數據系統的一個特徵。 在數據項的更新與將該更新傳播到每個副本節點所需的時間之間,這是短暫的延遲。 在正常情況下,滯後通常是短的,但當出現問題時可能會增加。 例如,如果要更新美國 NoSQL 資料庫中的產品項並從歐洲的副本節點查詢同一數據項,會發生什麼情況? 您將收到較早的產品資訊,直到群集更新帶有產品更改的歐洲節點。 通過立即返回查詢結果,而不是等待所有副本節點更新,您可以獲得巨大的規模和卷,但可以呈現較舊的數據。

高可用性和大規模可擴充性通常比強一致性對業務更關鍵。 開發人員可以實施像 Sagas、CQRS 和非同步訊息傳遞這樣的技術和模式,以擁抱最終的一致性。

> 如今,在約束 CAP 定理約束時必須小心謹慎。 一種稱為NewSQL的新型資料庫已經擴展了關係資料庫引擎,以支援NoSQL系統的橫向可擴充性和可擴充性能。

## <a name="considerations-for-relational-vs-nosql-systems"></a>關聯與 NoSQL 系統的注意事項

根據特定數據要求,基於雲的微服務可以實現關係、NoSQL 數據存儲或兩者。

|  在以下時間考慮 NoSQL 資料儲存: | 在以下時間考慮關係資料庫: |
| :-------- | :-------- |
| 您擁有需要大規模的高容量工作負載 | 您的工作負載量是一致的,需要大中型 |
| 您的工作負載不需要 ACID 保證 |  需要 ACID 保證 |
| 您的資料是動態的,並且經常變更 | 您的資料是可預測的,並且結構高度 |
| 資料可以在沒有關係的情況下表達 | 資料最好以關係表示 |  
| 您需要快速寫入,寫入安全性不重要 | 寫入安全是一項要求 |  
| 數據檢索簡單,趨於平面 | 您處理複雜查詢與報表|
| 您的資料需要廣泛的地理分佈 | 您的使用者更集中 |
| 您的應用程式將部署到商用硬體,例如使用公共雲 | 您的應用程式將部署到大型高階硬體 |
|||

在下一節中,我們將探討 Azure 雲中可用於存儲和管理雲原生數據的選項。

## <a name="database-as-a-service"></a>資料庫為服務

首先,您可以預配 Azure 虛擬機器,並為每個服務安裝您選擇的資料庫。 雖然您可以完全控制環境,但您會放棄雲平台的許多內置功能。 您還將負責管理每個服務的虛擬機器和資料庫。 這種方法可能很快變得耗時且成本高昂。

相反,雲原生應用程序傾向於作為[資料庫作為服務 (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/)公開的數據服務。 這些服務完全由雲供應商管理,可提供內置的安全性、可擴充性和監視。 您只需將其用作[支援服務](./definition.md#backing-services),而不是擁有該服務。 供應商大規模營運資源,並負責性能和維護。

它們可以跨雲可用性區域和區域進行配置,以實現高可用性。 他們都支援準時的容量和即用即付模式。 Azure 具有不同類型的託管數據服務選項,每個選項都有特定的優勢。

我們首先將瞭解 Azure 中提供的關係 DBaaS 服務。 您將看到 Microsoft 的旗艦 SQL Server 資料庫以及幾個開源選項都可用。 然後,我們將討論 Azure 中的 NoSQL 數據服務。

## <a name="azure-relational-databases"></a>Azure 關聯資料庫

對於需要關係數據的雲原生微服務,Azure 提供四個託管關係資料庫作為服務 (DBaaS) 產品,如圖 5-11 所示。

![Azure 的託管關係資料庫](./media/azure-managed-databases.png)

**圖 5-11**。 Azure 中提供的託管關係資料庫

在上圖中,請注意每個基礎設施如何位於通用 DBaaS 基礎結構上,該基礎結構具有關鍵功能,無需額外費用。

這些功能對於提供大量資料庫但管理這些資料庫的資源有限的組織尤其重要。
通過選擇處理核心、記憶體和基礎存儲的數量,可以在幾分鐘內預配 Azure 資料庫。 您可以動態擴展資料庫並動態調整資源,但停機時間很少或沒有停機時間。

## <a name="azure-sql-database"></a>Azure SQL Database

具有 Microsoft SQL Server 專業知識的開發團隊應考慮[Azure SQL 資料庫](https://docs.microsoft.com/azure/sql-database/)。 它是基於 Microsoft SQL Server 資料庫引擎的完全託管關係資料庫即服務 (DBaaS)。 該服務共用 SQL Server 的本地版本中的許多功能,並運行 SQL Server 資料庫引擎的最新穩定版本。

對於與雲端原生微服務一起使用,Azure SQL 資料庫提供三個部署選項:

- 單個資料庫表示在 Azure 雲中的 Azure [SQL 資料庫伺服器上](https://docs.microsoft.com/azure/sql-database/sql-database-servers)運行的完全託管 SQL 資料庫。 資料庫被視為[*包含*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases),因為它對基礎資料庫伺服器上沒有配置依賴項。
  
- [託管實例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)是 Microsoft SQL Server 資料庫引擎的完全託管實例,它提供與本地 SQL Server 的近 100% 相容性。 此選項支援更大的資料庫(最多 35 TB)並放置在[Azure 虛擬網路中](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)以更好的隔離。

- [Azure SQL 資料庫無伺服器](https://docs.microsoft.com/azure/sql-database/sql-database-serverless)是單個資料庫的計算層,該資料庫根據工作負載需求自動擴展。 它只對每秒使用的計算量進行帳單。 該服務非常適合間歇性、不可預知的使用模式的工作負載,這些工作負載穿插於不活動期。 無伺服器計算層還會在非活動期間自動暫停資料庫,以便只收取存儲費用。 當活動返回時,它會自動恢復。

除了傳統的 Microsoft SQL Server 堆疊之外,Azure 還具有三個常用開源資料庫的託管版本。

## <a name="open-source-databases-in-azure"></a>Azure 中的開源資料庫

開源關係資料庫已成為雲原生應用程式的熱門選擇。 許多企業比商業資料庫產品更青睞它們,尤其是為了節省成本。 許多開發團隊都享有靈活性、社區支援的開發以及工具和擴展的生態系統。 開源資料庫可以跨多個雲端供應商部署,有助於最大限度地減少"供應商鎖定"的問題。

開發人員可以輕鬆地在 Azure VM 上自承載任何開源資料庫。 在提供完全控制的同時,此方法使您能夠對資料庫和VM的管理、監視和維護。

但是,Microsoft 繼續致力於將 Azure 作為*完全託管*的 DBaaS 服務提供幾個流行的開源資料庫,從而保持 Azure 的"開放平臺」。

### <a name="azure-database-for-mysql"></a>適用於 MySQL 的 Azure 資料庫

[MySQL](https://en.wikipedia.org/wiki/MySQL) 是一個開源關係資料庫,是[建立在LAMP軟體堆疊](https://en.wikipedia.org/wiki/LAMP_(software_bundle))上的應用程式的支柱。 廣泛選擇*閱讀繁重的*工作量,它被許多大型組織使用,包括Facebook,Twitter和YouTube。 社區版免費提供,而企業版需要購買許可證。 該產品最初創建於1995年,於2008年被Sun微系統公司購買。 甲骨文於2010年收購了Sun和MySQL。

[MySQL 的 Azure 資料庫](https://azure.microsoft.com/services/mysql/)是基於開源 MySQL Server 引擎的託管關係資料庫服務。 它使用 MySQL 社群版本。 Azure MySQL 伺服器是服務的管理點。 它與用於本地部署的 MySQL 伺服器引擎相同。 引擎可以創建每個伺服器的單個資料庫,也可以創建每個共用資源的伺服器的多個資料庫。 您可以繼續使用相同的開源工具管理數據,而無需學習新技能或管理虛擬機器。

### <a name="azure-database-for-mariadb"></a>適用於 MariaDB 的 Azure 資料庫

[瑪麗亞DB](https://mariadb.com/)伺服器是另一個流行的開源資料庫伺服器。 當甲骨文收購擁有MySQL的太陽微系統公司時,它被創建為MySQL的*分叉*。 目的是確保MariaDB保持開放源碼。 由於 MariaDB 是 MySQL 的分叉,因此數據和表定義是相容的,並且用戶端協定、結構和 API 是緊密相連的。

MariaDB 擁有強大的社區,被許多大型企業所使用。 當 Oracle 繼續維護、增強和支援 MySQL 時,MariaDB 基金會管理 MariaDB,允許對產品和文檔進行公共貢獻。

[MariaDB 的 Azure 資料庫](https://azure.microsoft.com/services/mariadb/)是 Azure 雲中完全託管的關係資料庫,即服務。 該服務基於 MariaDB 社群版伺服器引擎。 它能夠處理任務關鍵型工作負載,具有可預測的性能和動態可擴充性。

### <a name="azure-database-for-postgresql"></a>適用於 PostgreSQL 的 Azure 資料庫

[PostgreSQL](https://www.postgresql.org/)是一個開源關係資料庫,擁有超過 30 年的積極發展。 PostgresSQL 在可靠性和數據完整性方面享有盛譽。 它功能豐富、SQL 相容,並且被認為比 MySQL 更具性能- 尤其對於具有複雜查詢和大量寫入的工作負載。 許多大型企業,包括蘋果,紅帽和富士通已經建立了產品使用PostgreSQL。

[基於開源 Postgres 資料庫引擎的 PostgreSQL Azure 資料庫](https://azure.microsoft.com/services/postgresql/)是一個完全託管的關係資料庫服務。 該服務支援許多開發平臺,包括C++、JAVA、Python、Node、C\#和 PHP。 您可以使用[命令列介面](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1)工具或 Azure 資料遷移服務將 PostgreSQL 資料庫遷移到該資料庫。

用於 PostgreSQL 的 Azure 資料庫提供兩個部署選項:

- [單伺服器](https://docs.microsoft.com/azure/postgresql/concepts-servers)部署選項是多個資料庫的中心管理點,您可以向其部署多個資料庫。 定價基於內核和存儲,按伺服器進行結構化。

- [超大規模 (Citus) 選項](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/)由 Citus 數據技術提供支援。 通過跨數百個節點*水平擴展*單個資料庫,實現高性能,從而提供快速性能和擴展。 此選項允許引擎在記憶體中容納更多數據,跨數百個節點並行化查詢,並更快地索引數據。

## <a name="nosql-data-in-azure"></a>Azure 中的無 SQL 資料

Cosmos DB 是 Azure 雲中完全託管的全域分佈的 NoSQL 資料庫服務。 它已被世界各地的許多大公司採用,包括可口可樂、Skype、埃克森美孚和自由互助。

如果您的服務需要來自世界任何地方的快速回應、高可用性或彈性可擴充性,Cosmos DB 是一個很好的選擇。 圖 5-12 顯示了宇宙 DB。

![宇宙 DB 概述](./media/cosmos-db-overview.png)

**圖5-12**:宇宙DB概述

上圖顯示了Cosmos DB中可用的許多內置雲原生功能。 在本節中,我們將仔細研究它們。

### <a name="global-support"></a>全球支援

雲原生應用程式通常具有全球受眾,需要全球擴展。

您可以跨地區或在世界各地分發Cosmos資料庫,將資料放在使用者附近,縮短回應時間並減少延遲。 您可以在不暫停或重新部署服務的情況下從區域添加或刪除資料庫。 在後台,Cosmos DB 透明地將資料複製到每個配置的區域。

Cosmos DB 支援全域等級的[活動/主動](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/)群集,讓您能夠設定任何資料庫區域以支援*寫入和讀取*。

[多主協定](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits)是 Cosmos DB 中的一個重要功能,可實現以下功能:

- 無限的彈性寫入和讀取可擴充性。

- 在世界各地具有 99.999% 的讀取和寫入可用性。

- 保證讀取和寫入會以第 99 百分位數且小於 10 毫秒的方式提供服務。

使用Cosmos DB[多宿主API,](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)微服務會自動知道最近的Azure區域並向其發送請求。 最近的區域由Cosmos DB識別,無需進行任何配置更改。 如果區域不可用,多宿主功能將自動將請求路由到下一個最近的可用區域。

### <a name="multi-model-support"></a>多型號支援

將單片應用程式重新程式設計到雲端原生體系結構時,開發團隊有時必須遷移開源 NoSQL 資料儲存。 Cosmos DB 可説明您透過其*多模型*資料平臺在這些NoSQL資料儲存中保留投資。 圖 5-13 顯示支援的 NoSQL[相容性 API](https://www.wikiwand.com/en/Cosmos_DB)。

![宇宙資料庫提供者](./media/cosmos-db-providers.png)

**圖 5-13**: 宇宙資料庫提供者

開發團隊可以將現有的蒙戈、格雷姆林或卡桑德拉資料庫遷移到 Cosmos DB,只需對數據或代碼進行最少的更改。 對於新應用,開發團隊可以選擇開源選項或內建 SQL API 模型。

> 在內部,Cosmos 以由原始數據類型組成的簡單結構格式存儲數據。 對於每個請求,資料庫引擎都會將原始數據轉換為您選擇的模型表示形式。

在上圖 5-13 中,請注意[表 API](https://docs.microsoft.com/azure/cosmos-db/table-introduction)選項。 此 API 是 Azure 表存儲的演變。 兩者共用相同的基礎表模型,但 Cosmos DB 表 API 添加了 Azure 儲存 API 中不可用的進階增強功能。 這些功能在圖 5-4 中進行了對比。

![Azure 資料表 API](media/azure-table-api.png)

**圖 5-14**: Azure 表 API 提供者

使用 Azure 表儲存的微服務可以輕鬆地遷移到 Cosmos DB 表 API。 不需要變更程式碼。

### <a name="tunable-consistency"></a>可調一致性

在 *"關係與NoSQL"* 部分的早些時候,我們討論了*數據一致性*的主題。 資料一致性是指資料*的完整性*。 具有分散式數據的雲原生服務依賴於複製,必須在讀取一致性、可用性和延遲之間做出根本性的權衡。

大多數分散式資料庫允許開發人員在兩種一致性模型之間進行選擇:強一致性和最終一致性。 *強一致性*是數據可程式設計性的黃金標準。 它保證查詢將始終返回最新的資料 - 即使系統必須產生延遲等待更新在所有資料庫副本之間複製。 雖然為*最終一致性*配置的資料庫將立即返回數據,即使該數據不是最新的副本。 后一個選項可實現更高的可用性、更大的規模和更高的性能。

Azure Cosmos DB 提供圖 5-15 所示的五個定義良好的[一致性模型](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)。

![宇宙 DB 一致性圖](./media/cosmos-consistency-level-graph.png)

**圖 5-15**: 宇宙 DB 一致性等級

 這些選項使您能夠對資料的一致性、可用性和性能做出精確的選擇和精細權衡。 圖 5-16 描述了每個級別。

![宇宙資料庫一致性等級](./media/cosmos-db-consistency-levels.png)

**圖 5-16**: 宇宙 DB 一致性級別描述

在["9球背後:宇宙DB一致性水平解釋"](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)一文中,微軟雲開發者宣導者Jeremy Likeness對五種模型給出了極好的解釋。

### <a name="partitioning"></a>資料分割

Azure Cosmos DB 採用自動[分區](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview)來擴展資料庫以滿足雲原生服務的性能需求。

通過創建資料庫、容器和項來管理 Cosmos DB 資料中的數據。

容器位於Cosmos DB資料庫中,表示與架構無關的專案分組。 項是添加到容器中的數據。 它們表示為文檔、行、節點或邊。 添加到容器的所有專案都將自動編制索引。

要對容器進行分區,項被劃分為稱為邏輯分區的不同子集。 邏輯分區是根據與容器中的每個項關聯的分區鍵的值填充的。 圖 5-18 顯示了兩個容器,每個容器都有一個基於分區鍵值的邏輯分區。

![宇宙資料庫分割區機制](./media/cosmos-db-partitioning.png)

**圖 5-18**: 宇宙 DB 分割區機制

請注意,在上圖中,每個專案如何包含"城市"或"機場"的分區鍵。 鍵確定項的邏輯分區。 帶有城市代碼的專案將分配給左側的容器,以及帶有機場代碼的專案分配給右側的容器。 將分區鍵值與 ID 值合併將創建項的索引,該索引唯一地標識項。

在內部,Cosmos DB 自動管理[物理分區上的邏輯分區](https://docs.microsoft.com/azure/cosmos-db/partition-data)放置,以滿足容器的可伸縮性和性能需求。 隨著應用程式輸送量和存儲要求的提高,Azure Cosmos DB 會跨更多伺服器重新分發邏輯分區。 重新分發操作由 Cosmos DB 管理,並在不中斷或停機的情況下調用。

## <a name="newsql-databases"></a>新增 SQL 資料庫

*NewSQL* 是一種新興的資料庫技術,它將NoSQL的分散式可擴充性與關係資料庫的ACID保證相結合。 NewSQL 資料庫對於必須在分散式環境中處理大量數據的業務系統非常重要,這些系統具有完全的事務支援和 ACID 合規性。 雖然 NoSQL 資料庫可以提供海量可伸縮性,但它不能保證數據一致性。 數據不一致的間歇性問題可能會給開發團隊帶來負擔。 開發人員必須在微服務代碼中構造安全措施,以管理由不一致數據引起的問題。

雲原生計算基礎 (CNCF) 具有多個新 SQL 資料庫專案。

| 隨附此逐步解說的專案 | 特性 |
| :-------- | :-------- |
| 蟑螂 DB |符合 ACID 的、全域擴展的關係資料庫。 向群集添加新節點,而 CockroachDB 負責平衡跨實例和地理位置的數據。 它創建、管理和分發副本以確保可靠性。 它是開源的,免費提供。  |
| 提亞布 | 支援混合事務和分析處理 (HTAP) 工作負載的開源資料庫。 它與 MySQL 相容,具有水準可擴充性、強一致性和高可用性。  TiDB 充當 MySQL 伺服器。 您可以繼續使用現有的 MySQL 用戶端庫,而無需對應用程式進行大量代碼更改。 |
| 尤加位元組開發銀行 | 開源、高性能、分散式 SQL 資料庫。 它支援低查詢延遲、抵禦故障的彈性和全域數據分發。 YugabyDB 與後回歸 SQL 相容,可處理橫向擴展 RDBMS 和 Internet 規模 OLTP 工作負載。 該產品還支援NoSQL,並與卡桑德拉相容。 |
|維特斯 | ViTES 是一種資料庫解決方案,用於部署、縮放和管理大型 MySQL 實例群集。 它可以在公共或私有雲體系結構中運行。 它結合了並擴展了許多重要的 MySQL 功能,並具有垂直和水準分片支援功能。 Vites源自YouTube,自2011年以來一直提供所有YouTube資料庫流量。 |

上圖中的開源專案可從雲原生計算基金會獲得。 其中三種產品是完整的資料庫產品,其中包括 .NET Core 支援。 另一個 Vites 是一個資料庫群集系統,它水準縮放 MySQL 實例的大型群集。

NewSQL 資料庫的關鍵設計目標是利用平臺的彈性和可擴充性,在 Kubernetes 中本機工作。

NewSQL 資料庫旨在在短暫的雲環境中蓬勃發展,在臨時雲環境中,基礎虛擬機可在接到通知后立即重新啟動或重新安排。 資料庫旨在抵禦節點故障,而不會丟失數據或停機。 例如,CockroachDB 通過在群集中的節點上維護任何數據的三個一致副本,能夠經受住電腦損失。

Kubernetes 使用*服務建構*允許用戶端從單個 DNS 條目處理一組相同的 NewSQL 資料庫進程。 通過將資料庫實例與與其關聯的服務位址分離,我們可以在不中斷現有應用程序實例的情況下進行擴展。 在給定時間向任何服務發送請求將始終產生相同的結果。

在這種情況下,所有資料庫實例都是相等的。 沒有主關係或次要關係。 在 CockroachDB 中找到*的協商一致複製*等技術允許任何資料庫節點處理任何請求。 如果接收負載平衡請求的節點具有本地所需的數據,它將立即回應。 如果沒有,節點將成為網關,並將請求轉發到相應的節點以獲得正確答案。 從用戶端的角度來看,每個資料庫節點都是一樣的:它們顯示為單個*邏輯*資料庫,具有單機系統的一致性保證,儘管有數十個甚至數百個節點在幕後工作。

有關 NewSQL 資料庫背後的機制的詳細資訊,請參閱[DASH:庫伯內斯-本機資料庫的四個屬性](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)一文。

## <a name="data-migration-to-the-cloud"></a>資料移至雲

更耗時的任務之一是從一個數據平臺將數據遷移到另一個數據平臺。 [Azure 資料遷移服務](https://azure.microsoft.com/services/database-migration/)可説明加快此類工作。 它可以將數據從多個外部資料庫源遷移到 Azure 數據平臺,但停機時間最少。 目標平臺包括以下服務:

- Azure SQL Database
- 適用於 MySQL 的 Azure 資料庫
- 適用於 MariaDB 的 Azure 資料庫
- 適用於 PostgreSQL 的 Azure 資料庫
- CosmosDB
  
該服務提供建議,指導您完成執行遷移所需的更改,無論是小還是大。

>[!div class="step-by-step"]
>[前一個](database-per-microservice.md)
>[下一個](azure-caching.md)
