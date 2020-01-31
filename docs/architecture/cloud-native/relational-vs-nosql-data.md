---
title: 關聯式與 NoSQL 資料的比較
description: 瞭解雲端原生應用程式中的關聯式和 NoSQL 資料
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 5ca40791f6c6a3d04f3a7d7d9d2dbf0f23196f8f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794916"
---
# <a name="relational-vs-nosql-data"></a>關聯式與 NoSQL 資料的比較

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

關聯式和 NoSQL 是在雲端原生應用程式中，通常會實作為兩種類型的資料庫系統。 它們會以不同的方式建立、以不同的方式儲存資料，並以不同方式存取。 在本節中，我們將探討這兩者。 在本章稍後，我們將探討名為*NewSQL*的新興資料庫技術。

*關係資料庫*是數十年的普遍技術。 這些是成熟、經過證明且廣泛實行的。 競爭資料庫產品、工具和專業知識為數眾多。 關係資料庫會提供相關資料表的存放區。 這些資料表具有固定的架構，使用 SQL （結構化查詢語言 (SQL)）來管理資料，並支援 ACID 保證。

*無-SQL 資料庫*會參考高效能、非關聯式資料存放區。 他們在 excel 中使用易用性、擴充性、彈性和可用性等特性。 NoSQL 不會聯結正規化資料的資料表，而是儲存非結構化或半結構化資料，通常是在索引鍵/值組或 JSON 檔中。 無-SQL 資料庫通常不會提供超出單一資料庫分割範圍的 ACID 保證。 需要次要秒數回應時間的高容量服務，傾向于 NoSQL 資料存放區。

無法十分出色分散式雲端原生系統的[NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/)技術影響。 這個空間中的新資料技術激增，有一次只依賴關係資料庫而中斷的解決方案。

NoSQL 資料庫包含數種不同的模型，可用於存取和管理資料，每個都適用于特定的使用案例。 圖5-9 顯示四個常見的模型。

![NoSQL 資料模型](./media/types-of-nosql-datastores.png)

**圖 5-9**： NoSQL 資料庫的資料模型

| 型號 | 特性 |
| :-------- | :-------- |
| 檔存放區 | 資料和中繼資料會以階層方式儲存在資料庫內以 JSON 為基礎的檔中。 |
| 金鑰值存放區 | 最簡單的 NoSQL 資料庫，資料會以索引鍵/值組的集合表示。 |
| 寬資料行存放區 | 相關資料會以一組嵌套索引鍵/值配對的形式儲存在單一資料行中。 |
| 圖形存放區 | 資料會儲存在圖形結構中，做為節點、邊緣和資料屬性。 |

## <a name="the-cap-theorem"></a>CAP 定理

若要瞭解這些資料庫類型之間的差異，請考慮 CAP 定理，這是一組套用至儲存狀態之分散式系統的原則。 圖5-10 顯示 CAP 定理的三個屬性。

![CAP 定理](./media/cap-theorem.png)

**圖 5-10**。 CAP 定理

定理說明分散式資料系統會在一致性、可用性及分割區容錯之間提供取捨。 而且，任何資料庫都只能保證三個屬性的其中*兩個*：

- *保證.* 叢集中的每個節點都會以最新的資料回應，即使系統必須封鎖要求，直到所有複本更新為止。 如果您查詢目前正在更新之專案的「一致系統」，您會等待該回應，直到所有複本都成功更新為止。 不過，您將會收到最新的資料。

- *提供.* 每個節點都會傳回立即回應，即使該回應不是最新的資料也一樣。 如果您針對正在更新的專案查詢「可用的系統」，您會收到服務可在當時提供的最佳解答。

- *分割區容錯。* 保證即使複寫的資料節點失敗或失去與其他複寫資料節點的連線，系統仍會繼續運作。

關係資料庫通常會提供一致性和可用性，而不是分割區容錯。 它們通常會布建到單一伺服器，並藉由將更多資源新增至電腦來垂直調整。

許多關係資料庫系統都支援內建複寫功能，其中主資料庫的複本可以對其他次要伺服器實例進行。 寫入作業會對主要實例進行，並複寫到每個次要資料庫。 失敗時，主要實例可以故障切換到次要資料庫，以提供高可用性。 次要複本也可以用來散發讀取作業。 雖然寫入作業一律會針對主要複本進行，但是讀取作業可以路由傳送至任何次要資料庫，以減少系統負載。

資料也可以跨多個節點進行水準分割，例如使用[分區化](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)。 但是，分區化會在多個無法輕鬆通訊的部分分隔資料，大幅增加作業額外負荷。 管理成本可能很高，而且耗時。 最後，它可能會影響效能、資料表聯結和參考完整性。

如果資料複本在「高度一致」的關係資料庫叢集中遺失網路連線，您將無法寫入資料庫。 系統會拒絕寫入作業，因為它無法將該變更複寫到其他資料複本。 在交易完成之前，每個資料複本都必須更新。

NoSQL 資料庫通常會支援高可用性和分割區容錯。 它們會水準相應放大，通常是跨商用伺服器。 這種方法可讓您以更低的成本，在地理區域內外提供極高的可用性。 您可以跨這些機器或節點分割和複寫資料，以提供冗余和容錯功能。 缺點是一致的。 對某個 NoSQL 節點上的資料所做的變更，可能需要一些時間才能傳播至其他節點。 Typically, a NoSQL database node will provide an immediate response to a query - even if the data that is presented is stale and hasn't updated yet.

If data replicas were to lose connectivity in a "highly available" NoSQL database cluster, you could still complete a write operation to the database. The database cluster would allow the write operation and update each data replica as it becomes available.

This kind of result is known as eventual consistency, a characteristic of distributed data systems where ACID transactions aren't supported. It's a brief delay between the update of a data item and time that it takes to propagate that update to each of the replica nodes. Under normal conditions, the lag is typically short, but can increase when problems arise. For example, what would happen if you were to update a product item in a NoSQL database in the United States and query that same data item from a replica node in Europe? You would receive the earlier product information, until the cluster updates the European node with the product change. By immediately returning a query result and not waiting for all replica nodes to update, you gain enormous scale and volume, but with the possibility of presenting older data.

High availability and massive scalability are often more critical to the business than strong consistency. Developers can implement techniques and patterns such as Sagas, CQRS, and asynchronous messaging to embrace eventual consistency.

> Nowadays, care must be taken when conidering the CAP theorem constraints. A new type of database, called NewSQL, has emerged which extends the relational database engine to support both horizontal scalability and the scalable performance of NoSQL systems.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Considerations for relational vs. NoSQL systems

Based upon specific data requirements, a cloud-native-based microservice can implement a relational, NoSQL datastore or both.

|  Consider a NoSQL datastore when: | Consider a relational database when: | 
| :-------- | :-------- |
| You have high volume workloads that require large scale | Your workload volume is consistent and requires medium to large scale |
| Your workloads don't require ACID guarantees |  ACID guarantees are required |
| Your data is dynamic and frequently changes | Your data is predictable and highly structured |
| Data can be expressed without relationships | Data is best expressed relationally |  
| You need fast writes and write safety isn't critical | Write safety is a requirement |  
| Data retrieval is simple and tends to be flat | You work with complex queries and reports|
| Your data requires a wide geographic distribution | Your users are more centralized | 
| Your application will be deployed to commodity hardware, such as with public clouds | Your application will be deployed to large, high-end hardware | 
|||

In the next sections, we'll explore the options available in the Azure cloud for storing and managing your cloud-native data.

## <a name="database-as-a-service"></a>Database as a Service

To start, you could provision an Azure virtual machine and install your database of choice for each service. While you'd have full control over the environment, you'd forgo many built-in features of the cloud platform. You'd also be responsible for managing the virtual machine and database for each service. This approach could quickly become time-consuming and expensive.

Instead, cloud-native applications favor data services exposed as a [Database as a Service (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/). Fully managed by a cloud vendor, these services provide built-in security, scalability, and monitoring. Instead of owning the service, you simply consume it as a [backing service](./definition.md#backing-services). The provider operates the resource at scale and bears the responsibility for performance and maintenance.

They can be configured across cloud availability zones and regions to achieve high availability. They all support just-in-time capacity and a pay-as-you-go model. Azure features different kinds of managed data service options, each with specific benefits.

We'll first look at relational DBaaS services available in Azure. You'll see that Microsoft's flagship SQL Server database is available along with several open-source options. Then, we'll talk about the NoSQL data services in Azure.

## <a name="azure-relational-databases"></a>Azure relational databases

For cloud-native microservices that require relational data, Azure offers four managed relational databases as a service (DBaaS) offerings, shown in Figure 5-11.

![Managed relational databases in Azure](./media/azure-managed-databases.png)

**圖 5-11**。 Managed relational databases available in Azure

In the previous figure, note how each sits upon a common DBaaS infrastructure which features key capabilities at no additional cost.

These features are especially important to organizations who provision large numbers of databases, but have limited resources to administer them.
You can provision an Azure database in minutes by selecting the amount of processing cores, memory, and underlying storage. You can scale the database on-the-fly and dynamically adjust resources with little to no downtime.

## <a name="azure-sql-database"></a>Azure SQL Database

具有 Microsoft SQL Server 專長的開發小組應該考慮[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/)。 它是完全受控的關係資料庫即服務（DBaaS），以 Microsoft SQL Server 資料庫引擎為基礎。 服務會共用在內部部署版本的 SQL Server 中找到的許多功能，並執行 SQL Server 資料庫引擎的最新穩定版本。

若要搭配使用雲端原生微服務，有三個部署選項可提供 Azure SQL Database：

- 單一資料庫代表在 Azure 雲端中的[Azure SQL Database 伺服器](https://docs.microsoft.com/azure/sql-database/sql-database-servers)上執行的完全受控 SQL Database。 資料庫會被視為[*包含*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases)，因為它在基礎資料庫伺服器上沒有任何設定相依性。
  
- [受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)是 Microsoft SQL Server 資料庫引擎的完全受控實例，可提供與內部部署 SQL Server 接近100% 的相容性。 此選項支援較大的資料庫，最高可達 35 TB，並放在[Azure 虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)中，以獲得更好的隔離。

- [Azure SQL Database 無伺服器](https://docs.microsoft.com/azure/sql-database/sql-database-serverless)是單一資料庫的計算層，可根據工作負載需求自動進行調整。 它只會針對每秒使用的計算數量計費。 此服務非常適合具有間歇性、無法預測之使用模式的工作負載，而且會與非使用狀態的期間混合。 無伺服器計算層也會在非使用中期間自動暫停資料庫，因此只會收取儲存體費用。 當活動傳回時，它會自動繼續。

除了傳統的 Microsoft SQL Server 堆疊之外，Azure 也有三個熱門開放原始碼資料庫的受控版本。

## <a name="open-source-databases-in-azure"></a>Azure 中的開放原始碼資料庫

開放原始碼關係資料庫已成為雲端原生應用程式的熱門選擇。 許多企業都傾向于商務資料庫產品，特別是為了節省成本。 許多開發團隊都享有其彈性、支援小組的開發，以及工具和擴充功能的生態系統。 開放原始碼資料庫可以跨多個雲端提供者部署，協助將「廠商鎖定」的顧慮降到最低。

開發人員可以輕鬆自我裝載 Azure VM 上的任何開放原始碼資料庫。 雖然提供完整的控制權，但這種方法會讓您進入攔截，以進行資料庫和 VM 的管理、監視和維護。

不過，Microsoft 會藉由提供數個熱門的開放原始碼資料庫做為*完全受控*的 DBaaS 服務，繼續致力於讓 Azure 成為「開放式平臺」。

### <a name="azure-database-for-mysql"></a>適用於 MySQL 的 Azure 資料庫

[MySQL](https://en.wikipedia.org/wiki/MySQL) 是一個開放原始碼關係資料庫，以及一個以[燈泡軟體堆疊](https://en.wikipedia.org/wiki/LAMP_(software_bundle))為基礎之應用程式的要件。 針對*讀取繁重*的工作負載廣泛選擇，許多大型組織都使用它，包括 Facebook、Twitter 和 YouTube。 此社區版本免費提供，而 enterprise edition 則需要購買授權。 產品原本是在1995中建立的，由 Sun Microsystems 在2008中購買。 Oracle 在2010中取得了 Sun 和 MySQL。

[適用於 MySQL 的 Azure 資料庫](https://azure.microsoft.com/services/mysql/)是以開放原始碼 MySQL 伺服器引擎為基礎的受控關係資料庫服務。 它會使用 MySQL 社區 edition。 Azure MySQL 伺服器是服務的管理點。 它與用於內部部署的 MySQL 伺服器引擎相同。 引擎可以為每個伺服器建立單一資料庫，或為每個共用資源的伺服器建立多個資料庫。 您可以使用相同的開放原始碼工具繼續管理資料，而不需要學習新技能或管理虛擬機器。

### <a name="azure-database-for-mariadb"></a>適用於 MariaDB 的 Azure 資料庫

[適用于 mariadb](https://mariadb.com/)伺服器是另一個熱門的開放原始碼資料庫伺服器。 當 Oracle 購買 Sun Microsystems （擁有 MySQL）時，它會建立為 MySQL 的*分支*。 其目的是要確保適用于 mariadb 保持開放原始碼。 因為適用于 mariadb 是 MySQL 的分支，所以資料和資料表定義相容，而用戶端通訊協定、結構和 Api 則是 knit。

適用于 mariadb 有一個強大的社區，供許多大型企業使用。 雖然 Oracle 會持續維護、增強和支援 MySQL，但適用于 mariadb foundation 會管理適用于 mariadb，以允許對產品和檔進行公開貢獻。

[適用於 MariaDB 的 Azure 資料庫](https://azure.microsoft.com/services/mariadb/)是 Azure 雲端中完全受控的關係資料庫即服務。 此服務是以適用于 mariadb 的「社區版本伺服器引擎」為基礎。 它可以處理任務關鍵性工作負載，並提供可預測的效能和動態擴充性。

### <a name="azure-database-for-postgresql"></a>適用於 PostgreSQL 的 Azure 資料庫

[于 postgresql](https://www.postgresql.org/)是開放原始碼關係資料庫，有超過30年的有效開發。 PostgresSQL 具有可靠性和資料完整性的強式信譽。 它的功能豐富、SQL 相容，而且比 MySQL 更具效能，特別是針對複雜查詢和大量寫入的工作負載。 許多大型企業（包括 Apple、Red Hat 和 Fujitsu）都有使用於 postgresql 的建立產品。

[適用於 PostgreSQL 的 Azure 資料庫](https://azure.microsoft.com/services/postgresql/)是完全受控的關係資料庫服務，以開放原始碼 Postgres 資料庫引擎為基礎。 此服務支援許多開發平臺，包括C++、JAVA、Python、Node、C\#和 PHP。 您可以使用[命令列介面](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1)工具或 Azure 資料移轉服務，將于 postgresql 資料庫移轉至其中。

適用於 PostgreSQL 的 Azure 資料庫提供兩個部署選項： 

- [單一伺服器](https://docs.microsoft.com/azure/postgresql/concepts-servers)部署選項是多個資料庫的中央管理點，您可以在其中部署許多資料庫。 定價是以核心和儲存體為基礎，依伺服器進行結構化。

- [超大規模資料庫（Citus）選項](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/)是由 Citus 資料技術提供技術支援。 藉由在數百個節點間*水準調整*單一資料庫，以提供快速的效能和規模，讓效能達到高效能。 此選項可讓引擎在記憶體中容納更多資料、跨數百個節點平行處理查詢，以及更快編制資料索引。 

## <a name="nosql-data-in-azure"></a>Azure 中的 NoSQL 資料

Cosmos DB 是 Azure 雲端中完全受控的全域分散式 NoSQL 資料庫服務。 世界各地的許多大型公司都採用這種方式，包括可口可樂-Cola、Skype、ExxonMobil 和「自由相互」。

如果您的服務需要來自世界各地、高可用性或彈性擴充性的快速回應，Cosmos DB 是絕佳的選擇。 圖5-12 顯示 Cosmos DB。

![Cosmos DB 總覽](./media/cosmos-db-overview.png)

**圖 5-12**： Cosmos DB 的總覽

上圖顯示 Cosmos DB 中提供的許多內建雲端原生功能。 在本節中，我們將進一步探討它們。

### <a name="global-support"></a>全球支援

雲端原生應用程式通常具有全球物件，而且需要全球規模。

您可以跨區域或全球各地散發 Cosmos 資料庫、將資料放在使用者附近、改善回應時間，並減少延遲。 您可以從區域新增或移除資料庫，而不需暫停或重新部署您的服務。 在背景中，Cosmos DB 會以透明方式將資料複製到每個已設定的區域。

Cosmos DB 支援全域層級的[主動/主動](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/)叢集，可讓您設定任何資料庫區域以*同時支援寫入和讀取*。

[多重主機](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits)通訊協定是 Cosmos DB 中的一項重要功能，可啟用下列功能：

- 無限制的彈性寫入和讀取擴充性。

- 99.999% 全球各地的讀取和寫入可用性。

- 保證在第99個百分位數小於10毫秒提供服務的讀取和寫入。

透過 Cosmos DB[多路連接 api](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)，您的微服務會自動知道最接近的 Azure 區域，並將要求傳送給它。 最接近的區域是由 Cosmos DB 來識別，而不會有任何設定變更。 如果區域變成無法使用，多路連接功能會自動將要求路由傳送至下一個最接近的可用區域。

### <a name="multi-model-support"></a>多模型支援

將整合型應用程式遷移至雲端原生架構時，開發小組有時必須遷移開放原始碼的 NoSQL 資料存放區。 Cosmos DB 可以協助您使用其*多模型*資料平臺，在這些 NoSQL 資料存放區中保留您的投資。 圖5-13 顯示支援的 NoSQL[相容性 api](https://www.wikiwand.com/en/Cosmos_DB)。

![Cosmos DB 提供者](./media/cosmos-db-providers.png)

**圖 5-13**： Cosmos DB 提供者

開發小組可以將現有的 Mongo、Gremlin 或 Cassandra 資料庫移轉到 Cosmos DB，但對資料或程式碼的變更最少。 針對新的應用程式，開發小組可以選擇開放原始碼選項或內建的 SQL API 模型。

> 就內部而言，Cosmos 會以基本資料類型組成的簡單結構格式來儲存資料。 資料庫引擎會針對每個要求，將基本資料轉譯成您所選取的模型標記法。

在上圖5-13 中，請記下 [[資料表 API](https://docs.microsoft.com/azure/cosmos-db/table-introduction) ] 選項。 此 API 是 Azure 表格儲存體的演進。 兩者都共用相同的基礎資料表模型，但 Cosmos DB 資料表 API 新增了 Azure 儲存體 API 中未提供的 premium 增強功能。 這些功能的對比圖5-4。

![Azure 資料表 API](media/azure-table-api.png)

**圖 5-14**： Azure 資料表 API 提供者

使用 Azure 資料表儲存體的微服務可以輕鬆地遷移至 Cosmos DB 資料表 API。 不需要變更程式碼。

### <a name="tunable-consistency"></a>可調式一致性

稍早在*關聯式與 NoSQL*一節中，我們討論了*資料一致性*的主旨。 資料一致性指的是資料的*完整性*。 具有分散式資料的雲端原生服務依賴複寫，而且必須在讀取一致性、可用性和延遲之間進行基本取捨。

大部分的分散式資料庫可讓開發人員在兩種一致性模型之間做選擇：強式一致性和最終一致性。 *強式一致性*是資料可程式性的黃金標準。 它保證查詢一律會傳回最新的資料，即使系統必須產生延遲，等待更新在所有資料庫複本之間複寫。 設定為*最終一致性*的資料庫會立即傳回資料，即使該資料不是最新的複本也一樣。 第二個選項可提供更高的可用性、更高的規模，並提升效能。

Azure Cosmos DB 提供五個定義完善的[一致性模型](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)，如圖5-15 所示。

![Cosmos DB 一致性圖表](./media/cosmos-consistency-level-graph.png)

**圖 5-15**： Cosmos DB 一致性層級

 這些選項可讓您針對一致性、可用性和資料的效能，做出精確的選擇和細微的取捨。 圖5-16 說明每個層級。

![Cosmos DB 一致性層級](./media/cosmos-db-consistency-levels.png)

**圖 5-16**： Cosmos DB 一致性層級描述

在[Cosmos DB 一致性層級入門一](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)文中，Microsoft Cloud 開發人員提倡者 Jeremy Likeness 提供五種模型的絕佳說明。

### <a name="partitioning"></a>資料分割

Azure Cosmos DB 會採用自動[分割](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview)來調整資料庫，以符合您的雲端原生服務的效能需求。

您可以藉由建立資料庫、容器和專案來管理 Cosmos DB 資料中的資料。

容器存留在 Cosmos DB 資料庫中，代表不受架構限制的專案群組。 專案是您加入至容器的資料。 它們是以檔、資料列、節點或邊緣表示。 所有新增至容器的專案都會自動編制索引。

若要分割容器，專案會分成不同的子集，稱為「邏輯分割區」。 系統會根據與容器中每個專案相關聯的分割區索引鍵的值來填入邏輯分割區。 圖5-18 顯示兩個容器，其中每一個都具有以資料分割索引鍵值為基礎的邏輯分割區。

![Cosmos DB 資料分割機制](./media/cosmos-db-partitioning.png)

**圖 5-18**： Cosmos DB 資料分割機制

請注意，在上圖中，每個專案都包含「city」或「機場」的分割區索引鍵。 索引鍵會決定專案的邏輯分割區。 具有城市代碼的專案會指派給左邊的容器，以及具有機場代碼的專案到右邊的容器。 將資料分割索引鍵值與識別碼值結合，會建立專案的索引，以唯一識別專案。

就內部而言，Cosmos DB 會自動管理實體分割區上[邏輯](https://docs.microsoft.com/azure/cosmos-db/partition-data)分割區的位置，以滿足容器的擴充性和效能需求。 隨著應用程式輸送量和儲存需求的增加，Azure Cosmos DB 會將邏輯分割區重新分配到更多伺服器。 轉散發作業是由 Cosmos DB 管理，並在不中斷或停機的情況下叫用。

## <a name="newsql-databases"></a>NewSQL 資料庫

*NewSQL* 是一項新興的資料庫技術，結合了 NoSQL 的分散式擴充性與關係資料庫的 ACID 保證。 對於必須跨分散式環境處理大量資料的商務系統而言，NewSQL 資料庫是很重要的，其具有完整的交易式支援和 ACID 合規性。 雖然 NoSQL 資料庫可提供大規模的擴充性，但不保證資料的一致性。 不一致資料的間歇性問題可能會對開發小組造成負擔。 開發人員必須在其微服務程式代碼中建立保護措施，以管理不一致的資料所造成的問題。

雲端原生運算基礎（由 CNCF）具備數個 NewSQL 資料庫專案。

| 專案 | 特性 |
| :-------- | :-------- |
| Cockroach DB |符合 ACID 規範的關係資料庫，可進行全域調整。 將新節點新增至叢集，CockroachDB 會負責平衡實例和地理位置之間的資料。 它會建立、管理和散發複本，以確保可靠性。 它是開放原始碼且可免費使用。  |
| TiDB | 支援混合式交易和分析處理（HTAP）工作負載的開放原始碼資料庫。 它與 MySQL 相容，而且具備水準擴充性、強式一致性和高可用性。  TiDB 的作用就像 MySQL 伺服器。 您可以繼續使用現有的 MySQL 用戶端程式庫，而不需要對應用程式進行大量的程式碼變更。 |
| YugabyteDB | 一種開放原始碼、高效能、分散式 SQL database。 它支援低查詢延遲、對失敗的恢復能力，以及全域資料散發。 YugabyteDB 與 PostgressSQL 相容，並會處理相應放大的 RDBMS 和網際網路級別 OLTP 工作負載。 產品也支援 NoSQL，而且與 Cassandra 相容。 |
|Vitess | Vitess 是一種資料庫解決方案，可用於部署、調整和管理 MySQL 實例的大型叢集。 它可以在公用或私用雲端架構中執行。 它結合並擴充許多重要的 MySQL 功能和功能，包括垂直和水準分區化支援。 Vitess 是由 YouTube 所產生，自2011起就已提供所有 YouTube 資料庫流量。 |

上圖中的開放原始碼專案可從雲端原生計算基礎取得。 其中三個供應專案都是完整的資料庫產品，其中包括 .NET Core 支援。 另一個（Vitess）是一種資料庫叢集系統，它會水準調整大型的 MySQL 實例叢集。 

NewSQL 資料庫的主要設計目標是在 Kubernetes 中以原生方式工作，利用平臺的復原和擴充性。

NewSQL 資料庫的設計，是為了在暫時的雲端環境中，您可以在稍後的通知中重新開機或排程基礎虛擬機器。 這些資料庫的設計是要在沒有資料遺失或停機的情況下，仍可承受節點失敗。 例如，CockroachDB 可以跨叢集中的節點維護三個一致的資料複本，以在電腦遺失的情況下存活。

Kubernetes 會使用*服務結構*，讓用戶端從單一 DNS 專案處理一組完全相同的 NewSQL 資料庫處理常式。 藉由將資料庫實例與相關聯之服務的位址分離，我們可以進行調整，而不會中斷現有的應用程式實例。 在指定的時間將要求傳送至任何服務，一律會產生相同的結果。

在此案例中，所有資料庫實例都是相等的。 沒有主要或次要關聯性。 在 CockroachDB 中找到的技術，像是*共識*複寫，可讓任何資料庫節點處理任何要求。 如果接收負載平衡要求的節點在本機上有其所需的資料，則會立即回應。 如果沒有，節點會變成閘道，並將要求轉送至適當的節點，以取得正確的答案。 從用戶端的觀點來看，每個資料庫節點都是相同的：它們會顯示為單一*邏輯*資料庫，具有單一電腦系統的一致性保證，儘管有數十個或甚至數百個在幕後工作的節點。

若要深入瞭解 NewSQL 資料庫背後的機制，請參閱[虛線： Kubernetes 原生資料庫的四個屬性一](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)文。

## <a name="data-migration-to-the-cloud"></a>將資料移轉至雲端

較費時的工作之一，就是將資料從一個資料平臺遷移到另一個。 [Azure 資料移轉服務](https://azure.microsoft.com/services/database-migration/)有助於加速這類工作。 它可以將數個外部資料庫來源的資料移轉到 Azure 資料平臺，並將停機時間降到最低。 目標平臺包含下列服務：

- Azure SQL Database
- 適用於 MySQL 的 Azure 資料庫
- 適用於 MariaDB 的 Azure 資料庫
- 適用於 PostgreSQL 的 Azure 資料庫
- CosmosDB
  
此服務會提供建議，引導您完成執行小型或大型遷移所需的變更。

>[!div class="step-by-step"]
>[上一頁](Database-per-microservice.md)
>[下一頁](azure-caching.md)
