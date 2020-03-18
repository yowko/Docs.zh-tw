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
# <a name="migrate-your-relational-databases-to-azure"></a><span data-ttu-id="ae095-103">將關係資料庫移轉到 Azure</span><span class="sxs-lookup"><span data-stu-id="ae095-103">Migrate your relational databases to azure</span></span>

<span data-ttu-id="ae095-104">願景：Azure 提供最全面的資料庫移轉。</span><span class="sxs-lookup"><span data-stu-id="ae095-104">Vision: Azure offers the most comprehensive database migration.</span></span>

<span data-ttu-id="ae095-105">在 Azure 中，您可以將資料庫伺服器直接遷移到 IaaS VM（純提升和移動），也可以遷移到 Azure SQL 資料庫，以獲得其他好處。</span><span class="sxs-lookup"><span data-stu-id="ae095-105">In Azure, you can migrate your database servers directly to IaaS VMs (pure lift and shift), or you can migrate to Azure SQL Database, for additional benefits.</span></span> <span data-ttu-id="ae095-106">Azure SQL 資料庫提供託管實例和完整的資料庫即服務 （DBaaS） 選項。</span><span class="sxs-lookup"><span data-stu-id="ae095-106">Azure SQL Database offers managed instance and full database-as-a-service (DBaaS) options.</span></span> <span data-ttu-id="ae095-107">圖 3-1 顯示了 Azure 中可用的多關係資料庫移轉路徑。</span><span class="sxs-lookup"><span data-stu-id="ae095-107">Figure 3-1 shows the multiple relational database migration paths available in Azure.</span></span>

![Azure 中的資料庫移轉路徑](./media/image3-1.png)

<span data-ttu-id="ae095-109">**圖 3-1。**</span><span class="sxs-lookup"><span data-stu-id="ae095-109">**Figure 3-1.**</span></span> <span data-ttu-id="ae095-110">Azure 中的資料庫移轉路徑</span><span class="sxs-lookup"><span data-stu-id="ae095-110">Database migration paths in Azure</span></span>

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a><span data-ttu-id="ae095-111">何時遷移到 Azure SQL 資料庫託管實例</span><span class="sxs-lookup"><span data-stu-id="ae095-111">When to migrate to Azure SQL Database Managed Instance</span></span>

<span data-ttu-id="ae095-112">在大多數情況下，Azure SQL 資料庫託管實例是將資料移轉到 Azure 時考慮的最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="ae095-112">In most cases, Azure SQL Database Managed Instance will be your best option to consider when you migrate your data to Azure.</span></span> <span data-ttu-id="ae095-113">如果要遷移 SQL Server 資料庫，並且需要幾乎 100% 的保證，以確保不需要重新構建應用程式或更改資料或資料存取碼，請選擇 Azure SQL 資料庫的託管實例功能。</span><span class="sxs-lookup"><span data-stu-id="ae095-113">If you are migrating SQL Server databases and need nearly 100% assurance that you won't need to rearchitect your application or make changes to your data or data access code, choose the Managed Instance feature of Azure SQL Database.</span></span>

<span data-ttu-id="ae095-114">如果對 SQL Server 實例級功能有其他要求，或者除了標準 Azure SQL 資料庫（單個資料庫模型）中提供的功能之外的隔離要求，Azure SQL 資料庫託管實例是最佳選項。</span><span class="sxs-lookup"><span data-stu-id="ae095-114">Azure SQL Database Managed Instance is the best option if you have additional requirements for SQL Server instance-level functionality, or isolation requirements beyond the features provided in a standard Azure SQL Database (single database model).</span></span> <span data-ttu-id="ae095-115">最後一個選擇是面向 PaaS 的，但它提供的功能與傳統 SQL 伺服器的功能不同。</span><span class="sxs-lookup"><span data-stu-id="ae095-115">This last one is the most PaaS-oriented choice, but it doesn't offer the same features as that of a traditional SQL server.</span></span> <span data-ttu-id="ae095-116">遷移可能會產生摩擦。</span><span class="sxs-lookup"><span data-stu-id="ae095-116">Migration might surface frictions.</span></span>

<span data-ttu-id="ae095-117">例如，對實例級 SQL Server 功能進行大量投資的組織將受益于遷移到 SQL 託管實例。</span><span class="sxs-lookup"><span data-stu-id="ae095-117">For example, an organization that has made deep investments in instance-level SQL Server capabilities would benefit from migrating to SQL Managed Instance.</span></span> <span data-ttu-id="ae095-118">實例級 SQL Server 功能的示例包括 SQL 通用語言運行時 （CLR） 集成、SQL Server 代理和跨資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="ae095-118">Examples of instance-level SQL Server capabilities include SQL common language runtime (CLR) integration, SQL Server Agent, and cross-database querying.</span></span> <span data-ttu-id="ae095-119">標準 Azure SQL 資料庫（單資料庫模型）中不支援這些功能。</span><span class="sxs-lookup"><span data-stu-id="ae095-119">Support for these features is not available in standard Azure SQL Database (a single-database model).</span></span>

<span data-ttu-id="ae095-120">在高度受監管的行業中運行且出於安全目的需要保持隔離的組織也可能受益于選擇 SQL 託管實例模型。</span><span class="sxs-lookup"><span data-stu-id="ae095-120">An organization that operates in a highly regulated industry, and which needs to maintain isolation for security purposes, also might benefit from choosing the SQL Managed Instance model.</span></span>

<span data-ttu-id="ae095-121">Azure SQL 資料庫中的託管實例具有以下特徵：</span><span class="sxs-lookup"><span data-stu-id="ae095-121">Managed Instance in Azure SQL Database has the following characteristics:</span></span>

- <span data-ttu-id="ae095-122">通過 Azure 虛擬網路進行安全隔離</span><span class="sxs-lookup"><span data-stu-id="ae095-122">Security isolation through Azure Virtual Network</span></span>

- <span data-ttu-id="ae095-123">應用表面相容性，具有以下功能：</span><span class="sxs-lookup"><span data-stu-id="ae095-123">Application surface compatibility, with these features:</span></span>

  - <span data-ttu-id="ae095-124">SQL 伺服器代理和 SQL 伺服器探測器</span><span class="sxs-lookup"><span data-stu-id="ae095-124">SQL Server Agent and SQL Server Profiler</span></span>

  - <span data-ttu-id="ae095-125">跨資料庫參考和查詢、SQL CLR、複製、更改資料捕獲 （CDC） 和服務代理</span><span class="sxs-lookup"><span data-stu-id="ae095-125">Cross-database references and queries, SQL CLR, replication, change data capture (CDC), and Service Broker</span></span>

- <span data-ttu-id="ae095-126">資料庫大小高達 35 TB</span><span class="sxs-lookup"><span data-stu-id="ae095-126">Database sizes up to 35 TB</span></span>

- <span data-ttu-id="ae095-127">具有以下功能的最小停機時間遷移：</span><span class="sxs-lookup"><span data-stu-id="ae095-127">Minimum-downtime migration, with these features:</span></span>

  - <span data-ttu-id="ae095-128">Azure 資料庫移轉服務</span><span class="sxs-lookup"><span data-stu-id="ae095-128">Azure Database Migration Service</span></span>

  - <span data-ttu-id="ae095-129">本機備份和還原以及記錄傳送</span><span class="sxs-lookup"><span data-stu-id="ae095-129">Native backup and restore, and log shipping</span></span>

<span data-ttu-id="ae095-130">借助這些功能，當您將現有應用程式資料庫移轉到 Azure SQL 資料庫時，託管實例模型為 SQL Server 提供了幾乎 100% 的 PaaS 優勢。</span><span class="sxs-lookup"><span data-stu-id="ae095-130">With these capabilities, when you migrate existing application databases to Azure SQL Database, the Managed Instance model offers nearly 100% of the benefits of PaaS for SQL Server.</span></span> <span data-ttu-id="ae095-131">託管實例是一個 SQL Server 環境，您可以在其中繼續使用實例級功能，而無需更改應用程式設計。</span><span class="sxs-lookup"><span data-stu-id="ae095-131">Managed Instance is a SQL Server environment where you continue using instance-level capabilities without changing your application design.</span></span>

<span data-ttu-id="ae095-132">託管實例可能最適合當前使用 SQL Server 且需要在雲中網路安全方面具有靈活性的企業。</span><span class="sxs-lookup"><span data-stu-id="ae095-132">Managed Instance is probably the best fit for enterprises that currently are using SQL Server, and which require flexibility in their network security in the cloud.</span></span> <span data-ttu-id="ae095-133">這就像為 SQL 資料庫提供了專用虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ae095-133">It's like having a private virtual network for your SQL databases.</span></span>

## <a name="when-to-migrate-to-azure-sql-database"></a><span data-ttu-id="ae095-134">何時遷移到 Azure SQL 資料庫</span><span class="sxs-lookup"><span data-stu-id="ae095-134">When to migrate to Azure SQL Database</span></span>

<span data-ttu-id="ae095-135">如前所述，標準 Azure SQL 資料庫是一個完全託管的關係 DBaaS。</span><span class="sxs-lookup"><span data-stu-id="ae095-135">As mentioned, the standard Azure SQL Database is a fully managed, relational DBaaS.</span></span> <span data-ttu-id="ae095-136">SQL 資料庫目前管理著全球 38 個資料中心的數百萬個生產資料庫。</span><span class="sxs-lookup"><span data-stu-id="ae095-136">SQL Database currently manages millions of production databases, across 38 datacenters, around the world.</span></span> <span data-ttu-id="ae095-137">它支援廣泛的應用程式和工作負載，從管理直接交易資料到推動需要全球高級資料處理的資料密集型、任務關鍵型應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae095-137">It supports a broad range of applications and workloads, from managing straightforward transactional data, to driving the most data-intensive, mission-critical applications that require advanced data processing at a global scale.</span></span>

<span data-ttu-id="ae095-138">由於其完整的 PaaS 功能，因此，如果應用程式使用基本標準 SQL 資料庫，並且沒有其他實例功能，則應將其遷移到標準 Azure SQL 資料庫作為"預設選擇"。</span><span class="sxs-lookup"><span data-stu-id="ae095-138">Because of its full PaaS features, better pricing-and ultimately lower cost-you should move to the standard Azure SQL Database as your "by-default choice" if you have an application that uses basic, standard SQL databases, and no additional instance features.</span></span> <span data-ttu-id="ae095-139">標準 Azure SQL 資料庫中不支援 SQL Server 集成、SQL Server 代理和跨資料庫查詢等 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="ae095-139">SQL Server features like SQL CLR integration, SQL Server Agent, and cross-database querying are not supported in the standard Azure SQL Database.</span></span> <span data-ttu-id="ae095-140">這些功能僅在 Azure SQL 資料庫託管實例模型中可用。</span><span class="sxs-lookup"><span data-stu-id="ae095-140">Those features are available only in the Azure SQL Database Managed Instance model.</span></span>

<span data-ttu-id="ae095-141">Azure SQL 資料庫是專為應用開發人員構建的唯一智慧雲資料庫服務。</span><span class="sxs-lookup"><span data-stu-id="ae095-141">Azure SQL Database is the only intelligent cloud database service that's built for app developers.</span></span> <span data-ttu-id="ae095-142">它還是唯一一個動態擴展且不停機的雲資料庫服務，可説明您高效地交付多租戶應用。</span><span class="sxs-lookup"><span data-stu-id="ae095-142">It's also the only cloud database service that scales on-the-fly, without downtime, to help you efficiently deliver multitenant apps.</span></span> <span data-ttu-id="ae095-143">最終，Azure SQL 資料庫讓您有更多時間進行創新，並加快您的上市時間。</span><span class="sxs-lookup"><span data-stu-id="ae095-143">Ultimately, Azure SQL Database leaves you more time to innovate, and it accelerates your time to market.</span></span> <span data-ttu-id="ae095-144">您可以使用您喜歡的語言和平臺構建安全應用並連接到 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ae095-144">You can build secure apps and connect to your SQL database by using the languages and platforms that you prefer.</span></span>

<span data-ttu-id="ae095-145">Azure SQL 資料庫具有以下優點：</span><span class="sxs-lookup"><span data-stu-id="ae095-145">Azure SQL Database offers the following benefits:</span></span>

- <span data-ttu-id="ae095-146">內置智慧（機器學習），可學習和適應您的應用</span><span class="sxs-lookup"><span data-stu-id="ae095-146">Built-in intelligence (machine learning) that learns and adapts to your app</span></span>

- <span data-ttu-id="ae095-147">按需資料庫預配</span><span class="sxs-lookup"><span data-stu-id="ae095-147">On-demand database provisioning</span></span>

- <span data-ttu-id="ae095-148">適用于所有工作負載的一系列優惠</span><span class="sxs-lookup"><span data-stu-id="ae095-148">A range of offers, for all workloads</span></span>

- <span data-ttu-id="ae095-149">99.99% 可用性 SLA，零維護</span><span class="sxs-lookup"><span data-stu-id="ae095-149">99.99% availability SLA, zero maintenance</span></span>

- <span data-ttu-id="ae095-150">用於資料保護的異地複製和恢復服務</span><span class="sxs-lookup"><span data-stu-id="ae095-150">Geo-replication and restore services for data protection</span></span>

- <span data-ttu-id="ae095-151">Azure SQL 資料庫時間點還原功能</span><span class="sxs-lookup"><span data-stu-id="ae095-151">Azure SQL Database Point in Time Restore feature</span></span>

- <span data-ttu-id="ae095-152">與 SQL Server 2016 的相容性，包括混合和遷移</span><span class="sxs-lookup"><span data-stu-id="ae095-152">Compatibility with SQL Server 2016, including hybrid and migration</span></span>

<span data-ttu-id="ae095-153">與 Azure SQL 資料庫託管實例相比，標準 Azure SQL 資料庫更接近 PaaS。</span><span class="sxs-lookup"><span data-stu-id="ae095-153">The standard Azure SQL Database is closer to PaaS than Azure SQL Database Managed Instance.</span></span> <span data-ttu-id="ae095-154">首選標準 Azure SQL 資料庫，因為您將從託管雲中獲得更多好處。</span><span class="sxs-lookup"><span data-stu-id="ae095-154">Prefer the standard Azure SQL Database because you'll get more benefits from a managed cloud.</span></span> <span data-ttu-id="ae095-155">但是，Azure SQL 資料庫與常規和本地 SQL Server 實例有一些關鍵區別。</span><span class="sxs-lookup"><span data-stu-id="ae095-155">However, Azure SQL Database has some key differences from regular and on-premises SQL Server instances.</span></span> <span data-ttu-id="ae095-156">根據現有應用程式的資料庫要求以及企業要求和策略，在規劃遷移到雲時，它可能不是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="ae095-156">Depending on your existing application's database requirements, and your enterprise requirements and policies, it might not be the best choice when you are planning your migration to the cloud.</span></span>

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a><span data-ttu-id="ae095-157">何時將原始 RDBMS 移動到 VM （IaaS）</span><span class="sxs-lookup"><span data-stu-id="ae095-157">When to move your original RDBMS to a VM (IaaS)</span></span>

<span data-ttu-id="ae095-158">遷移選項之一是將原始關係資料庫管理系統 （RDBMS）移動到 Azure VM 上運行的類似伺服器，包括 Oracle、IBM DB2、MySQL、PostgreSQL 或 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ae095-158">One of your migration options is to move your original relational database management system (RDBMS), including Oracle, IBM DB2, MySQL, PostgreSQL, or SQL Server, to a similar server that's running on an Azure VM.</span></span> <span data-ttu-id="ae095-159">如果您有需要以最快速度遷移到雲的應用程式，但更改最少，或者根本沒有更改，則直接遷移到雲中的 IaaS 可能是一個公平的選擇。</span><span class="sxs-lookup"><span data-stu-id="ae095-159">If you have existing applications that require the fastest migration to the cloud with minimal changes, or no changes at all, a direct migration to IaaS in the cloud might be a fair option.</span></span> <span data-ttu-id="ae095-160">它可能不是利用雲的所有優勢的最佳方式，但它可能是最快的初始路徑。</span><span class="sxs-lookup"><span data-stu-id="ae095-160">It might not be the best way to take advantage of all the cloud's benefits, but it's probably the fastest initial path.</span></span>

<span data-ttu-id="ae095-161">目前，Microsoft Azure 支援多達[331 台不同的資料庫伺服器](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all)，這些伺服器部署為 IaaS VM。</span><span class="sxs-lookup"><span data-stu-id="ae095-161">Currently, Microsoft Azure supports up to [331 different database servers](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) deployed as IaaS VMs.</span></span> <span data-ttu-id="ae095-162">其中包括流行的 RDBMS，如 SQL Server、Oracle、MySQL、PostgreSQL 和 IBM DB2，以及許多其他 NoSQL 資料庫，如蒙戈DB、卡珊多拉資料庫、DataStax、MariaDB 和 Cloudera。</span><span class="sxs-lookup"><span data-stu-id="ae095-162">These include popular RDBMS like SQL Server, Oracle, MySQL, PostgreSQL, and IBM DB2, and many other NoSQL databases like MongoDB, Cassandra, DataStax, MariaDB, and Cloudera.</span></span>

> [!NOTE]
> <span data-ttu-id="ae095-163">儘管將 RDBMS 遷移到 Azure VM 可能是將資料移轉到雲的最快方式（因為它是 IaaS），但此方法需要對 IT 團隊（資料庫管理員和 IT 專業人員）進行大量投資。</span><span class="sxs-lookup"><span data-stu-id="ae095-163">Although moving your RDBMS to an Azure VM might be the fastest way to migrate your data to the cloud (because it is IaaS), this approach requires a significant investment in your IT teams (database administrators and IT pros).</span></span> <span data-ttu-id="ae095-164">企業團隊需要能夠設置和管理 SQL Server 的高可用性、災害復原和修補。</span><span class="sxs-lookup"><span data-stu-id="ae095-164">Enterprise teams need to be able to set up and manage high availability, disaster recovery, and patching for SQL Server.</span></span> <span data-ttu-id="ae095-165">此上下文還需要一個具有完全管理許可權的自訂環境。</span><span class="sxs-lookup"><span data-stu-id="ae095-165">This context also needs a customized environment, with full administrative rights.</span></span>

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a><span data-ttu-id="ae095-166">何時以 VM （IaaS） 遷移到 SQL 伺服器</span><span class="sxs-lookup"><span data-stu-id="ae095-166">When to migrate to SQL Server as a VM (IaaS)</span></span>

<span data-ttu-id="ae095-167">可能還需要作為常規 VM 遷移到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ae095-167">There might be a few cases where you still need to migrate to SQL Server as a regular VM.</span></span> <span data-ttu-id="ae095-168">示例方案是，如果需要使用 SQL 伺服器報表服務。</span><span class="sxs-lookup"><span data-stu-id="ae095-168">An example scenario is if you need to use SQL Server Reporting Services.</span></span> <span data-ttu-id="ae095-169">但是，在大多數情況下，Azure SQL 資料庫託管實例可以提供從本地 SQL 伺服器遷移所需的一切，因此遷移到 SQL Server VM 應該是您嘗試的最後手段。</span><span class="sxs-lookup"><span data-stu-id="ae095-169">In most cases, though, Azure SQL Database Managed Instance can provide everything you need to migrate from on-premises SQL servers, so migration to a SQL Server VM should be your last resort to try.</span></span>

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a><span data-ttu-id="ae095-170">使用 Azure 資料庫移轉服務將關係資料庫移轉到 Azure</span><span class="sxs-lookup"><span data-stu-id="ae095-170">Use Azure Database Migration Service to migrate your relational databases to Azure</span></span>

<span data-ttu-id="ae095-171">您可以使用 Azure 資料庫移轉服務將關係資料庫（如 SQL Server、Oracle 和 MySQL）遷移到 Azure，無論您的目標資料庫是 Azure SQL 資料庫、Azure SQL 資料庫託管實例還是 Azure VM 上的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ae095-171">You can use Azure Database Migration Service to migrate relational databases like SQL Server, Oracle, and MySQL to Azure, whether your target database is Azure SQL Database, Azure SQL Database Managed Instance, or SQL Server on an Azure VM.</span></span>

<span data-ttu-id="ae095-172">自動工作流帶有評估報告，可指導您在遷移資料庫之前完成所需的更改。</span><span class="sxs-lookup"><span data-stu-id="ae095-172">The automated workflow, with assessment reporting, guides you through the changes you need to make before you migrate the database.</span></span> <span data-ttu-id="ae095-173">準備就緒後，該服務會將源資料庫移轉到 Azure。</span><span class="sxs-lookup"><span data-stu-id="ae095-173">When you are ready, the service migrates the source database to Azure.</span></span>

<span data-ttu-id="ae095-174">每當更改原始 RDBMS 時，您可能需要重新測試。</span><span class="sxs-lookup"><span data-stu-id="ae095-174">Whenever you change an original RDBMS, you might need to retest.</span></span> <span data-ttu-id="ae095-175">您可能還需要更改應用程式中的 SQL 句子或物件關係映射 （ORM） 代碼，具體取決於測試結果。</span><span class="sxs-lookup"><span data-stu-id="ae095-175">You also might need to change the SQL sentences or Object-Relational Mapping (ORM) code in your application, depending on testing results.</span></span>

<span data-ttu-id="ae095-176">如果您有任何其他資料庫（例如 IBM DB2），並且選擇提升和移動方法，則可能需要繼續將這些資料庫用作 Azure 中的 IaaS VM，除非您願意執行更複雜的資料移轉。</span><span class="sxs-lookup"><span data-stu-id="ae095-176">If you have any other database (for example, IBM DB2) and you opt for a lift and shift approach, you might want to continue using those databases as IaaS VMs in Azure, unless you are willing to perform a more complex data migration.</span></span> <span data-ttu-id="ae095-177">更複雜的資料移轉需要付出額外的努力，因為您將使用新的架構和不同的程式設計庫遷移到不同的資料庫類型。</span><span class="sxs-lookup"><span data-stu-id="ae095-177">A more complex data migration will require additional effort because you'd be migrating to a different database type with new schema and different programming libraries.</span></span>

<span data-ttu-id="ae095-178">要瞭解如何使用 Azure 資料庫移轉服務遷移資料庫，請參閱[使用 Azure SQL 資料庫託管實例和 Azure 資料庫移轉服務更快地訪問雲](https://channel9.msdn.com/Events/Build/2017/P4008)。</span><span class="sxs-lookup"><span data-stu-id="ae095-178">To learn how to migrate databases by using Azure Database Migration Service, see [Get to the cloud faster with Azure SQL Database Managed Instance and Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ae095-179">其他資源</span><span class="sxs-lookup"><span data-stu-id="ae095-179">Additional resources</span></span>

- <span data-ttu-id="ae095-180">**選擇雲 SQL 伺服器選項：Azure SQL 資料庫 （PaaS） 或 Azure VM 上的 SQL 伺服器 （IaaS）**</span><span class="sxs-lookup"><span data-stu-id="ae095-180">**Choose a cloud SQL Server option: Azure SQL Database (PaaS) or SQL Server on Azure VM (IaaS)**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- <span data-ttu-id="ae095-181">**使用 Azure SQL DB 託管實例和資料庫移轉服務更快地訪問雲**</span><span class="sxs-lookup"><span data-stu-id="ae095-181">**Get to the cloud faster with Azure SQL DB Managed Instance and Database Migration Service**</span></span>

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- <span data-ttu-id="ae095-182">**SQL Server 資料庫移轉至雲端 SQL Database**</span><span class="sxs-lookup"><span data-stu-id="ae095-182">**SQL Server database migration to SQL Database in the cloud**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- <span data-ttu-id="ae095-183">**Azure SQL Database**</span><span class="sxs-lookup"><span data-stu-id="ae095-183">**Azure SQL Database**</span></span>

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- <span data-ttu-id="ae095-184">**虛擬機器上的 SQL 伺服器**</span><span class="sxs-lookup"><span data-stu-id="ae095-184">**SQL Server on virtual machines**</span></span>

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> <span data-ttu-id="ae095-185">[上一個](lift-and-shift-existing-apps-azure-iaas.md)
> [下一個](modernize-existing-apps-to-cloud-optimized/index.md)</span><span class="sxs-lookup"><span data-stu-id="ae095-185">[Previous](lift-and-shift-existing-apps-azure-iaas.md)
[Next](modernize-existing-apps-to-cloud-optimized/index.md)</span></span> <!-- Next Chapter -->
