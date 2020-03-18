---
title: 將關係資料庫移轉到 Azure
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |將關係資料庫移轉到 Azure
ms.date: 04/28/2018
ms.openlocfilehash: efd1548c3f74fc27450f4949d71a1c4d61907ba5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093620"
---
# <a name="migrate-your-relational-databases-to-azure"></a>將關係資料庫移轉到 Azure

願景：Azure 提供最全面的資料庫移轉。

在 Azure 中，您可以將資料庫伺服器直接遷移到 IaaS VM（純提升和移動），也可以遷移到 Azure SQL 資料庫，以獲得其他好處。 Azure SQL 資料庫提供託管實例和完整的資料庫即服務 （DBaaS） 選項。 圖 3-1 顯示了 Azure 中可用的多關係資料庫移轉路徑。

![Azure 中的資料庫移轉路徑](./media/image3-1.png)

**圖 3-1。** Azure 中的資料庫移轉路徑

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>何時遷移到 Azure SQL 資料庫託管實例

在大多數情況下，Azure SQL 資料庫託管實例是將資料移轉到 Azure 時考慮的最佳選擇。 如果要遷移 SQL Server 資料庫，並且需要幾乎 100% 的保證，以確保不需要重新構建應用程式或更改資料或資料存取碼，請選擇 Azure SQL 資料庫的託管實例功能。

如果對 SQL Server 實例級功能有其他要求，或者除了標準 Azure SQL 資料庫（單個資料庫模型）中提供的功能之外的隔離要求，Azure SQL 資料庫託管實例是最佳選項。 最後一個選擇是面向 PaaS 的，但它提供的功能與傳統 SQL 伺服器的功能不同。 遷移可能會產生摩擦。

例如，對實例級 SQL Server 功能進行大量投資的組織將受益于遷移到 SQL 託管實例。 實例級 SQL Server 功能的示例包括 SQL 通用語言運行時 （CLR） 集成、SQL Server 代理和跨資料庫查詢。 標準 Azure SQL 資料庫（單資料庫模型）中不支援這些功能。

在高度受監管的行業中運行且出於安全目的需要保持隔離的組織也可能受益于選擇 SQL 託管實例模型。

Azure SQL 資料庫中的託管實例具有以下特徵：

- 通過 Azure 虛擬網路進行安全隔離

- 應用表面相容性，具有以下功能：

  - SQL 伺服器代理和 SQL 伺服器探測器

  - 跨資料庫參考和查詢、SQL CLR、複製、更改資料捕獲 （CDC） 和服務代理

- 資料庫大小高達 35 TB

- 具有以下功能的最小停機時間遷移：

  - Azure 資料庫移轉服務

  - 本機備份和還原以及記錄傳送

借助這些功能，當您將現有應用程式資料庫移轉到 Azure SQL 資料庫時，託管實例模型為 SQL Server 提供了幾乎 100% 的 PaaS 優勢。 託管實例是一個 SQL Server 環境，您可以在其中繼續使用實例級功能，而無需更改應用程式設計。

託管實例可能最適合當前使用 SQL Server 且需要在雲中網路安全方面具有靈活性的企業。 這就像為 SQL 資料庫提供了專用虛擬網路。

## <a name="when-to-migrate-to-azure-sql-database"></a>何時遷移到 Azure SQL 資料庫

如前所述，標準 Azure SQL 資料庫是一個完全託管的關係 DBaaS。 SQL 資料庫目前管理著全球 38 個資料中心的數百萬個生產資料庫。 它支援廣泛的應用程式和工作負載，從管理直接交易資料到推動需要全球高級資料處理的資料密集型、任務關鍵型應用程式。

由於其完整的 PaaS 功能，因此，如果應用程式使用基本標準 SQL 資料庫，並且沒有其他實例功能，則應將其遷移到標準 Azure SQL 資料庫作為"預設選擇"。 標準 Azure SQL 資料庫中不支援 SQL Server 集成、SQL Server 代理和跨資料庫查詢等 SQL Server 功能。 這些功能僅在 Azure SQL 資料庫託管實例模型中可用。

Azure SQL 資料庫是專為應用開發人員構建的唯一智慧雲資料庫服務。 它還是唯一一個動態擴展且不停機的雲資料庫服務，可説明您高效地交付多租戶應用。 最終，Azure SQL 資料庫讓您有更多時間進行創新，並加快您的上市時間。 您可以使用您喜歡的語言和平臺構建安全應用並連接到 SQL 資料庫。

Azure SQL 資料庫具有以下優點：

- 內置智慧（機器學習），可學習和適應您的應用

- 按需資料庫預配

- 適用于所有工作負載的一系列優惠

- 99.99% 可用性 SLA，零維護

- 用於資料保護的異地複製和恢復服務

- Azure SQL 資料庫時間點還原功能

- 與 SQL Server 2016 的相容性，包括混合和遷移

與 Azure SQL 資料庫託管實例相比，標準 Azure SQL 資料庫更接近 PaaS。 首選標準 Azure SQL 資料庫，因為您將從託管雲中獲得更多好處。 但是，Azure SQL 資料庫與常規和本地 SQL Server 實例有一些關鍵區別。 根據現有應用程式的資料庫要求以及企業要求和策略，在規劃遷移到雲時，它可能不是最佳選擇。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>何時將原始 RDBMS 移動到 VM （IaaS）

遷移選項之一是將原始關係資料庫管理系統 （RDBMS）移動到 Azure VM 上運行的類似伺服器，包括 Oracle、IBM DB2、MySQL、PostgreSQL 或 SQL Server。 如果您有需要以最快速度遷移到雲的應用程式，但更改最少，或者根本沒有更改，則直接遷移到雲中的 IaaS 可能是一個公平的選擇。 它可能不是利用雲的所有優勢的最佳方式，但它可能是最快的初始路徑。

目前，Microsoft Azure 支援多達[331 台不同的資料庫伺服器](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all)，這些伺服器部署為 IaaS VM。 其中包括流行的 RDBMS，如 SQL Server、Oracle、MySQL、PostgreSQL 和 IBM DB2，以及許多其他 NoSQL 資料庫，如蒙戈DB、卡珊多拉資料庫、DataStax、MariaDB 和 Cloudera。

> [!NOTE]
> 儘管將 RDBMS 遷移到 Azure VM 可能是將資料移轉到雲的最快方式（因為它是 IaaS），但此方法需要對 IT 團隊（資料庫管理員和 IT 專業人員）進行大量投資。 企業團隊需要能夠設置和管理 SQL Server 的高可用性、災害復原和修補。 此上下文還需要一個具有完全管理許可權的自訂環境。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>何時以 VM （IaaS） 遷移到 SQL 伺服器

可能還需要作為常規 VM 遷移到 SQL Server。 示例方案是，如果需要使用 SQL 伺服器報表服務。 但是，在大多數情況下，Azure SQL 資料庫託管實例可以提供從本地 SQL 伺服器遷移所需的一切，因此遷移到 SQL Server VM 應該是您嘗試的最後手段。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>使用 Azure 資料庫移轉服務將關係資料庫移轉到 Azure

您可以使用 Azure 資料庫移轉服務將關係資料庫（如 SQL Server、Oracle 和 MySQL）遷移到 Azure，無論您的目標資料庫是 Azure SQL 資料庫、Azure SQL 資料庫託管實例還是 Azure VM 上的 SQL Server。

自動工作流帶有評估報告，可指導您在遷移資料庫之前完成所需的更改。 準備就緒後，該服務會將源資料庫移轉到 Azure。

每當更改原始 RDBMS 時，您可能需要重新測試。 您可能還需要更改應用程式中的 SQL 句子或物件關係映射 （ORM） 代碼，具體取決於測試結果。

如果您有任何其他資料庫（例如 IBM DB2），並且選擇提升和移動方法，則可能需要繼續將這些資料庫用作 Azure 中的 IaaS VM，除非您願意執行更複雜的資料移轉。 更複雜的資料移轉需要付出額外的努力，因為您將使用新的架構和不同的程式設計庫遷移到不同的資料庫類型。

要瞭解如何使用 Azure 資料庫移轉服務遷移資料庫，請參閱[使用 Azure SQL 資料庫託管實例和 Azure 資料庫移轉服務更快地訪問雲](https://channel9.msdn.com/Events/Build/2017/P4008)。

## <a name="additional-resources"></a>其他資源

- **選擇雲 SQL 伺服器選項：Azure SQL 資料庫 （PaaS） 或 Azure VM 上的 SQL 伺服器 （IaaS）**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **使用 Azure SQL DB 託管實例和資料庫移轉服務更快地訪問雲**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **SQL Server 資料庫移轉至雲端 SQL Database**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **虛擬機器上的 SQL 伺服器**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [上一個](lift-and-shift-existing-apps-azure-iaas.md)
> [下一個](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
