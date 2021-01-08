---
title: 將關聯式資料庫移轉至 Azure
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |將您的關係資料庫移轉至 Azure
ms.date: 12/21/2020
ms.openlocfilehash: c8dc92e1c5c5fb36a68bcad000c10e47c946ca0c
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025377"
---
# <a name="migrate-your-relational-databases-to-azure"></a>將關聯式資料庫移轉至 Azure

願景： Azure 提供最全面的資料庫移轉。

在 Azure 中，您可以將資料庫伺服器直接遷移至 IaaS Vm (單純的隨即轉移) ，也可以遷移至 Azure SQL Database，以獲得更多優點。 Azure SQL Database 提供受控實例和完整的資料庫即服務 (DBaaS) 選項。 圖3-1 顯示 Azure 中可使用的多個關係資料庫移轉路徑。

![Azure 中的資料庫移轉路徑](./media/image3-1.png)

**圖3-1。** Azure 中的資料庫移轉路徑

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>遷移至 Azure SQL Database 受控執行個體的時機

在大多數情況下，當您將資料移轉至 Azure 時，Azure SQL Database 受控執行個體將是您最好考慮的選項。 如果您要遷移 SQL Server 的資料庫，而且需要將近100% 的保證，您不需要重新架構應用程式，也不需要變更您的資料或資料存取程式碼，請選擇 Azure SQL Database 的受控執行個體功能。

如果您有 SQL Server 實例層級功能的額外需求，或是除了標準 Azure SQL Database (單一資料庫模型) 中提供的功能以外的隔離需求，Azure SQL Database 受控執行個體是最佳選項。 最後一個是最適合 PaaS 導向的選擇，但它並不提供與傳統 SQL server 相同的功能。 遷移可能會呈現摩擦。

例如，在實例層級 SQL Server 功能中進行深度投資的組織，將可受益于遷移至 SQL 受控執行個體。 實例層級 SQL Server 功能的範例包括 SQL common language runtime (CLR) 整合、SQL Server Agent 和跨資料庫查詢。 標準 Azure SQL Database 不提供這些功能的支援 (單一資料庫模型) 。

在高度管制的產業中運作，而且基於安全性目的而需要維護隔離的組織，也可能會因為選擇 SQL 受控執行個體模型而有所説明。

Azure SQL Database 中的受控執行個體具有下列特性：

- 透過 Azure 虛擬網路的安全性隔離

- 使用這些功能的應用程式介面相容性：

  - SQL Server Agent 和 SQL Server Profiler

  - 跨資料庫參考和查詢、SQL CLR、複寫、變更資料捕獲 (CDC) 和 Service Broker

- 最高達 35 TB 的資料庫大小

- 使用下列功能的最少停機時間遷移：

  - Azure 資料庫移轉服務

  - 原生備份和還原，以及記錄傳送

使用這些功能時，當您將現有的應用程式資料庫移轉至 Azure SQL Database 時，受控執行個體模型可提供 PaaS for SQL Server 的將近100% 優點。 受控執行個體是一種 SQL Server 的環境，可讓您繼續使用實例層級的功能，而不需要變更應用程式設計。

受控執行個體可能最適合目前使用 SQL Server 的企業，且需要在雲端的網路安全性方面提供彈性。 它就像是 SQL 資料庫的私人虛擬網路。

## <a name="when-to-migrate-to-azure-sql-database"></a>遷移至 Azure SQL Database 的時機

如前所述，標準 Azure SQL Database 是完全受控的關聯式 DBaaS。 SQL Database 目前在全球各地的38資料中心管理數百萬個生產資料庫。 它支援各種不同的應用程式和工作負載，從管理簡單的交易資料，到需要以全球規模進行先進資料處理的最大量資料、任務關鍵性應用程式。

由於其完整的 PaaS 功能、更好的定價和最終成本較低，因此，如果您的應用程式使用基本、標準 SQL 資料庫，而且沒有其他實例功能，則您應該移至標準 Azure SQL Database 作為「預設選擇」。 標準 Azure SQL Database 不支援 SQL CLR 整合、SQL Server Agent 和跨資料庫查詢等 SQL Server 功能。 這些功能僅適用于 Azure SQL Database 受控執行個體模型。

Azure SQL Database 是專為應用程式開發人員打造的智慧型雲端資料庫服務。 這也是唯一可即時調整而不需要停機的雲端資料庫服務，可協助您有效率地提供多組織使用者共用應用程式。 最後，Azure SQL Database 可讓您更輕鬆地進行創新，而且可加速您的上市時間。 您可以使用您偏好的語言和平臺來建立安全的應用程式，並連接到您的 SQL database。

Azure SQL Database 提供下列優點：

- 內建智慧 (機器學習) ，可學習和適應您的應用程式

- 依需求提供的資料庫布建

- 適用于所有工作負載的優惠範圍

- 99.99% 可用性 SLA，零維護

- 適用于資料保護的異地複寫和還原服務

- Azure SQL Database 時間點還原功能

- 與 SQL Server 2016 （包括混合式和遷移）的相容性

標準 Azure SQL Database 比 Azure SQL Database 受控執行個體更接近 PaaS。 偏好使用標準 Azure SQL Database，因為您會從受控雲端獲得更多的權益。 不過，Azure SQL Database 與一般和內部部署 SQL Server 實例之間有一些重要的差異。 根據您現有應用程式的資料庫需求，以及您的企業需求和原則，當您計畫遷移至雲端時，這可能不是最佳選擇。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>將原始 RDBMS 移至 VM (IaaS) 

其中一個遷移選項是將您的原始關係資料庫管理)  (系統（包括 Oracle、IBM DB2、MySQL、于 postgresql 或 SQL Server）移至在 Azure VM 上執行的類似伺服器。 如果您的現有應用程式需要最快速地遷移至雲端，但變更最短，或完全沒有變更，則直接遷移至雲端中的 IaaS 可能是合理的選擇。 這可能不是充分利用雲端優勢的最佳方式，但可能是最快的初始路徑。

目前，Microsoft Azure 支援最多331個部署為 IaaS Vm 的 [不同資料庫伺服器](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) 。 這些包括熱門的 RDBMS，例如 SQL Server、Oracle、MySQL、于 postgresql 和 IBM DB2，以及其他許多 NoSQL 資料庫（例如 MongoDB、Cassandra、DataStax、適用于 mariadb 和 Cloudera）。

> [!NOTE]
> 雖然將 RDBMS 移至 Azure VM 可能是將資料移轉至雲端的最快方法 (因為它是 IaaS) ，所以這種方法需要在您的 IT 小組 (資料庫管理員和 IT 專業人員) 進行大量投資。 企業小組必須能夠設定和管理 SQL Server 的高可用性、嚴重損壞修復和修補。 此內容也需要具有完整系統管理許可權的自訂環境。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>遷移至 SQL Server 作為 VM (IaaS) 

在一些情況下，您仍然需要以一般 VM 的形式遷移至 SQL Server。 如果您需要使用 SQL Server Reporting Services，則為範例案例。 不過，在大部分情況下，Azure SQL Database 受控執行個體可以提供從內部部署 SQL server 遷移所需的所有專案，因此您必須先嘗試進行遷移至 SQL Server VM。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>使用 Azure 資料庫移轉服務將您的關係資料庫移轉至 Azure

您可以使用 Azure 資料庫移轉服務，將 SQL Server、Oracle 和 MySQL 等關係資料庫移轉至 Azure，無論您的目標資料庫是在 Azure VM 上 Azure SQL Database、Azure SQL Database 受控執行個體或 SQL Server。

自動化工作流程（含評量報告）會引導您完成在遷移資料庫之前所需進行的變更。 當您準備好時，服務會將源資料庫移轉至 Azure。

每當您變更原始 RDBMS 時，可能需要重新測試。 您也可能需要根據測試結果，在您的應用程式中變更 SQL 句子或 Object-Relational 對應 (ORM) 程式碼。

如果您有任何其他資料庫 (例如 IBM DB2) ，而您選擇了增益和轉移方法，除非您願意執行更複雜的資料移轉，否則您可能會想要繼續在 Azure 中使用這些資料庫作為 IaaS Vm。 更複雜的資料移轉將需要額外的工作，因為您要使用新的架構和不同的程式設計程式庫遷移至不同的資料庫類型。

若要瞭解如何使用 Azure 資料庫移轉服務來遷移資料庫，請參閱 [Azure SQL Database 受控執行個體和 Azure 資料庫移轉服務，以更快的速度進入雲端](https://channel9.msdn.com/Events/Build/2017/P4008)。

## <a name="additional-resources"></a>其他資源

- **選擇雲端 SQL Server 選項： Azure SQL Database Azure VM 上的 (PaaS) 或 SQL Server (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **使用 Azure SQL DB 受控執行個體和資料庫移轉服務，更快進入雲端**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **SQL Server 資料庫移轉至雲端 SQL Database**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **虛擬機器上的 SQL Server**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [上一個](lift-and-shift-existing-apps-azure-iaas.md) 
> [下一步](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
