---
title: 將關聯式資料庫移轉至 azure
description: 將現有.NET 應用程式與 Azure 雲端和 Windows 容器現代化 |將關聯式資料庫移轉至 azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a2aedc9729c674a7b4958506b90c285e54d8d724
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153757"
---
# <a name="migrate-your-relational-databases-to-azure"></a>將關聯式資料庫移轉至 azure

願景：Azure 提供最完整的資料庫移轉。

在 Azure 中，您可以直接到 IaaS Vm （純提升與轉變），移轉您的資料庫伺服器，或您可以移轉至 Azure SQL Database，額外的好處。 Azure SQL Database 提供受控執行個體和完整資料庫做為-即服務 (DBaaS) 選項。 圖 3-1 顯示多個關聯式資料庫在 Azure 中可用的移轉路徑。

![在 Azure 中的資料庫移轉路徑](./media/image3-1.png)

> **圖 3-1** 在 Azure 中的資料庫移轉路徑

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>移轉至 Azure SQL Database 受控執行個體

在大部分情況下，Azure SQL Database 受控執行個體將會是您最佳的選項，您將資料移轉至 Azure 時，請考慮。 如果您要移轉 SQL Server 資料庫，並需要近 100%保證，證明您不需要重新架構您的應用程式，或變更您的資料或資料存取程式碼，請選擇 Azure SQL Database 受控執行個體功能。

如果您有其他需求，如需 SQL Server 執行個體層級功能或隔離需求，提供標準的 Azure SQL Database （單一資料庫模型） 中的功能之外，azure SQL Database 受控執行個體是最佳選項。 最後一項最以 PaaS 為導向的選擇，但它不會提供與傳統的 SQL server 的相同功能。 移轉可能會出現的摩擦。

例如，組織方面所做深入的投資執行個體層級 SQL Server 功能受益於移轉至 SQL 受控執行個體。 執行個體層級 SQL Server 功能的範例包括 SQL common language runtime (CLR) 整合，SQL Server Agent，以及跨資料庫查詢。 無法使用標準的 Azure SQL Database （單一資料庫模型） 中支援這些功能。

組織，在高管制的產業中運作，並需要維護隔離，基於安全考量，也可能會受益於選擇 SQL 受控執行個體模型。

在 Azure SQL Database 受控執行個體具有下列特性：

- 透過 Azure 虛擬網路的安全性隔離

- 應用程式介面相容，這些功能：

  - SQL Server Agent 和 SQL Server Profiler

  - 跨資料庫參考和查詢，SQL CLR、 複寫、 異動資料擷取 (CDC) 和 Service Broker

- 資料庫大小上限為 35 TB

- 最少停機時間移轉，這些功能：

  - Azure 資料庫移轉服務

  - 原生備份及還原，記錄傳送

使用這些功能，當您將現有的應用程式資料庫移轉至 Azure SQL Database 受控執行個體模型提供幾乎 100%的 Paas 優點適用於 SQL Server。 受控執行個體是 SQL Server 環境，您可以繼續使用執行個體層級功能，而不需要變更您的應用程式設計。

受控執行個體可能是最好的選擇，適用於企業目前使用之 SQL Server，而且必須在其雲端中的網路安全性的彈性。 就像您的 SQL database 的私人虛擬網路。

## <a name="when-to-migrate-to-azure-sql-database"></a>移轉至 Azure SQL Database

如前所述，標準的 Azure SQL Database 是完全受控的關聯式 DBaaS。 目前，SQL Database 會管理數以百萬計的生產資料庫，在世界各地的 38 資料中心。 它支援廣泛的應用程式和工作負載，從管理簡單的交易資料，以推動需要全球規模的進階的資料處理的資料密集、 任務關鍵性應用程式。

因為其完整的 PaaS 功能，更好的定價層和最終降低成本-您應該移至標準的 Azure SQL Database 為您的 「 預設為選擇 「 如果您的應用程式，會使用基本、 標準 SQL database 和任何額外的執行個體功能。 標準的 Azure SQL Database 中不支援 SQL Server 功能，像是 SQL CLR 整合、 SQL Server Agent，以及跨資料庫查詢。 這些功能是僅適用於 Azure SQL Database 受控執行個體模型。

Azure SQL Database 是建置應用程式開發人員只智慧型雲端資料庫服務。 它也是唯一的雲端資料庫服務，可擴展上作業，而不需要停機，可協助您有效率地提供多租用戶的應用程式。 最後，Azure SQL Database 會讓您更多時間發揮創意，，而且它加速上市的時間。 您可以建置安全應用程式，並使用您偏好的平台與語言連線到您的 SQL database。

Azure SQL Database 提供下列優點：

- 可學習並適應您的應用程式的內建智慧 （機器學習服務）

- 視資料庫佈建

- 範圍的所有工作負載的供應項目

- 99.99%可用性 SLA，不需要維護

- 資料保護的異地複寫和還原服務

- 在 還原時間功能的 azure SQL Database 點

- 使用 SQL Server 2016，包括混合式和移轉的相容性

標準的 Azure SQL Database 是較接近 PaaS 比 Azure SQL Database 受控執行個體。 偏好使用標準的 Azure SQL Database，因為您會從受管理的雲端中享有更多好處。 不過，Azure SQL Database 已從一般的一些主要差異和內部部署 SQL Server 執行個體。 根據現有的應用程式的資料庫需求，以及您企業需求和原則，它可能不是最佳選擇在規劃移轉至雲端時。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>將原始的 RDBMS 移到 VM (IaaS) 的時機

移轉選項的其中一個是移動您原始關聯式資料庫管理系統 (RDBMS)，包括 Oracle、 IBM DB2、 MySQL、 PostgreSQL 或 SQL Server 到類似的伺服器在 Azure VM 上執行。 如果您有現有的應用程式完全需要最快速移轉至雲端，幾乎不需要變更或完全不變更時，直接移轉至雲端中的 IaaS 可能是合理的選項。 它可能無法利用所有的雲端優勢的最佳辦法，但它可能是最快速的初始路徑。

目前，Microsoft Azure 支援最多[331 不同資料庫伺服器](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all)部署為 IaaS Vm。 這些包括常用的 RDBMS，例如 SQL Server、 Oracle、 MySQL、 PostgreSQL 和 IBM DB2 和 MongoDB、 Cassandra、 DataStax、 MariaDB 和 Cloudera 等許多其他 NoSQL 資料庫。

> [!NOTE]
> 雖然移動您 RDBMS 至 Azure VM 可能是最快速的方式將資料移轉至雲端 （因為它是 IaaS），這種方法需要大量投資您的 IT 團隊 （資料庫管理員和 IT 專業人員）。 企業團隊必須要能夠設定和管理高可用性、 災害復原及修補 SQL Server。 此內容也需要自訂的環境中，以完整系統管理權限。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>為 VM (IaaS) 移轉至 SQL Server 的時機

可能有少數情況下，您仍然需要移轉至 SQL Server 和一般 VM。 如果您要使用 SQL Server Reporting Services 即為一例。 在大部分情況下，不過，Azure SQL Database 受控執行個體可以提供您需要讓移轉至 SQL Server VM 應該是您最後的手段，嘗試從內部部署 SQL 伺服器，移轉的所有項目。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>使用 Azure 資料庫移轉服務來將關聯式資料庫移轉至 Azure 

不論您的目標資料庫是 Azure SQL Database、 Azure SQL Database 受控執行個體或在 Azure VM 上的 SQL Server，您可以將 SQL Server、 Oracle 和 MySQL 等關聯式資料庫移轉至 Azure，使用 Azure 資料庫移轉服務。

自動化的工作流程中，透過評估報告，會引導您完成您需要先將資料庫移轉進行的變更。 準備好時，服務會將來源資料庫移轉至 Azure。

每當您變更原始 RDBMS 時，您可能需要重新測試。 您也可能需要變更的 SQL 句子或您的應用程式，根據測試結果中的物件關聯式對應 (ORM) 程式碼。

如果您有其他任何資料庫 (例如 IBM DB2)，而且您選擇使用原形方法，您可能想要繼續使用這些資料庫做為 IaaS Vm 在 Azure 中，除非您願意執行更複雜的資料移轉。 更複雜的資料移轉將會需要額外的工作，因為您會移轉至新的結構描述和不同的程式設計程式庫的不同的資料庫型別。

若要了解如何使用 Azure 資料庫移轉服務來移轉資料庫，請參閱[前往 Azure SQL Database 受控執行個體和 Azure 資料庫移轉服務使用更快速地定域機組](https://channel9.msdn.com/Events/Build/2017/P4008)。

## <a name="additional-resources"></a>其他資源

- **選擇雲端 SQL Server 選項：Azure SQL Database (PaaS) 或 Azure VM (IaaS) 上的 SQL Server**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **取得雲端使用 Azure SQL DB 受控執行個體和資料庫移轉服務更快**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **SQL Server 資料庫移轉至雲端中的 SQL Database**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Azure SQL Database**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **在虛擬機器上的 SQL Server**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
>[上一頁](lift-and-shift-existing-apps-azure-iaas.md)
>[下一頁](modernize-existing-apps-to-cloud-optimized/index.md)