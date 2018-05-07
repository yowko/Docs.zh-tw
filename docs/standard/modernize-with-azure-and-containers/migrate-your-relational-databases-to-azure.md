---
title: 將關聯式資料庫移轉至 azure
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows Containers |將關聯式資料庫移轉至 azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: efc558115d184ed53a963eab2acdd847a12dbb3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="migrate-your-relational-databases-to-azure"></a>將關聯式資料庫移轉至 azure

願景： Azure 提供最完整的資料庫移轉。

在 Azure 中，您可以移轉您的資料庫伺服器直接到 IaaS Vm （純增益和 shift），或您可以移轉到 Azure SQL Database，額外的好處。 Azure SQL Database 提供受管理的執行個體與完整資料庫做為服務 (DBaaS) 選項。 圖 3-1 顯示在 Azure 中可用的移轉路徑的多個關聯式資料庫。

![在 Azure 中資料庫的移轉路徑](./media/image3-1.png)

> **圖 3-1** 在 Azure 中資料庫的移轉路徑

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>當移轉到 Azure SQL Database 管理執行個體

在大部分情況下，Azure SQL Database 管理執行個體將會是您最佳的選項，您將資料移轉至 Azure 時，請考慮。 如果您要移轉 SQL Server 資料庫，而且需要將近 100%的保證，讓您不需要重新設計應用程式架構，或變更您的資料或資料存取程式碼，請選擇 Azure SQL Database 的 Managed 執行個體功能。

如果您有其他需求，如需 SQL Server 執行個體層級功能或隔離需求，提供標準的 Azure SQL Database （單一資料庫模型） 中的功能之外，azure SQL Database 管理執行個體是最佳選擇。 這個最後一個最以 PaaS 為導向的選擇，但它不提供與傳統的 SQL server 的相同的功能。 移轉可能會出現 frictions。

例如，組織中 SQL Server 執行個體層級的功能已深層投資獲益移轉至 SQL 受管理的執行個體。 SQL Server 的執行個體層級功能的範例包括 SQL common language runtime (CLR) 整合，SQL Server 代理程式，以及跨資料庫查詢。 無法使用標準的 Azure SQL Database （單一資料庫模型） 中的這些功能支援。

組織的高管制的業界的操作，並基於安全性考量，隔離資料時需也可能會受益於選擇 SQL 受管理的執行個體模型。

Azure SQL Database 中的 managed 執行個體具有下列特性：

- 透過 Azure 虛擬網路的安全性隔離

- 應用程式介面與相容性，這些功能：

  - SQL Server Agent 和 SQL Server Profiler

  - 跨資料庫參考和查詢，SQL CLR 複寫、 異動資料擷取 (CDC) 和 Service Broker

- 資料庫大小最多 35 TB

- 最少停機時間移轉，與這些功能：

  - Azure 資料庫移轉的服務

  - 原生備份及還原，記錄傳送

使用這些功能，當您將現有的應用程式資料庫移轉至 Azure SQL Database 中，Managed 執行個體模型提供近 100%的 Paas 優點適用於 SQL Server。 受管理的執行個體是 SQL Server 環境，讓您繼續使用執行個體層級功能，而不需要變更應用程式的設計。

受管理的執行個體可能是最適合用於企業目前使用的 SQL Server，而且需要它們在雲端中的網路安全性的彈性。 它可用的 SQL 資料庫的私人虛擬網路。

## <a name="when-to-migrate-to-azure-sql-database"></a>當移轉到 Azure SQL Database

如前所述，標準的 Azure SQL Database 是完全受管理、 關聯式 DBaaS。 SQL Database 目前管理包含數百萬個生產資料庫，在世界各地的 38 資料中心。 它支援廣泛的應用程式和工作負載，而不需要管理要開車最需要大量資料的關鍵任務應用程式，需要全域的縮放比例的進階的資料處理簡單的交易式資料。

由於其完整的 PaaS 功能，因此更好的定價層和降低成本-要改用標準的 Azure SQL Database 為 」 的預設選擇 「 如果您的應用程式，使用基本、 標準 SQL 資料庫以及任何額外的執行個體功能。 在標準的 Azure SQL Database 不支援 SQL Server 功能，例如 SQL CLR 整合、 SQL Server 代理程式，以及跨資料庫查詢。 只能在 Azure SQL Database 管理執行個體模型中使用這些功能。

Azure SQL Database 是建置應用程式開發人員只智慧型雲端資料庫服務。 它也是縮放上作業，而不需要停機，可協助您有效率地將多租用戶應用程式提供的唯一雲端資料庫服務。 最後，Azure SQL Database 會讓您更多時間來創新，而且它市場加速您的時間。 您可以建置安全的應用程式，並連接到 SQL database 所使用的語言和您偏好的平台。

Azure SQL Database 提供下列優點：

- 內建智慧 （機器學習），會學習，而您的應用程式適應

- 視資料庫的佈建

- 某個範圍的所有工作負載的方案，

- 99.99%可用性 SLA、 零維護

- 地理複寫和還原的資料保護服務

- Azure SQL Database 點還原時間的功能

- 與 SQL Server 2016，包括混合式和移轉的相容性

標準的 Azure SQL Database 是 PaaS 接近於 Azure SQL Database 管理執行個體。 您應該嘗試使用它，可能的話，請從受管理的雲端，將會有更多的優點。 不過，Azure SQL Database 已從規則的一些主要差異而且在內部部署 SQL Server 執行個體。 根據您現有的應用程式的資料庫需求，和企業需求和原則，它可能無法最佳的選擇時您計劃移轉至雲端。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>何時將您的原始 RDBMS 移至 VM (IaaS)

移轉選項的其中一個是移動您原始關聯式資料庫管理系統 (RDBMS)，包括 Oracle、 IBM DB2、 MySQL、 PostgreSQL 或 SQL Server 到類似的伺服器在 Azure VM 上執行。 如果您有現有的應用程式需要最少的變更或沒有變更雲端最快速移轉，直接移轉至雲端中的 IaaS 可能公平的選項。 您可能無法充分利用的所有雲端優點的最佳方式，但它可能是最快的初始路徑。

Microsoft Azure 目前最多支援[331 不同資料庫伺服器](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all)部署為 IaaS Vm。 其中包括熱門 RDBMSes 像 SQL Server、 Oracle、 MySQL、 PostgreSQL 和 IBM DB2 和類似 MongoDB、 Cassandra、 DataStax、 MariaDB 和 Cloudera 的許多其他 NoSQL 資料庫。

> [!NOTE]
> 雖然移動您到 Azure VM 的 RDBMS 可能 （因為它是 IaaS），將資料移轉至雲端最快速的方式，這個方法會要求您的 IT 團隊 （資料庫管理員和 IT 專業人員） 方面的大量投資。 企業團隊必須能夠設定和管理高可用性、 災害復原和修補 SQL Server。 此內容也需要自訂的環境中，以完整系統管理權限。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>當移轉到 SQL Server VM (IaaS)

可能會有少數情況下，您仍然需要移轉到 SQL Server 作為規則的 VM。 如果您需要使用 SQL Server Reporting Services 即為一例。 在大部分情況下，不過，Azure SQL Database 管理執行個體可以提供您需要讓移轉至 SQL Server VM 應該是您最後的手段，嘗試從內部部署 SQL server，移轉的所有項目。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>使用 Azure 資料庫移轉服務來將關聯式資料庫移轉至 Azure 

目標資料庫是 Azure SQL Database、 Azure SQL Database 管理執行個體或在 Azure VM 上的 SQL Server，您可以使用關聯式資料庫，例如 SQL Server、 Oracle 和 MySQL 移轉至 Azure，Azure 資料庫移轉的服務。

自動化的工作流程中，使用評估報告時，會引導您完成變更，您必須先將資料庫移轉完成。 當您準備好時，服務會將來源資料庫移轉至 Azure。

每當您變更原始的 RDBMS 時，您可能需要重新測試。 您也可能需要變更 SQL 句子或您的應用程式，根據測試結果中的物件關聯式對應 (ORM) 程式碼。

如果您有其他任何資料庫 (例如，IBM DB2)，而且您選擇增益和 shift 方法，您可能想要繼續使用這些資料庫做為 IaaS Vm 在 Azure 中，除非您願意執行更複雜的資料移轉。 更複雜的資料移轉將會需要額外的工作，因為您會將移轉至新的結構描述和不同的程式設計程式庫不同的資料庫類型。

若要了解如何使用 Azure 資料庫移轉服務，移轉資料庫，請參閱[至雲端的 Azure SQL Database 管理執行個體與 Azure 資料庫移轉服務更快取得](https://channel9.msdn.com/Events/Build/2017/P4008)。

## <a name="additional-resources"></a>其他資源

- **選擇雲端 SQL Server 選項： Azure SQL Database (PaaS) 或 Azure VM (IaaS) 上的 SQL Server**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **取得 Azure SQL DB Managed 執行個體和資料庫移轉服務更快的雲端**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **SQL Server 資料庫移轉至雲端中的 SQL Database**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Azure SQL Database**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **在虛擬機器上的 SQL Server**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
[上一頁](lift-and-shift-existing-apps-azure-iaas.md)
[下一頁](lift-and-shift-existing-apps-devops/index.md)