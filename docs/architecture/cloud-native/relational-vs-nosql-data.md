---
title: 關聯式與NoSQL 資料
description: 瞭解雲端原生應用程式中的關聯式和 NoSQL 資料
author: robvet
ms.date: 05/17/2020
ms.openlocfilehash: 11db5cdca06b9c2c8ce12598456c4b147ac379ba
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434865"
---
# <a name="relational-vs-nosql-data"></a>關聯式與NoSQL 資料

關聯式和 NoSQL 是在雲端原生應用程式中通常會實作為兩種類型的資料庫系統。 它們的建立方式不同，以不同的方式儲存資料，並以不同的方式存取。 在本節中，我們將探討這兩者。 在本章稍後，我們將探討稱為 *NewSQL*的新興資料庫技術。

*關係資料庫* 是數十年來的普遍技術。 這些都是成熟、證明且廣泛實行的。 競爭的資料庫產品、工具和專業知識為數眾多。 關係資料庫會提供相關資料表的存放區。 這些資料表有固定的架構、使用 SQL (結構化查詢語言 (SQL) ) 來管理資料，並支援 ACID 保證。

*無 SQL 資料庫* 是指高效能、非關聯式資料存放區。 他們以易用性、可調整性、彈性和可用性等特性的方式使用 excel。 NoSQL 會儲存非結構化或半結構化的資料，而不是聯結正規化資料的資料表，通常是在機碼值組或 JSON 檔中。 非 SQL 資料庫通常不會提供超過單一資料庫分割範圍的 ACID 保證。 需要第二次回應時間的大量服務需要 NoSQL 資料存放區。

[NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/)技術對於分散式雲端原生系統的影響無法過。 在此空間中，新資料技術的激增，會中斷以獨佔方式依賴關係資料庫的解決方案。

NoSQL 資料庫包含數種不同的模型來存取和管理資料，每個都適合特定的使用案例。 圖5-9 提供四個常見的模型。

![NoSQL 資料模型](./media/types-of-nosql-datastores.png)

**圖 5-9**： NoSQL 資料庫的資料模型

| 型號 | 特性 |
| :-------- | :-------- |
| 文件存放區 | 資料和中繼資料會以階層方式儲存在資料庫內以 JSON 為基礎的檔中。 |
| 機碼值存放區 | NoSQL 資料庫最簡單的資料會以索引鍵/值組的集合表示。 |
| Wide-Column 存放區 | 相關資料會以一組嵌套索引鍵/值組的形式儲存在單一資料行中。 |
| 圖形存放區 | 資料會以節點、邊緣和資料屬性的形式儲存在圖形結構中。 |

## <a name="the-cap-theorem"></a>端點定理

若要瞭解這些資料庫類型之間的差異，請考慮 CAP 定理，這是一組套用至儲存狀態之分散式系統的原則。 圖5-10 顯示端點定理的三個屬性。

![CAP 定理](./media/cap-theorem.png)

**圖 5-10**。 端點定理

定理指出分散式資料系統將會提供一致性、可用性和分割區容錯之間的取捨。 而且，任何資料庫都只能保證三個屬性的其中 *兩個* ：

- *一致性。* 叢集中的每個節點都會以最新的資料回應，即使系統必須封鎖要求，直到所有複本更新為止。 如果您針對目前正在更新的專案查詢「一致的系統」，您將會等候該回應，直到所有複本都成功更新為止。 不過，您將會收到最新的資料。

- *可用 性。* 每個節點都會傳回立即回應，即使該回應不是最新的資料。 如果您查詢「可用的系統」以取得正在更新的專案，您將會得到最可能的答案，也就是服務可以在當時提供的答案。

- *資料分割容錯。* 保證即使複寫的資料節點失敗或失去與其他複寫資料節點的連接，系統仍會繼續運作。

關係資料庫通常會提供一致性和可用性，但不會提供資料分割容錯。 它們通常會布建到單一伺服器，並藉由將更多資源新增至電腦來垂直調整。

許多關係資料庫系統都支援內建的複寫功能，也就是可以對其他次要伺服器實例建立主資料庫的複本。 系統會對主要實例進行寫入作業，並將其複寫到每個次要複本。 失敗時，主要實例可以容錯移轉至次要資料庫，以提供高可用性。 次要複本也可以用來散發讀取作業。 雖然寫入作業一律會針對主要複本進行，但是讀取作業可以路由傳送至任何次要複本，以減少系統負載。

資料也可以跨多個節點進行水準分割，例如使用 [分區化](/azure/sql-database/sql-database-elastic-scale-introduction)。 但是，分區化會在無法輕鬆通訊的許多片段之間分隔資料，以大幅增加作業的額外負荷。 管理成本可能很高且耗時。 最後可能會影響效能、資料表聯結和參考完整性。

如果資料複本在「高度一致」的關係資料庫叢集中遺失網路連線能力，您將無法寫入資料庫。 系統會拒絕寫入作業，因為它無法將變更複寫到其他資料複本。 每個資料複本都必須更新，才能完成交易。

NoSQL 資料庫通常會支援高可用性和資料分割容錯。 它們會水準水準延展，通常是在商用伺服器上進行擴充。 這種方法可讓您以較低的成本，在地理區域內和跨地區提供極高的可用性。 您可以在這些機器或節點之間分割及複寫資料，以提供冗余和容錯功能。 缺點是一致的。 變更一個 NoSQL 節點上的資料可能需要一些時間才能傳播到其他節點。 一般來說，NoSQL 資料庫節點會提供對查詢的立即回應，即使呈現的資料已過時且尚未更新也是一樣。

如果資料複本遺失「高可用性」 NoSQL 資料庫叢集中的連線能力，您仍然可以完成對資料庫的寫入操作。 資料庫叢集會允許寫入作業，並在每個資料複本可用時加以更新。

這類結果稱為「最終一致性」，這是不支援 ACID 交易的分散式資料系統特性。 這是資料項目目更新與將該更新傳播到每個複本節點所需的時間之間的短暫延遲。 在正常狀況下，延遲通常很短，但在發生問題時可能會增加。 例如，如果您要更新美國 NoSQL 資料庫中的產品專案，並且從歐洲的複本節點查詢相同資料項目時，會發生什麼事？ 您會收到先前的產品資訊，直到叢集以產品變更更新歐洲節點為止。 藉由立即傳回查詢結果，而不是等待所有複本節點進行更新，您可以取得龐大的規模和量，但有可能呈現較舊的資料。

高可用性和大規模的擴充性對於企業來說，通常比強式一致性更為重要。 開發人員可以實行 Sagas 故事、CQRS 和非同步訊息等技術與模式，以採用最終一致性。

> 現今，在考慮 CAP 定理條件約束時必須小心。 有一種新的資料庫類型，稱為 NewSQL，它會擴充關係資料庫引擎，以同時支援 NoSQL 系統的水準擴充性和可調整的效能。

## <a name="considerations-for-relational-vs-nosql-systems"></a>關聯式與 NoSQL 系統的考慮

根據特定的資料需求，雲端原生的微服務可以執行關聯式、NoSQL 資料存放區或兩者。

|  當下列情況時，請考慮 NoSQL 資料存放區： | 當下列情況時，請考慮關係資料庫： |
| :-------- | :-------- |
| 您的大量工作負載需要大規模 | 您的工作負載磁片區一致，需要中型到大型規模 |
| 您的工作負載不需要 ACID 保證 |  需要 ACID 保證 |
| 您的資料是動態且經常變更 | 您的資料是可預測且高度結構化 |
| 資料可以不具關聯性表示 | 資料的最佳表示 relationally |  
| 您需要快速寫入和寫入安全性並不重要 | 需要撰寫安全性 |  
| 資料抓取很簡單，且通常是一般的 | 您使用複雜的查詢和報表|
| 您的資料需要廣泛的地理分佈 | 您的使用者更集中 |
| 您的應用程式將會部署到商用硬體，例如使用公用雲端 | 您的應用程式將會部署到大型、高階硬體 |

在接下來的幾節中，我們將探索 Azure 雲端中可用的選項，以儲存和管理您的雲端原生資料。

## <a name="database-as-a-service"></a>資料庫為服務

若要開始，您可以布建 Azure 虛擬機器，並為每個服務安裝您選擇的資料庫。 雖然您可以完全掌控您的環境，但您會放棄雲端平臺的許多內建功能。 您也必須負責管理每個服務的虛擬機器和資料庫。 這種方法很快就會耗費時間和成本。

取而代之的是，雲端原生應用程式偏好以 [資料庫即服務形式 ](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/)公開的資料服務 (DBaaS) 。 這些服務完全由雲端廠商管理，提供內建的安全性、擴充性和監視功能。 您只需將服務作為 [支援服務](./definition.md#backing-services)使用，而不是擁有服務。 此提供者會大規模地操作資源，並承擔效能和維護的責任。

您可以跨雲端可用性區域和區域設定這些設定，以達成高可用性。 它們全都支援即時容量和隨用隨付模型。 Azure 具有不同種類的受控資料服務選項，每個選項都有特定的優點。

我們會先查看 Azure 中可用的關聯式 DBaaS 服務。 您會看到 Microsoft 的旗艦 SQL Server 資料庫與數個開放原始碼選項搭配使用。 然後，我們將討論 Azure 中的 NoSQL 資料服務。

## <a name="azure-relational-databases"></a>Azure 關係資料庫

對於需要關聯式資料的雲端原生微服務，Azure 提供四個受控關係資料庫即服務 (DBaaS) 供應專案，如圖5-11 所示。

![Azure 中的受控關係資料庫](./media/azure-managed-databases.png)

**圖 5-11**。 Azure 中可用的受控關係資料庫

在上圖中，請注意，每一個都位於一般的 DBaaS 基礎結構上，其具有不需額外成本的重要功能。

這些功能對於布建大量資料庫，但具有有限資源來管理這些資料庫的組織而言尤其重要。
您可以藉由選取處理核心、記憶體和基礎儲存體的數量，在幾分鐘內布建 Azure 資料庫。 您可以即時調整資料庫，並以幾乎不停機的方式動態調整資源。

## <a name="azure-sql-database"></a>Azure SQL Database

具有 Microsoft SQL Server 專長的開發小組應該考慮 [Azure SQL Database](/azure/sql-database/)。 它是完全受控的關係資料庫即服務， (根據 Microsoft SQL Server 資料庫引擎 DBaaS) 。 服務會共用 SQL Server 內部部署版本中的許多功能，並執行 SQL Server 資料庫引擎的最新穩定版本。

適用于雲端原生微服務的 Azure SQL Database 可透過三種部署選項來使用：

- 單一資料庫代表在 Azure 雲端的 [Azure SQL Database 伺服器](/azure/sql-database/sql-database-servers) 上執行的完全受控 SQL Database。 資料庫會被視為 [*包含*](/sql/relational-databases/databases/contained-databases) ，因為它在基礎資料庫伺服器上沒有設定相依性。
  
- [受控執行個體](/azure/sql-database/sql-database-managed-instance)是 Microsoft SQL Server 資料庫引擎的完全受控實例，可提供與內部部署 SQL Server 接近100% 的相容性。 此選項支援較大的資料庫（最多 35 TB），並放在 [Azure 虛擬網路](/azure/virtual-network/virtual-networks-overview) 中，以獲得更好的隔離。

- [Azure SQL Database 無伺服器](/azure/sql-database/sql-database-serverless) 是單一資料庫的計算層，可根據工作負載需求自動調整規模。 它只會針對每秒使用的計算量計費。 這項服務非常適合具有間歇、無法預測的使用模式的工作負載，並與非使用中的時間間隔。 無伺服器計算層也會在非使用期間自動暫停資料庫，因此只會收取儲存體費用。 它會在活動傳回時自動繼續。

除了傳統的 Microsoft SQL Server 堆疊之外，Azure 也提供三個熱門開放原始碼資料庫的受控版本。

## <a name="open-source-databases-in-azure"></a>Azure 中的開放原始碼資料庫

開放原始碼關係資料庫已成為適用于雲端原生應用程式的熱門選擇。 許多企業都優先于商務資料庫產品，特別是為了節省成本。 許多開發團隊都享有其彈性、支援社區的開發，以及工具和擴充功能的生態系統。 開放原始碼資料庫可跨多個雲端提供者部署，協助將「廠商鎖定」的顧慮降至最低。

開發人員可以輕鬆地自我裝載 Azure VM 上的任何開放原始碼資料庫。 雖然提供完整控制權，但這種方法可讓您將資料庫和 VM 的管理、監視和維護進行攔截。

不過，Microsoft 藉由提供數個熱門的開放原始碼資料庫做為 *完全受控* 的 DBaaS 服務，繼續承諾讓 Azure 成為「開放平臺」。

### <a name="azure-database-for-mysql"></a>適用於 MySQL 的 Azure 資料庫

[MySQL](https://en.wikipedia.org/wiki/MySQL) 是開放原始碼關係資料庫，也是以 [燈泡軟體堆疊](https://en.wikipedia.org/wiki/LAMP_(software_bundle))為基礎的應用程式要件。 廣泛為大量 *讀取* 的工作負載選擇，包括 Facebook、Twitter 和 YouTube 在內的許多大型組織都會使用它。 您可以免費使用該社區版，而 enterprise edition 則需要購買授權。 此產品最初是在1995中建立的，在2008中是由 Sun Microsystems 購買。 Oracle 在2010中取得 Sun 和 MySQL。

[適用於 MySQL 的 Azure 資料庫](https://azure.microsoft.com/services/mysql/) 是以開放原始碼 MySQL 伺服器引擎為基礎的受控關係資料庫服務。 它會使用 MySQL 的社區版。 Azure MySQL 伺服器是服務的管理點。 它與用於內部部署的 MySQL 伺服器引擎相同。 引擎可以針對每個伺服器建立單一資料庫，或為每個共用資源的伺服器建立多個資料庫。 您可以繼續使用相同的開放原始碼工具來管理資料，而不需要學習新技能或管理虛擬機器。

### <a name="azure-database-for-mariadb"></a>適用於 MariaDB 的 Azure 資料庫

[適用于 mariadb](https://mariadb.com/) 伺服器是另一個受歡迎的開放原始碼資料庫伺服器。 當 Oracle 購買 Sun Microsystems （擁有 MySQL）時，它會建立為 MySQL 的 *分支* 。 其目的是要確保適用于 mariadb 保持開放原始碼。 由於適用于 mariadb 是 MySQL 的分支，資料和資料表定義是相容的，而且用戶端通訊協定、結構和 Api 都是緊密結合。

適用于 mariadb 有一個強大的社區，由許多大型企業使用。 雖然 Oracle 會持續維護、增強及支援 MySQL，但適用于 mariadb foundation 會管理適用于 mariadb，允許對產品和檔的公開投稿。

[適用於 MariaDB 的 Azure 資料庫](https://azure.microsoft.com/services/mariadb/) 是 Azure 雲端中完全受控的關係資料庫即服務。 此服務是以適用于 mariadb 社區 edition 伺服器引擎為基礎。 它可透過可預測的效能和動態擴充性來處理任務關鍵性工作負載。

### <a name="azure-database-for-postgresql"></a>適用於 PostgreSQL 的 Azure 資料庫

[于 postgresql](https://www.postgresql.org/) 是開放原始碼關係資料庫，有超過30多年的積極開發。 PostgresSQL 具有可靠性與資料完整性的強大信譽。 它的功能豐富、符合 SQL 規範，且比 MySQL 更具效能，特別是針對具有複雜查詢和大量寫入的工作負載。 許多大型企業（包括 Apple、Red Hat 和 Fujitsu）都使用於 postgresql 建立了產品。

[適用於 PostgreSQL 的 Azure 資料庫](https://azure.microsoft.com/services/postgresql/) 是完全受控的關係資料庫服務，以開放原始碼 Postgres 資料庫引擎為基礎。 此服務支援許多開發平臺，包括 c + +、JAVA、Python、Node、C \# 和 PHP。 您可以使用 [命令列介面](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) 工具或 Azure 資料移轉服務，將于 postgresql 資料庫移轉至其中。

有兩個部署選項可使用適用於 PostgreSQL 的 Azure 資料庫：

- [單一伺服器](/azure/postgresql/concepts-servers)部署選項是您可以部署多個資料庫的多個資料庫的中央管理點。 定價是根據核心和儲存體，以每一伺服器為基礎進行結構化。

- [超大規模 (Citus) 選項](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/)是由 Citus 資料技術提供技術支援。 它藉由 *水準調整* 數百個節點的單一資料庫，以提供快速的效能和規模，讓效能達到高效能。 此選項可讓引擎在記憶體中容納更多資料、跨數百個節點平行處理查詢，以及更快編制索引資料。

## <a name="nosql-data-in-azure"></a>Azure 中的 NoSQL 資料

Cosmos DB 是 Azure 雲端中完全受控、全域散發的 NoSQL 資料庫服務。 全球各地的許多大型公司都採用了它，包括可哥-Cola、Skype、ExxonMobil 和自由的相互。

如果您的服務需要來自世界各地的快速回應、高可用性或彈性的擴充性，Cosmos DB 是絕佳的選擇。 圖5-12 顯示 Cosmos DB。

![Cosmos DB 總覽](./media/cosmos-db-overview.png)

**圖 5-12**： Cosmos DB 的總覽

上圖顯示 Cosmos DB 中提供的許多內建雲端原生功能。 在本節中，我們將進一步瞭解它們。

### <a name="global-support"></a>全球支援

雲端原生應用程式通常有全球受眾，需要全球規模。

您可以跨區域或世界各地散發 Cosmos 資料庫、將資料放在您的使用者附近、改善回應時間，以及降低延遲。 您可以新增或移除區域中的資料庫，而不需暫停或重新部署您的服務。 在背景中，Cosmos DB 會以透明方式將資料複寫到每個已設定的區域。

Cosmos DB 支援全域層級的 [主動/主動](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) 叢集，可讓您設定任何資料庫區域以 *同時支援寫入和讀取*。

[多](/azure/cosmos-db/multi-master-benefits)宿主通訊協定是 Cosmos DB 中的一項重要功能，可啟用下列功能：

- 無限制的彈性寫入和讀取的擴充性。

- 在世界各地具有 99.999% 的讀取和寫入可用性。

- 保證讀取和寫入會以第 99 百分位數且小於 10 毫秒的方式提供服務。

使用 Cosmos DB [多路連接 api](/azure/cosmos-db/distribute-data-globally)時，您的微服務會自動察覺最接近的 Azure 區域，並將要求傳送給它。 最接近的區域是由 Cosmos DB 識別，不需要任何設定變更。 如果區域變得無法使用，多路連接功能就會自動將要求路由傳送至下一個最接近的可用區域。

### <a name="multi-model-support"></a>多模型支援

將整合型應用程式遷移到雲端原生架構時，開發小組有時必須遷移開放原始碼的 NoSQL 資料存放區。 Cosmos DB 可協助您使用它的 *多模型* 資料平臺，將這些 NoSQL 資料存放區的投資保持在一起。 下表顯示支援的 NoSQL [相容性 api](https://www.wikiwand.com/en/Cosmos_DB)。

| 提供者 | 描述  |
| :-------- | :-------- |
| SQL API | 專屬的 API，可支援 JSON 檔和以 SQL 為基礎的查詢 |
| Mongo DB API | 支援 Mongo DB Api 和 JSON 檔|
| Gremlin API | 支援 Gremlin API 與以圖形為基礎的節點和邊緣資料表示 |
| Cassandra API | 支援適用于寬資料行資料表示的 Casandra API |  
| 資料表 API  | 使用 premium 增強功能支援 Azure 資料表儲存體 |  
| etcd API | 啟用 Cosmos DB 作為 Azure Kubernetes Service 叢集的備份存放區 |

開發小組可以將現有的 Mongo、Gremlin 或 Cassandra 資料庫移轉至 Cosmos DB，只要對資料或程式碼進行極短的變更即可。 針對新的應用程式，開發小組可以在開放原始碼選項或內建的 SQL API 模型中選擇。

> 就內部而言，Cosmos 會以基本資料類型所組成的簡單結構格式來儲存資料。 針對每個要求，資料庫引擎會將基本資料轉譯為您所選取的模型標記法。

在上表中，請注意 [資料表 API](/azure/cosmos-db/table-introduction) 選項。 此 API 是 Azure 資料表儲存體的演進。 兩者都會共用相同的基礎資料表模型，但 Cosmos DB 資料表 API 會新增 Azure 儲存體 API 中未提供的 premium 增強功能。 下表會對照這些功能。

|  | Azure 表格儲存體  | Azure Cosmos DB  |
| :-------- | :-------- |:-------- |
| Latency | 快速 | 在世界各地讀取和寫入的一位數毫秒延遲 |
| 輸送量 | 每個資料表的20000作業限制 | 每個資料表10000000個作業 |
| 全域散發 | 具有選擇性單一次要讀取區域的單一區域 | 具有自動容錯移轉的所有區域的通行分佈 |
| 編製索引 | 僅適用于分割區和資料列索引鍵屬性 | 自動編制所有屬性的索引 |
| 定價 | 以儲存體為基礎 | 根據輸送量 |

使用 Azure 資料表儲存體的微服務可輕鬆地遷移至 Cosmos DB 資料表 API。 不需要變更程式碼。

### <a name="tunable-consistency"></a>可調整的一致性

稍早在 *關聯式與 NoSQL* 區段中，我們討論了 *資料一致性*的主體。 資料一致性指的是資料的 *完整性* 。 具有分散式資料的雲端原生服務依賴複寫，而且必須在讀取一致性、可用性和延遲之間進行基本取捨。

大部分的分散式資料庫可讓開發人員在兩個一致性模型之間做選擇：強式一致性和最終一致性。 *強式一致性* 是資料可程式性的黃金標準。 它保證查詢一律會傳回最新的資料，即使系統必須產生等待更新複寫到所有資料庫複本的延遲。 如果設定為 *最終一致性* 的資料庫會立即傳回資料，即使該資料不是最新的複本。 第二個選項可提供更高的可用性、更高的規模和更高的效能。

Azure Cosmos DB 提供五個定義完善的 [一致性模型](/azure/cosmos-db/consistency-levels) ，如圖5-13 所示。

![Cosmos DB 一致性圖形](./media/cosmos-consistency-level-graph.png)

**圖 5-13**： Cosmos DB 一致性層級

 這些選項可讓您針對一致性、可用性和資料的效能進行精確的選擇和細微的權衡取捨。 下表會顯示這些層級。

| 一致性層級 | 描述  |
| :-------- | :-------- |
| 最終 | 讀取沒有排序保證。 複本最終將會聚合。 |
| 常數前置詞 | 讀取仍是最終的，但資料會依照寫入的順序傳回。 |
| 工作階段 | 保證您可以讀取目前會話期間所寫入的任何資料。 這是預設的一致性層級。 |
| 限定過期 | 讀取以您指定的間隔寫入記錄。 |  
| 強式  | 保證讀取會傳回專案的最新認可版本。 用戶端永遠不會看到未認可或部分讀取。 |  

在《 [9 球後方： Cosmos DB 一致性層級](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)的文章中，Microsoft Program Manager Jeremy Likness 提供五個模型的絕佳說明。

### <a name="partitioning"></a>資料分割

Azure Cosmos DB 採用自動 [分割](/azure/cosmos-db/partitioning-overview) 來調整資料庫，以符合雲端原生服務的效能需求。

您可以藉由建立資料庫、容器和專案來管理 Cosmos DB 資料中的資料。

容器會存留在 Cosmos DB 資料庫中，並代表與架構無關的專案群組。 專案是您新增至容器的資料。 它們是以檔、資料列、節點或邊緣表示。 新增至容器的所有專案都會自動編制索引。

若要分割容器，專案會分割成不同的子集，稱為邏輯分割區。 邏輯分割區會根據與容器中每個專案相關聯的分割區索引鍵值來填入。 圖5-14 顯示兩個容器，每個容器都有以分割區索引鍵值為基礎的邏輯分割區。

![Cosmos DB 資料分割機制](./media/cosmos-db-partitioning.png)

**圖 5-14**： Cosmos DB 資料分割機制

請注意，在上圖中，每個專案都包含「城市」或「機場」的分割區索引鍵。 索引鍵會決定專案的邏輯分割區。 具有城市代碼的專案會指派給左邊的容器，並將具有機場程式碼的專案指派給右邊的容器。 結合資料分割索引鍵值與識別碼值會建立可唯一識別專案的專案索引。

Cosmos DB 會在內部自動管理實體分割區上的 [邏輯](/azure/cosmos-db/partition-data) 分割區位置，以滿足容器的擴充性和效能需求。 隨著應用程式輸送量和存放裝置需求的增加，Azure Cosmos DB 會將邏輯磁碟分割分散到更多伺服器。 重新發佈作業是由 Cosmos DB 管理，並在不中斷或停機的情況下叫用。

## <a name="newsql-databases"></a>NewSQL 資料庫

*NewSQL* 是一種新興的資料庫技術，將 NoSQL 的分散式擴充性與關係資料庫的 ACID 保證結合在一起。 NewSQL 資料庫對於必須跨分散式環境處理大量資料的商務系統而言很重要，並具備完整的交易式支援和 ACID 合規性。 雖然 NoSQL 資料庫可提供大規模的擴充性，但不保證資料的一致性。 不一致資料的間歇性問題可能會對開發小組造成負擔。 開發人員必須在其微服務程式代碼中設計防護措施，以管理不一致資料所造成的問題。

雲端原生運算基礎 (CNCF) 提供數個 NewSQL 資料庫專案的功能。

| Project | 特性 |
| :-------- | :-------- |
| Cockroach DB |符合 ACID 規範的關係資料庫，可進行全域調整。 將新節點新增至叢集，CockroachDB 會負責平衡實例和地理位置之間的資料。 它會建立、管理及散發複本，以確保可靠性。 它是開放原始碼且可免費使用。  |
| TiDB | 支援混合式交易和分析處理 (HTAP) 工作負載的開放原始碼資料庫。 它是 MySQL 相容的功能，可提供水準擴充性、強式一致性和高可用性。  TiDB 的作用就像是 MySQL 伺服器。 您可以繼續使用現有的 MySQL 用戶端程式庫，而不需要對應用程式進行大量的程式碼變更。 |
| YugabyteDB | 開放原始碼、高效能的分散式 SQL database。 它支援低查詢延遲、可因應失敗的恢復功能，以及全域資料散發。 YugabyteDB 與 PostgressSQL 相容，並且會處理相應放大 RDBMS 和網際網路規模的 OLTP 工作負載。 此產品也支援 NoSQL 並且與 Cassandra 相容。 |
|Vitess | Vitess 是一種資料庫解決方案，可用於部署、調整及管理大型的 MySQL 實例叢集。 它可以在公用或私用雲端架構中執行。 Vitess 結合和延伸許多重要的 MySQL 功能，以及垂直和水準分區化支援的功能。 由 YouTube 產生，Vitess 自2011起提供所有 YouTube 資料庫流量。 |

上圖中的開放原始碼專案可從雲端原生運算基礎進行取得。 其中有三個供應專案是完整的資料庫產品，包括 .NET Core 支援。 另一種是 Vitess，它是一種資料庫群集系統，可水準調整大型的 MySQL 實例叢集。

NewSQL 資料庫的主要設計目標是要在 Kubernetes 中以原生方式運作，並利用平臺的復原能力和擴充性。

NewSQL 資料庫的設計目的是要在暫時雲端環境中，重新開機或重新排程底層的虛擬機器。 這些資料庫的設計是為了在不遺失資料或停機的情況下，在節點失敗的情況下 例如，CockroachDB 藉由在叢集中的各個節點上維護三個一致的資料複本，來維持電腦遺失的能力。

Kubernetes 會使用 *服務結構* ，以允許用戶端從單一 DNS 專案定址一組相同的 NewSQL 資料庫處理常式。 藉由將資料庫實例與相關聯之服務的位址分離，我們就可以調整，而不會中斷現有的應用程式實例。 在指定時間將要求傳送至任何服務時，一律會產生相同的結果。

在此案例中，所有資料庫實例都相等。 沒有主要或次要關聯性。 在 CockroachDB 中找到的 *共識* 複寫之類的技術，可讓任何資料庫節點處理任何要求。 如果接收負載平衡要求的節點具有在本機所需的資料，則會立即回應。 如果沒有，節點就會變成閘道，並將要求轉送至適當的節點，以取得正確的答案。 從用戶端的觀點來看，每個資料庫節點都是相同的：它們會顯示為具有單一電腦系統一致性保證的單一 *邏輯* 資料庫，儘管有數十個或甚至數百個節點在幕後運作。

若要深入瞭解 NewSQL 資料庫背後的機制，請參閱 [虛線： Kubernetes-Native 資料庫的四個屬性](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) 文章。

## <a name="data-migration-to-the-cloud"></a>資料移轉至雲端

更耗時的工作之一，就是將資料從一個資料平臺遷移到另一個。 [Azure 資料移轉服務](https://azure.microsoft.com/services/database-migration/)可協助加速這類工作。 它可以將數個外部資料庫來源的資料移轉到 Azure 資料平臺，將停機時間降到一。 目標平臺包括下列服務：

- Azure SQL Database
- 適用於 MySQL 的 Azure 資料庫
- 適用於 MariaDB 的 Azure 資料庫
- 適用於 PostgreSQL 的 Azure 資料庫
- CosmosDB
  
此服務會提供建議以引導您完成執行遷移（小型或大型）所需的變更。

>[!div class="step-by-step"]
>[上一個](distributed-data.md) 
>[下一步](azure-caching.md)
