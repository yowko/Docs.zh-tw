---
title: 將您的關係資料庫移轉至 azure
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |將您的關係資料庫移轉至 azure
ms.date: 04/28/2018
ms.openlocfilehash: 982050d99aaa66cde1168a2f2fa64ed5f3e9163b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660736"
---
# <a name="migrate-your-relational-databases-to-azure"></a>將您的關係資料庫移轉至 azure

願景：Azure 提供最完整的資料庫移轉。

在 Azure 中, 您可以將資料庫伺服器直接遷移到 IaaS Vm (單純的隨即轉移), 或者您可以遷移到 Azure SQL Database, 以獲得更多好處。 Azure SQL Database 提供受控實例和完整的資料庫即服務 (DBaaS) 選項。 圖3-1 顯示 Azure 中提供的多個關係資料庫移轉路徑。

![Azure 中的資料庫移轉路徑](./media/image3-1.png)

> **圖 3-1** Azure 中的資料庫移轉路徑

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>遷移至 Azure SQL Database 受控執行個體的時機

在大部分情況下, 當您將資料移轉至 Azure 時, Azure SQL Database 受控執行個體會是您最好考慮的選項。 如果您要遷移 SQL Server 資料庫, 而且需要幾乎 100% 保證, 而不需要重新架構您的應用程式或變更您的資料或資料存取程式碼, 請選擇 Azure SQL Database 的受控執行個體功能。

如果您有 SQL Server 實例層級功能的額外需求, 或超出標準 Azure SQL Database (單一資料庫模型) 所提供之功能的隔離需求, Azure SQL Database 受控執行個體是最佳選項。 最後一個是 PaaS 導向的選擇, 但它並不提供與傳統 SQL server 相同的功能。 遷移可能會呈現摩擦。

例如, 在實例層級 SQL Server 功能中進行深度投資的組織, 將可受益于遷移至 SQL 受控執行個體。 實例層級 SQL Server 功能的範例包括 SQL common language runtime (CLR) 整合、SQL Server Agent 和跨資料庫查詢。 標準 Azure SQL Database (單一資料庫模型) 不提供這些功能的支援。

在高度規範的產業中操作, 而且基於安全性目的而需要維護隔離的組織, 也可能受益于選擇 SQL 受控執行個體模型。

Azure SQL Database 中的受控執行個體具有下列特性:

- 透過 Azure 虛擬網路的安全性隔離

- 應用程式介面相容性, 具備下列功能:

  - SQL Server Agent 和 SQL Server Profiler

  - 跨資料庫參考和查詢、SQL CLR、複寫、變更資料捕獲 (CDC) 和 Service Broker

- 資料庫大小上限為 35 TB

- 最小停機時間遷移, 具備下列功能:

  - Azure 資料庫移轉服務

  - 原生備份和還原, 以及記錄傳送

有了這些功能, 當您將現有的應用程式資料庫移轉至 Azure SQL Database 時, 受控執行個體模型可為 SQL Server 的 PaaS 提供將近 100% 的優勢。 受控執行個體是一個 SQL Server 的環境, 您可以繼續使用實例層級的功能, 而不需要變更應用程式設計。

受控執行個體可能最適合目前使用 SQL Server 的企業, 而且需要在雲端的網路安全性中提供彈性。 就像是為您的 SQL 資料庫提供私人虛擬網路。

## <a name="when-to-migrate-to-azure-sql-database"></a>遷移至 Azure SQL Database 的時機

如前所述, 標準 Azure SQL Database 是完全受控的關聯式 DBaaS。 SQL Database 目前管理數百萬個生產資料庫, 跨38個資料中心, 在全球各地。 它支援廣泛的應用程式和工作負載, 從管理直接的交易資料, 到驅動最需要大量資料的任務關鍵性應用程式, 以全球規模進行先進的資料處理。

因為它是完整的 PaaS 功能, 所以價格較佳, 而且最終成本較低-如果您的應用程式使用基本、標準 SQL 資料庫, 而且沒有其他實例功能, 您應該移至標準 Azure SQL Database 做為您的「預設選擇」。 標準 Azure SQL Database 中不支援 SQL CLR 整合、SQL Server Agent 和跨資料庫查詢之類的 SQL Server 功能。 這些功能僅適用于 Azure SQL Database 受控執行個體模型。

Azure SQL Database 是專為應用程式開發人員打造的唯一智慧型雲端資料庫服務。 這也是唯一可即時調整而不會停機的雲端資料庫服務, 以協助您有效率地傳遞多組織使用者共用應用程式。 最後, Azure SQL Database 會讓您更多時間進行創新, 並加速您的上市時間。 您可以使用您偏好的語言和平臺, 建立安全的應用程式, 並連接到您的 SQL 資料庫。

Azure SQL Database 提供下列優點:

- 可學習並適應您應用程式的內建智慧 (機器學習)

- 視需要提供的資料庫布建

- 適用于所有工作負載的優惠範圍

- 99.99% 可用性 SLA, 零維護

- 適用于資料保護的異地複寫與還原服務

- Azure SQL Database 時間點還原功能

- 與 SQL Server 2016 的相容性, 包括混合式和遷移

標準 Azure SQL Database 比 Azure SQL Database 受控執行個體更接近 PaaS。 偏好使用標準 Azure SQL Database, 因為您會從受控雲端獲得更多好處。 不過, Azure SQL Database 與一般和內部部署 SQL Server 實例有一些主要差異。 根據您現有應用程式的資料庫需求, 以及您的企業需求和原則, 當您打算遷移至雲端時, 這可能不是最佳選擇。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>將原始 RDBMS 移至 VM (IaaS) 的時機

其中一個遷移選項是將您的原始關係資料庫管理系統 (RDBMS) (包括 Oracle、IBM DB2、MySQL、于 postgresql 或 SQL Server) 移至在 Azure VM 上執行的類似伺服器。 如果您現有的應用程式需要最少的變更, 最快速的雲端遷移, 或根本沒有變更, 則直接遷移至雲端中的 IaaS 可能是合理的選擇。 這可能不是利用所有雲端優勢的最佳方式, 但可能是最快的初始路徑。

目前, Microsoft Azure 支援最多331個部署為 IaaS Vm 的[不同資料庫伺服器](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all)。 這些包括熱門的 RDBMS, 例如 SQL Server、Oracle、MySQL、于 postgresql 和 IBM DB2, 以及其他許多 NoSQL 資料庫, 例如 MongoDB、Cassandra、DataStax、適用于 mariadb 和 Cloudera。

> [!NOTE]
> 雖然將您的 RDBMS 移至 Azure VM 可能是將資料移轉至雲端的最快方式 (因為它是 IaaS), 但這種方法需要在您的 IT 小組 (資料庫管理員和 IT 專業人員) 中進行大量投資。 企業小組必須能夠設定和管理 SQL Server 的高可用性、嚴重損壞修復和修補。 此內容也需要具有完整系統管理許可權的自訂環境。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>何時以 VM (IaaS) 的形式遷移至 SQL Server

在一些情況下, 您仍然需要以一般 VM 的方式遷移至 SQL Server。 例如, 如果您需要使用 SQL Server Reporting Services, 就會發生這種情況。 不過, 在大多數情況下, Azure SQL Database 受控執行個體可以提供從內部部署 SQL 伺服器進行遷移所需的所有專案, 因此您必須先嘗試遷移至 SQL Server VM。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>使用 Azure 資料庫移轉服務, 將您的關係資料庫移轉至 Azure 

您可以使用 Azure 資料庫移轉服務, 將 SQL Server、Oracle 和 MySQL 之類的關係資料庫移轉至 Azure, 不論您的目標資料庫是在 Azure VM 上 Azure SQL Database、Azure SQL Database 受控執行個體或 SQL Server。

自動化的工作流程和評量報告, 會引導您完成在遷移資料庫之前所需進行的變更。 當您準備好時, 服務會將源資料庫移轉至 Azure。

每當您變更原始 RDBMS 時, 可能需要重新測試。 視測試結果而定, 您也可能需要變更應用程式中的 SQL 句子或物件關聯式對應 (ORM) 程式碼。

如果您有任何其他資料庫 (例如, IBM DB2), 而您選擇了隨即轉移方法, 您可能會想要在 Azure 中繼續使用這些資料庫做為 IaaS Vm, 除非您願意執行更複雜的資料移轉。 較複雜的資料移轉需要額外的工作, 因為您會使用新的架構和不同的程式設計程式庫來遷移至不同的資料庫類型。

若要瞭解如何使用 Azure 資料庫移轉服務來遷移資料庫, 請參閱[使用 Azure SQL Database 受控執行個體和 Azure 資料庫移轉服務更快取得雲端](https://channel9.msdn.com/Events/Build/2017/P4008)。

## <a name="additional-resources"></a>其他資源

- **選擇雲端 SQL Server 選項:在 Azure VM (IaaS) 上 Azure SQL Database (PaaS) 或 SQL Server**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **使用 Azure SQL DB 受控執行個體和資料庫移轉服務, 更快取得雲端**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **SQL Server 資料庫移轉至雲端 SQL Database**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **虛擬機器上的 SQL Server**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [上一頁](lift-and-shift-existing-apps-azure-iaas.md)
> [下一頁](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
