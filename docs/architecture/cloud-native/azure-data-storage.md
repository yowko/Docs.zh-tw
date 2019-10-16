---
title: Azure 中的資料儲存體
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |Azure 中的資料儲存體
ms.date: 06/30/2019
ms.openlocfilehash: 5e1182af61401990112135c2f7a3dd37508c9e72
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214101"
---
# <a name="data-storage-in-azure"></a>Azure 中的資料儲存體

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

如我們在本書中所見，雲端正在改變應用程式的設計、部署和管理方式。 當您移至雲端時，重要的問題是如何移動資料？ 幸運的是，Azure 雲端提供許多選項。

您可以直接布建 Azure 虛擬機器，並安裝您選擇的資料庫。 這就是所謂的[基礎結構即服務（IaaS）](https://www.techopedia.com/definition/141/infrastructure-as-a-service-iaas)。 這種方法可簡化將內部部署資料庫移至雲端的工作，但會將管理虛擬機器和資料庫的負擔轉移給您。  

取而代之的是，完全受控的[資料庫即服務（DBaaS）](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/)是較好的選擇。 您可以取得許多內建功能，而裝載、維護和授權是由 Microsoft 所管理。 Azure 具備不同種類的完全受控資料儲存選項，每個都有特定的優點。 它們全都支援即時容量和隨用隨付模型。

接下來，我們將探討 Azure 中可用的 DBaaS 選項。 您將瞭解 Microsoft 如何繼續讓 Azure 成為「開放式平臺」，為許多開放原始碼關聯式和 NoSQL 資料庫提供受控支援，並對各種開放原始碼基礎做為使用中成員的重要貢獻。

## <a name="azure-sql-database"></a>Azure SQL Database

[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/)是以 Microsoft SQL Server 資料庫引擎為基礎的功能豐富、一般用途的關係資料庫即服務（DBaaS）。 它完全由 Microsoft 管理，而且是高效能、可靠且安全的雲端資料庫。 服務會共用在內部部署版本的 SQL Server 中找到的許多功能。 

您可以在幾分鐘內布建 SQL Database 伺服器和資料庫。 當您的應用程式需求從幾個客戶成長到百萬個時，Azure SQL Database 在最短的停機時間內即時調整規模。 您可以動態新增或移除資源，包括 CPU 電源、記憶體、IO 輸送量和配置給資料庫的儲存體。

圖5-12 顯示 Azure SQL Database 的部署選項。

![Azure SQL 部署選項](./media/azure-sql-database-deployment-options.png)

**圖 5-12**。 Azure SQL 部署選項

部署 SQL Database 時，請注意上圖中的替代方案：

- 具有一組由[SQL Database 伺服器](https://docs.microsoft.com/azure/sql-database/sql-database-servers)管理之自有資源的[單一資料庫](https://docs.microsoft.com/azure/sql-database/sql-database-single-database) 。 單一資料庫類似于內部部署 SQL Server 部署中的自主 [資料庫](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) 。

- 一種[彈性](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-pool)集區，其中 SQL 資料庫的集合會以設定的價格共用單一 SQL Database 伺服器。 您可以視需要在彈性集區中移動或移出單一資料庫，以優化一組資料庫的價格效能。

- [受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)，其中是系統和使用者資料庫的集合，可提供與內部部署 SQL Server 近乎 100% 的相容性。 此選項支援較大的資料庫，最高可達 35 TB，並放在[Azure 虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)中，以獲得更好的隔離。

Azure SQL Database 是完全受控的[平臺即服務（PaaS）資料庫引擎](https://docs.microsoft.com/azure/sql-database/sql-database-paas)，可在不需要使用者介入的情況下，處理升級、修補、備份和監視。 它一律會執行最新穩定版本的 SQL Server 資料庫引擎和修補的作業系統，並保證 99.99% 的可用性。 其中一項功能是[主動式異地](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)複寫，可讓您在相同或不同的 Azure 資料中心內建立可讀取的次要資料庫。 失敗時，可以起始容錯移轉至次要資料庫。 此時，其他次要複本會自動連結到新的主要複本。 在相同或不同的區域中，最多可支援四個次要複本，而且這些次要資料庫也可以用於唯讀存取查詢。

Azure SQL Database 包含[內建的監視和智慧型調整](https://docs.microsoft.com/azure/sql-database/sql-database-monitoring-tuning-index)功能，可協助您將效能最大化並降低營運成本。 例如，[自動調整](https://docs.microsoft.com/azure/sql-database/sql-database-automatic-tuning)功能可根據 AI 和機器學習提供持續的效能微調。 服務會從您執行中的工作負載學習，並且可以套用微調建議。 Azure SQL Database 在啟用自動調整的情況下執行的時間越長，效能就愈好。

[Azure SQL Database 無伺服器](https://docs.microsoft.com/azure/sql-database/sql-database-serverless)（在本書撰寫時提供預覽）是單一資料庫的計算層，可根據工作負載需求自動調整，並以每秒所使用的計算量來計費。 無伺服器計算層也會在非使用中期間自動暫停資料庫，因此只會收取儲存體費用。 當活動傳回時，它會自動繼續。

最後，有新的[Azure SQL Database 超大規模資料庫](https://azure.microsoft.com/services/sql-database/)定價層。 它是由可高度擴充的儲存體架構所提供，可讓您的資料庫視需要成長，而不必預先布建儲存體資源。 您可以獨立調整計算和儲存體資源，為每個工作負載提供優化效能的彈性。 Azure SQL Database 超大規模資料庫已針對[OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing)處理和高輸送量分析工作負載進行優化，儲存體最多可達 100 TB。  透過大量讀取的工作負載，超大規模資料庫會視需要布建額外的讀取複本來提供快速相應放大，以卸載讀取工作負載。 

除了傳統的 Microsoft SQL Server 堆疊之外，Azure 也提供數個熱門開放原始碼資料庫的受控版本。

## <a name="azure-database-for-mysql"></a>適用於 MySQL 的 Azure 資料庫

[MySQL](https://en.wikipedia.org/wiki/MySQL)  是一個 [開放原始](https://en.wikipedia.org/wiki/Open-source_software)碼 [關係資料庫](https://en.wikipedia.org/wiki/Relational_database_management_system)。 它是[燈泡軟體堆疊](https://en.wikipedia.org/wiki/LAMP_(software_bundle))中的元件，可供許多大型組織使用，包括 Facebook、Twitter 和 YouTube。 此社區版本免費提供，而 enterprise edition 則需要購買授權。 此產品原本是在1995中建立的，由 Sun Microsystems 在2008（由 Oracle 在2010中取得）所購買。

[適用於 MySQL 的 Azure 資料庫](https://azure.microsoft.com/services/mysql/)是完全受控、符合企業需求的關係資料庫服務，以開放原始碼 MySQL 伺服器引擎為基礎。 執行 MySQL 社區版，其中包含下列 PaaS 功能，不需額外費用：

- 內建[高可用性](https://docs.microsoft.com/azure/mysql/concepts-high-availability)。

- 可預測的效能，使用內含的[隨用隨付定價](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers)。 

- 在幾秒內視需要進行[調整](https://docs.microsoft.com/azure/mysql/concepts-high-availability)。

- 安全地保護待用和移動中的敏感性資料。

- 最多35天的[自動備份](https://docs.microsoft.com/azure/mysql/concepts-backup)和[時間點還原](https://docs.microsoft.com/azure/mysql/concepts-backup)。

- 企業級安全性與合規性。

這些內建 PaaS 功能對於在其資料中心具有數百個「策略性」（非策略性）資料庫，但沒有執行修補、備份、安全性和效能監視的資源的組織而言非常重要。 

此外， [Azure 資料移轉服務](https://azure.microsoft.com/services/database-migration/)可以將多個資料庫來源的資料移轉至 Azure 資料平臺，並將停機時間降到最低。 服務會產生評量報告，並提供建議以引導您完成執行遷移所需的變更，也就是小型或大型。

受管理的[Azure MySQL 伺服器](https://docs.microsoft.com/azure/mysql/concepts-servers)是服務的中央管理點。 它與用於內部部署的 MySQL 伺服器引擎相同。 有了它，您可以為每部伺服器建立單一資料庫，以取用所有資源，或為每部伺服器建立多個資料庫來共用資源。 您的小組可以繼續使用您選擇的開放原始碼工具和平臺來開發應用程式，而不需要學習新技能或管理虛擬機器和基礎結構。

## <a name="azure-database-for-mariadb"></a>適用於 MariaDB 的 Azure 資料庫

[適用于 mariadb](https://mariadb.com/)伺服器是另一個熱門的開放原始碼資料庫伺服器。 在 Oracle 購買 Sun Microsystems （擁有 MySQL）時，MySQL 的原始開發人員會將它建立為 MySQL 的分叉。 其目的是要確保適用于 mariadb 保持開放原始碼。

由於適用于 mariadb 是[MySQL 的分叉](https://blog.panoply.io/a-comparative-vmariadb-vs-mysql)，因此資料和資料表定義相容，而用戶端通訊協定、結構和 api 則是 knit。 MySQL 資料連線器會在不修改的情況下適用于 mariadb 工作。

適用于 mariadb 具有強大的功能，且由許多大型企業使用。 雖然 Oracle 持續維護、增強和支援 MySQL，但適用于 mariadb 是由適用于 mariadb Foundation 管理，允許對產品和檔進行公開貢獻。

[適用於 MariaDB 的 Azure 資料庫](https://azure.microsoft.com/services/mariadb/)是 Azure 雲端中完全受控的資料庫即服務。 它是以適用于 mariadb 的「 [社區版本](https://mariadb.org/download/)伺服器引擎」為基礎。 它可以處理任務關鍵性工作負載，並提供可預測的效能和動態擴充性。 與其他 Azure 資料庫平臺類似，它包含許多平臺即服務功能，不需額外費用：

- 內建[高可用性](https://docs.microsoft.com/azure/mariadb/concepts-high-availability)。

- 可預測的效能，使用內含的[隨用隨付定價](https://docs.microsoft.com/azure/mariadb/concepts-pricing-tiers)。 
 
- 在幾秒內視需要進行[調整](https://docs.microsoft.com/azure/mariadb/concepts-high-availability)。

- 保護待用和移動中敏感性資料的安全。

- 最多35天的[自動備份](https://docs.microsoft.com/azure/mariadb/concepts-backup)和[時間點還原](https://docs.microsoft.com/azure/mariadb/concepts-backup)。

- 企業級安全性與合規性。

## <a name="azure-database-for-postgresql"></a>適用於 PostgreSQL 的 Azure 資料庫 

[于 postgresql](https://www.postgresql.org/)是另一個受歡迎的開放原始碼關係資料庫，有超過30年的作用中開發。 這是一般用途和物件關係資料庫管理系統。 其授權被視為「自由」，而產品可免費使用、修改及散佈任何形式。 許多大型企業（包括 Apple、Red Hat 和 Fujitsu）都有使用於 postgresql 的建立產品。

[適用於 PostgreSQL 的 Azure 資料庫](https://azure.microsoft.com/services/postgresql/)是完全受控的關係資料庫服務，以開放原始碼 Postgres 資料庫引擎為基礎。 它可以使用可預測的效能、安全性、高可用性和動態擴充性來處理任務關鍵性工作負載。 它支援數個開放原始碼架構和語言， C++包括、JAVA、Python、Node、\#C 和 PHP。 它可讓您透過命令列介面或[Azure 資料移轉服務](https://azure.microsoft.com/services/database-migration/)來[遷移](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1)于 postgresql 資料庫。

本服務包含[內建的智慧功能](https://docs.microsoft.com/azure/postgresql/concepts-monitoring)，可研究您獨特的資料庫模式，並提供自訂的建議和見解，協助您將于 postgresql 資料庫的效能最大化。 [先進的威脅防護](https://docs.microsoft.com/azure/postgresql/concepts-data-access-and-security-threat-protection)會以時鐘來監視您的資料庫，並偵測潛在的惡意活動、在偵測到時發出警示，讓您可以立即介入。

適用於 PostgreSQL 的 Azure 資料庫提供兩種部署選項：單一伺服器與超大規模資料庫（Citus），可在本書撰寫時預覽

- [單一伺服器](https://docs.microsoft.com/azure/postgresql/concepts-servers)部署選項是多個資料庫的中央管理點。 這是相同的于 postgresql 伺服器引擎，適用于內部部署。 有了它，您可以為每部伺服器建立單一資料庫，以取用所有資源，或建立多個資料庫來共用資源。 定價是以核心和儲存體為基礎，依伺服器進行結構化。

- [超大規模資料庫（Citus）選項](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/)是由 [Citus 資料](https://www.citusdata.com/) 技術提供技術支援。 它可透過在數百個節點間水準調整單一資料庫，以提供神速的快速效能和規模，藉此進行高效能調整。 此選項可讓引擎在記憶體中容納更多資料、跨數百個節點平行處理查詢，以及更快編制資料索引。 超大規模資料庫功能與于 postgresql 的最新創新、版本和工具相容，因此您可以利用現有的于 postgresql 專長。

## <a name="cosmos-db"></a>Cosmos DB

Azure Cosmos DB 是完全受控的全域分散式 NoSQL 資料庫服務，其設計目的是要提供低延遲、彈性的擴充性、受控資料一致性和高可用性。 簡單地說，如果您的應用程式需要在世界各地保證快速回應時間，而且必須隨時上線，而且輸送量和儲存空間需要無限制且彈性的擴充性，Cosmos DB 是絕佳的選擇。 圖5-13 顯示 Cosmos DB 的高階總覽。

![Cosmos DB 總覽](./media/cosmos-db-overview.png)

**圖 5-13**：Cosmos DB 總覽

請注意，在圖5-13 中，Cosmos DB 是一項功能強大且非常多功能的資料庫服務，其中包含許多內建的雲端原生功能。 在本節中，我們將進一步探討它們。

### <a name="global-support"></a>全球支援

您可以在全球所有 Azure 區域中全域散發 Cosmos 資料庫、將資料放在使用者附近、改善回應時間，以及減少延遲。 您可以從區域新增或移除資料庫，而不需要暫停或重新部署您的應用程式。 在背景中，Cosmos DB 會以透明方式將資料複寫到所有已設定的區域。

Cosmos DB 支援全域層級的[主動/主動](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/)叢集，可讓您設定任何或所有資料庫區域，以同時支援寫入和讀取。

Cosmos DB 中的[多](https://docs.microsoft.com/azure/cosmos-db/how-to-multi-master)宿主通訊協定功能可啟用下列功能：

- 無限制的彈性寫入和讀取擴充性。

- 99.999% 全球各地的讀取和寫入可用性。

- 保證在第99個百分位數小於10毫秒提供服務的讀取和寫入。

就內部而言，Cosmos DB 會處理具有一致性層級保證之區域之間的資料複寫，以及財務支援的服務等級協定。

透過 Cosmos DB[多路連接 api](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)，您的應用程式可以自動留意到最接近的 Azure 區域，並將要求傳送給它。 最接近的區域是由 Cosmos DB 來識別，而不會有任何設定變更。 如果區域變得無法使用，Cosmos DB 支援自動容錯移轉，且多路連接功能會自動將您的要求路由至下一個最接近的可用區域。

### <a name="multi-model-support"></a>多模型支援

Cosmos DB 是*多模型資料平臺*，可讓您使用數個支援的 NoSQL 模型與資料互動，包括檔、索引鍵/值組、寬資料行和圖形標記法。 就內部而言，資料是以基本資料類型組成的簡單[結構](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/using-structs)格式儲存，包括字串、布林和數位。 資料庫引擎會針對每個要求，將資料轉譯成您所選取的模型標記法。 您可以從專屬 Cosmos DB 以 SQL 為基礎的 API 或任何如圖5-14 所示的[相容性 api](https://www.wikiwand.com/en/Cosmos_DB)中選擇。

![Cosmos DB 提供者](./media/cosmos-db-providers.png)

**圖 5-14**：Cosmos DB 提供者

請注意，在圖5-14 中，Cosmos DB 如何支援[表格儲存體](https://azure.microsoft.com/services/storage/tables/)。 Cosmos DB 和[Azure 表格儲存體](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)會共用相同的基礎資料表模型，並公開許多相同的資料表作業。 不過， [Cosmos DB 資料表 API](https://docs.microsoft.com/azure/cosmos-db/table-introduction)提供 Azure 儲存體 API 中未提供的許多 premium 增強功能。 這些功能的對比圖5-15。

![Azure 資料表 API](./media/azure-table-api.png)

**圖 5-15**：Azure 資料表 API

針對 Azure 資料表儲存體所撰寫的應用程式可以使用資料表 API 而不需要變更程式碼，來遷移至 Azure Cosmos DB。

在 [Brownfield] （ https://en.wikipedia.org/wiki/Brownfield_(software_development) 應用程式案例中，開發小組可以將現有的 Mongo、Gremlin 或 Cassandra 資料庫移轉到 Cosmos DB，並對現有的資料或應用程式代碼進行最少的變更。 在[Greenfield](https://en.wikipedia.org/wiki/Greenfield_project)案例中，開發小組可以選擇最符合其需求和喜好設定的資料模型，包括 MongoDB、Cassandra 和 Gremlin 平臺的完全支援開放原始碼選項。

### <a name="consistency-models"></a>一致性模型

稍早在*關聯式與 NoSQL*一節中，我們討論了*資料一致性*的主旨，這是指資料完整性的詞彙。 依賴複寫以獲得高可用性、低延遲或兩者的分散式資料庫，必須在讀取一致性、可用性和延遲之間做出基本取捨。

大部分的分散式資料庫可讓開發人員在兩種一致性模型之間做選擇： [強式一致性](https://en.wikipedia.org/wiki/Strong_consistency)和 [最終一致性](https://en.wikipedia.org/wiki/Eventual_consistency)。 *強式一致性*是資料可程式性的黃金標準。 它保證查詢結果一律會傳回最新的資料，即使系統必須產生延遲，等待更新在所有資料庫複本之間複寫。 另一方面，設定為*最終一致性*的系統會立即傳回資料，即使該資料不是最新的複本也一樣。 此選項可提供更高的可用性、更高的規模，並提升效能。

Azure Cosmos DB 提供一系列[五個定義完善的一致性模型](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)，如圖5-16 所示。 這些選項可讓您根據應用程式的需求，針對可用性和效能做出精確的選擇和細微的取捨。 這些模型已妥善定義、直覺化，並受到服務等級協定（Sla）的支援。 

![Cosmos DB 一致性層級](./media/cosmos-db-consistency-levels.png)

**圖 5-16**：Cosmos DB 一致性層級

### <a name="partitioning"></a>資料分割

Azure Cosmos DB 會使用自動[分割](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview)來調整資料庫，以符合您應用程式的效能需求。 

您可以藉由建立[資料庫、容器和專案](https://docs.microsoft.com/azure/cosmos-db/databases-containers-items)來管理 Cosmos DB 資料中的資料，如圖5-17 所示。

![Cosmos DB 實體](./media/cosmos-db-entities.png)

**圖 5-17**：Cosmos DB 實體的階層

請注意圖5-17 如何從在 Azure 帳戶內建立 Cosmos DB 資料庫開始。 該資料庫會成為一組容器的管理單位。 容器是一種不限架構的專案群組，可以根據您選取的 API 提供者（在先前的章節中討論），以集合、資料表或圖形表示。 專案是您加入至容器並以檔、資料列、節點或邊緣表示的資料。 根據預設，系統會自動為您新增至容器的所有項目編製索引，您不需要進行任何明確的索引或結構描述管理。

若要分割容器，專案會分成不同的子集，稱為「 [邏輯](https://docs.microsoft.com/azure/cosmos-db/partition-data)分割區」。 邏輯分割區是根據與容器中每個專案相關聯的資料分割索引鍵的值來建立。 圖5-18 顯示邏輯分割區中的所有專案如何具有相同的資料分割索引鍵值。

![Cosmos DB 資料分割機制](./media/cosmos-db-partitioning.png)

**圖 5-18**：Cosmos DB 資料分割機制

請注意，在圖5-18 中，每個專案都包含「city」或「機場」的分割區索引鍵。 此分割區索引鍵會決定專案的邏輯分割區。 每個城市代碼都會指派給左邊容器中的邏輯分割區，並將其機場代碼提供給右邊的容器。 將資料分割索引鍵值與專案的識別碼值結合，會建立專案的索引，以唯一識別該專案。

就內部而言，Cosmos DB 會自動管理[實體](https://docs.microsoft.com/azure/cosmos-db/partition-data)分割區上[邏輯](https://docs.microsoft.com/azure/cosmos-db/partition-data)分割區的位置，以有效率地滿足容器的擴充性和效能需求。 隨著應用程式的輸送量和儲存體需求增加，Azure Cosmos DB 會移動邏輯分割區，以將負載分散到更多的伺服器上。 這些轉散發作業是由 Cosmos DB 管理，而且會在沒有任何中斷或停機的情況下執行。

## <a name="azure-redis-cache"></a>Azure Redis 快取

瞭解快取以改善效能和擴充性的優點很容易理解。 

針對雲端原生應用程式，新增快取的常見位置是在 API 閘道上。 閘道可做為所有傳入要求的前端。 藉由新增快取，您可以藉由傳回快取的資料，並避免往返本機資料庫或下游服務，來提升效能和回應性。 圖5-19 顯示雲端原生應用程式的快取架構。

![在雲端原生應用程式中快取](./media/caching-in-a-cloud-native-app.png)

**圖 5-19**：在雲端原生應用程式中快取

常見的快取模式是另行快取[模式](https://docs.microsoft.com/azure/architecture/patterns/cache-aside)。 針對連入要求，您必須先查詢回應的快取，如圖5-19 中的步驟 #1 所示。 如果找到，則會立即傳回資料。 如果資料不存在於快取中（稱為快取[遺漏](https://www.techopedia.com/definition/6308/cache-miss)），則會從本機資料庫或下游服務（步驟 #2）取出，並將其寫入快取以供未來的要求（步驟 #3），並傳回給呼叫者。 請小心，定期收回快取的資料，讓系統維持一致且正確的狀態。

此外，請注意圖5-19 中的快取不會在服務界限內實作為本機，而是當做雲端型的支援服務使用，如第1章所述。

[Azure Redis](https://azure.microsoft.com/services/cache/)快取是一種資料快取和訊息代理程式服務。 它可為應用程式提供高輸送量和低延遲的資料存取。 它完全由 Microsoft 管理，裝載于 Azure 內，而且可供 Azure 內部或外部的任何應用程式存取。

就內部而言，Azure Cache for Redis 是由開放原始碼[Redis 伺服器](https://redis.io/)支援，而且原生支援[字串](https://redis.io/topics/data-types#strings)、[雜湊](https://redis.io/topics/data-types#hashes)、[清單](https://redis.io/topics/data-types#sets)、[集合](https://redis.io/topics/data-types#sets)和[排序的集合](https://redis.io/topics/data-types#sorted-sets)等資料結構。 如果您的應用程式使用 Redis，它會與 Azure Cache for Redis 搭配使用。

Azure Cache for Redis 也可用來作為記憶體中的資料快取、分散式非關係資料庫和訊息代理程式。 有三個不同的定價層可供使用。 高階層提供許多企業層級的功能，例如叢集、資料持續性、異地複寫，以及虛擬網路安全性和隔離。

>[!div class="step-by-step"]
>[上一頁](data-patterns.md)
>[下一頁](resiliency.md)
