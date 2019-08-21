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
# <a name="migrate-your-relational-databases-to-azure"></a><span data-ttu-id="fd2eb-103">將您的關係資料庫移轉至 azure</span><span class="sxs-lookup"><span data-stu-id="fd2eb-103">Migrate your relational databases to azure</span></span>

<span data-ttu-id="fd2eb-104">願景：Azure 提供最完整的資料庫移轉。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-104">Vision: Azure offers the most comprehensive database migration.</span></span>

<span data-ttu-id="fd2eb-105">在 Azure 中, 您可以將資料庫伺服器直接遷移到 IaaS Vm (單純的隨即轉移), 或者您可以遷移到 Azure SQL Database, 以獲得更多好處。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-105">In Azure, you can migrate your database servers directly to IaaS VMs (pure lift and shift), or you can migrate to Azure SQL Database, for additional benefits.</span></span> <span data-ttu-id="fd2eb-106">Azure SQL Database 提供受控實例和完整的資料庫即服務 (DBaaS) 選項。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-106">Azure SQL Database offers managed instance and full database-as-a-service (DBaaS) options.</span></span> <span data-ttu-id="fd2eb-107">圖3-1 顯示 Azure 中提供的多個關係資料庫移轉路徑。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-107">Figure 3-1 shows the multiple relational database migration paths available in Azure.</span></span>

![Azure 中的資料庫移轉路徑](./media/image3-1.png)

> <span data-ttu-id="fd2eb-109">**圖 3-1**</span><span class="sxs-lookup"><span data-stu-id="fd2eb-109">**Figure 3-1.**</span></span> <span data-ttu-id="fd2eb-110">Azure 中的資料庫移轉路徑</span><span class="sxs-lookup"><span data-stu-id="fd2eb-110">Database migration paths in Azure</span></span>

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a><span data-ttu-id="fd2eb-111">遷移至 Azure SQL Database 受控執行個體的時機</span><span class="sxs-lookup"><span data-stu-id="fd2eb-111">When to migrate to Azure SQL Database Managed Instance</span></span>

<span data-ttu-id="fd2eb-112">在大部分情況下, 當您將資料移轉至 Azure 時, Azure SQL Database 受控執行個體會是您最好考慮的選項。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-112">In most cases, Azure SQL Database Managed Instance will be your best option to consider when you migrate your data to Azure.</span></span> <span data-ttu-id="fd2eb-113">如果您要遷移 SQL Server 資料庫, 而且需要幾乎 100% 保證, 而不需要重新架構您的應用程式或變更您的資料或資料存取程式碼, 請選擇 Azure SQL Database 的受控執行個體功能。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-113">If you are migrating SQL Server databases and need nearly 100% assurance that you won't need to rearchitect your application or make changes to your data or data access code, choose the Managed Instance feature of Azure SQL Database.</span></span>

<span data-ttu-id="fd2eb-114">如果您有 SQL Server 實例層級功能的額外需求, 或超出標準 Azure SQL Database (單一資料庫模型) 所提供之功能的隔離需求, Azure SQL Database 受控執行個體是最佳選項。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-114">Azure SQL Database Managed Instance is the best option if you have additional requirements for SQL Server instance-level functionality, or isolation requirements beyond the features provided in a standard Azure SQL Database (single database model).</span></span> <span data-ttu-id="fd2eb-115">最後一個是 PaaS 導向的選擇, 但它並不提供與傳統 SQL server 相同的功能。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-115">This last one is the most PaaS-oriented choice, but it doesn't offer the same features as that of a traditional SQL server.</span></span> <span data-ttu-id="fd2eb-116">遷移可能會呈現摩擦。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-116">Migration might surface frictions.</span></span>

<span data-ttu-id="fd2eb-117">例如, 在實例層級 SQL Server 功能中進行深度投資的組織, 將可受益于遷移至 SQL 受控執行個體。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-117">For example, an organization that has made deep investments in instance-level SQL Server capabilities would benefit from migrating to SQL Managed Instance.</span></span> <span data-ttu-id="fd2eb-118">實例層級 SQL Server 功能的範例包括 SQL common language runtime (CLR) 整合、SQL Server Agent 和跨資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-118">Examples of instance-level SQL Server capabilities include SQL common language runtime (CLR) integration, SQL Server Agent, and cross-database querying.</span></span> <span data-ttu-id="fd2eb-119">標準 Azure SQL Database (單一資料庫模型) 不提供這些功能的支援。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-119">Support for these features is not available in standard Azure SQL Database (a single-database model).</span></span>

<span data-ttu-id="fd2eb-120">在高度規範的產業中操作, 而且基於安全性目的而需要維護隔離的組織, 也可能受益于選擇 SQL 受控執行個體模型。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-120">An organization that operates in a highly regulated industry, and which needs to maintain isolation for security purposes, also might benefit from choosing the SQL Managed Instance model.</span></span>

<span data-ttu-id="fd2eb-121">Azure SQL Database 中的受控執行個體具有下列特性:</span><span class="sxs-lookup"><span data-stu-id="fd2eb-121">Managed Instance in Azure SQL Database has the following characteristics:</span></span>

- <span data-ttu-id="fd2eb-122">透過 Azure 虛擬網路的安全性隔離</span><span class="sxs-lookup"><span data-stu-id="fd2eb-122">Security isolation through Azure Virtual Network</span></span>

- <span data-ttu-id="fd2eb-123">應用程式介面相容性, 具備下列功能:</span><span class="sxs-lookup"><span data-stu-id="fd2eb-123">Application surface compatibility, with these features:</span></span>

  - <span data-ttu-id="fd2eb-124">SQL Server Agent 和 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="fd2eb-124">SQL Server Agent and SQL Server Profiler</span></span>

  - <span data-ttu-id="fd2eb-125">跨資料庫參考和查詢、SQL CLR、複寫、變更資料捕獲 (CDC) 和 Service Broker</span><span class="sxs-lookup"><span data-stu-id="fd2eb-125">Cross-database references and queries, SQL CLR, replication, change data capture (CDC), and Service Broker</span></span>

- <span data-ttu-id="fd2eb-126">資料庫大小上限為 35 TB</span><span class="sxs-lookup"><span data-stu-id="fd2eb-126">Database sizes up to 35 TB</span></span>

- <span data-ttu-id="fd2eb-127">最小停機時間遷移, 具備下列功能:</span><span class="sxs-lookup"><span data-stu-id="fd2eb-127">Minimum-downtime migration, with these features:</span></span>

  - <span data-ttu-id="fd2eb-128">Azure 資料庫移轉服務</span><span class="sxs-lookup"><span data-stu-id="fd2eb-128">Azure Database Migration Service</span></span>

  - <span data-ttu-id="fd2eb-129">原生備份和還原, 以及記錄傳送</span><span class="sxs-lookup"><span data-stu-id="fd2eb-129">Native backup and restore, and log shipping</span></span>

<span data-ttu-id="fd2eb-130">有了這些功能, 當您將現有的應用程式資料庫移轉至 Azure SQL Database 時, 受控執行個體模型可為 SQL Server 的 PaaS 提供將近 100% 的優勢。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-130">With these capabilities, when you migrate existing application databases to Azure SQL Database, the Managed Instance model offers nearly 100% of the benefits of PaaS for SQL Server.</span></span> <span data-ttu-id="fd2eb-131">受控執行個體是一個 SQL Server 的環境, 您可以繼續使用實例層級的功能, 而不需要變更應用程式設計。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-131">Managed Instance is a SQL Server environment where you continue using instance-level capabilities without changing your application design.</span></span>

<span data-ttu-id="fd2eb-132">受控執行個體可能最適合目前使用 SQL Server 的企業, 而且需要在雲端的網路安全性中提供彈性。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-132">Managed Instance is probably the best fit for enterprises that currently are using SQL Server, and which require flexibility in their network security in the cloud.</span></span> <span data-ttu-id="fd2eb-133">就像是為您的 SQL 資料庫提供私人虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-133">It's like having a private virtual network for your SQL databases.</span></span>

## <a name="when-to-migrate-to-azure-sql-database"></a><span data-ttu-id="fd2eb-134">遷移至 Azure SQL Database 的時機</span><span class="sxs-lookup"><span data-stu-id="fd2eb-134">When to migrate to Azure SQL Database</span></span>

<span data-ttu-id="fd2eb-135">如前所述, 標準 Azure SQL Database 是完全受控的關聯式 DBaaS。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-135">As mentioned, the standard Azure SQL Database is a fully managed, relational DBaaS.</span></span> <span data-ttu-id="fd2eb-136">SQL Database 目前管理數百萬個生產資料庫, 跨38個資料中心, 在全球各地。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-136">SQL Database currently manages millions of production databases, across 38 datacenters, around the world.</span></span> <span data-ttu-id="fd2eb-137">它支援廣泛的應用程式和工作負載, 從管理直接的交易資料, 到驅動最需要大量資料的任務關鍵性應用程式, 以全球規模進行先進的資料處理。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-137">It supports a broad range of applications and workloads, from managing straightforward transactional data, to driving the most data-intensive, mission-critical applications that require advanced data processing at a global scale.</span></span>

<span data-ttu-id="fd2eb-138">因為它是完整的 PaaS 功能, 所以價格較佳, 而且最終成本較低-如果您的應用程式使用基本、標準 SQL 資料庫, 而且沒有其他實例功能, 您應該移至標準 Azure SQL Database 做為您的「預設選擇」。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-138">Because of its full PaaS features, better pricing-and ultimately lower cost-you should move to the standard Azure SQL Database as your "by-default choice" if you have an application that uses basic, standard SQL databases, and no additional instance features.</span></span> <span data-ttu-id="fd2eb-139">標準 Azure SQL Database 中不支援 SQL CLR 整合、SQL Server Agent 和跨資料庫查詢之類的 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-139">SQL Server features like SQL CLR integration, SQL Server Agent, and cross-database querying are not supported in the standard Azure SQL Database.</span></span> <span data-ttu-id="fd2eb-140">這些功能僅適用于 Azure SQL Database 受控執行個體模型。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-140">Those features are available only in the Azure SQL Database Managed Instance model.</span></span>

<span data-ttu-id="fd2eb-141">Azure SQL Database 是專為應用程式開發人員打造的唯一智慧型雲端資料庫服務。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-141">Azure SQL Database is the only intelligent cloud database service that's built for app developers.</span></span> <span data-ttu-id="fd2eb-142">這也是唯一可即時調整而不會停機的雲端資料庫服務, 以協助您有效率地傳遞多組織使用者共用應用程式。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-142">It's also the only cloud database service that scales on-the-fly, without downtime, to help you efficiently deliver multitenant apps.</span></span> <span data-ttu-id="fd2eb-143">最後, Azure SQL Database 會讓您更多時間進行創新, 並加速您的上市時間。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-143">Ultimately, Azure SQL Database leaves you more time to innovate, and it accelerates your time to market.</span></span> <span data-ttu-id="fd2eb-144">您可以使用您偏好的語言和平臺, 建立安全的應用程式, 並連接到您的 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-144">You can build secure apps and connect to your SQL database by using the languages and platforms that you prefer.</span></span>

<span data-ttu-id="fd2eb-145">Azure SQL Database 提供下列優點:</span><span class="sxs-lookup"><span data-stu-id="fd2eb-145">Azure SQL Database offers the following benefits:</span></span>

- <span data-ttu-id="fd2eb-146">可學習並適應您應用程式的內建智慧 (機器學習)</span><span class="sxs-lookup"><span data-stu-id="fd2eb-146">Built-in intelligence (machine learning) that learns and adapts to your app</span></span>

- <span data-ttu-id="fd2eb-147">視需要提供的資料庫布建</span><span class="sxs-lookup"><span data-stu-id="fd2eb-147">On-demand database provisioning</span></span>

- <span data-ttu-id="fd2eb-148">適用于所有工作負載的優惠範圍</span><span class="sxs-lookup"><span data-stu-id="fd2eb-148">A range of offers, for all workloads</span></span>

- <span data-ttu-id="fd2eb-149">99.99% 可用性 SLA, 零維護</span><span class="sxs-lookup"><span data-stu-id="fd2eb-149">99.99% availability SLA, zero maintenance</span></span>

- <span data-ttu-id="fd2eb-150">適用于資料保護的異地複寫與還原服務</span><span class="sxs-lookup"><span data-stu-id="fd2eb-150">Geo-replication and restore services for data protection</span></span>

- <span data-ttu-id="fd2eb-151">Azure SQL Database 時間點還原功能</span><span class="sxs-lookup"><span data-stu-id="fd2eb-151">Azure SQL Database Point in Time Restore feature</span></span>

- <span data-ttu-id="fd2eb-152">與 SQL Server 2016 的相容性, 包括混合式和遷移</span><span class="sxs-lookup"><span data-stu-id="fd2eb-152">Compatibility with SQL Server 2016, including hybrid and migration</span></span>

<span data-ttu-id="fd2eb-153">標準 Azure SQL Database 比 Azure SQL Database 受控執行個體更接近 PaaS。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-153">The standard Azure SQL Database is closer to PaaS than Azure SQL Database Managed Instance.</span></span> <span data-ttu-id="fd2eb-154">偏好使用標準 Azure SQL Database, 因為您會從受控雲端獲得更多好處。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-154">Prefer the standard Azure SQL Database because you'll get more benefits from a managed cloud.</span></span> <span data-ttu-id="fd2eb-155">不過, Azure SQL Database 與一般和內部部署 SQL Server 實例有一些主要差異。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-155">However, Azure SQL Database has some key differences from regular and on-premises SQL Server instances.</span></span> <span data-ttu-id="fd2eb-156">根據您現有應用程式的資料庫需求, 以及您的企業需求和原則, 當您打算遷移至雲端時, 這可能不是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-156">Depending on your existing application's database requirements, and your enterprise requirements and policies, it might not be the best choice when you are planning your migration to the cloud.</span></span>

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a><span data-ttu-id="fd2eb-157">將原始 RDBMS 移至 VM (IaaS) 的時機</span><span class="sxs-lookup"><span data-stu-id="fd2eb-157">When to move your original RDBMS to a VM (IaaS)</span></span>

<span data-ttu-id="fd2eb-158">其中一個遷移選項是將您的原始關係資料庫管理系統 (RDBMS) (包括 Oracle、IBM DB2、MySQL、于 postgresql 或 SQL Server) 移至在 Azure VM 上執行的類似伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-158">One of your migration options is to move your original relational database management system (RDBMS), including Oracle, IBM DB2, MySQL, PostgreSQL, or SQL Server, to a similar server that's running on an Azure VM.</span></span> <span data-ttu-id="fd2eb-159">如果您現有的應用程式需要最少的變更, 最快速的雲端遷移, 或根本沒有變更, 則直接遷移至雲端中的 IaaS 可能是合理的選擇。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-159">If you have existing applications that require the fastest migration to the cloud with minimal changes, or no changes at all, a direct migration to IaaS in the cloud might be a fair option.</span></span> <span data-ttu-id="fd2eb-160">這可能不是利用所有雲端優勢的最佳方式, 但可能是最快的初始路徑。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-160">It might not be the best way to take advantage of all the cloud's benefits, but it's probably the fastest initial path.</span></span>

<span data-ttu-id="fd2eb-161">目前, Microsoft Azure 支援最多331個部署為 IaaS Vm 的[不同資料庫伺服器](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all)。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-161">Currently, Microsoft Azure supports up to [331 different database servers](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) deployed as IaaS VMs.</span></span> <span data-ttu-id="fd2eb-162">這些包括熱門的 RDBMS, 例如 SQL Server、Oracle、MySQL、于 postgresql 和 IBM DB2, 以及其他許多 NoSQL 資料庫, 例如 MongoDB、Cassandra、DataStax、適用于 mariadb 和 Cloudera。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-162">These include popular RDBMS like SQL Server, Oracle, MySQL, PostgreSQL, and IBM DB2, and many other NoSQL databases like MongoDB, Cassandra, DataStax, MariaDB, and Cloudera.</span></span>

> [!NOTE]
> <span data-ttu-id="fd2eb-163">雖然將您的 RDBMS 移至 Azure VM 可能是將資料移轉至雲端的最快方式 (因為它是 IaaS), 但這種方法需要在您的 IT 小組 (資料庫管理員和 IT 專業人員) 中進行大量投資。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-163">Although moving your RDBMS to an Azure VM might be the fastest way to migrate your data to the cloud (because it is IaaS), this approach requires a significant investment in your IT teams (database administrators and IT pros).</span></span> <span data-ttu-id="fd2eb-164">企業小組必須能夠設定和管理 SQL Server 的高可用性、嚴重損壞修復和修補。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-164">Enterprise teams need to be able to set up and manage high availability, disaster recovery, and patching for SQL Server.</span></span> <span data-ttu-id="fd2eb-165">此內容也需要具有完整系統管理許可權的自訂環境。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-165">This context also needs a customized environment, with full administrative rights.</span></span>

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a><span data-ttu-id="fd2eb-166">何時以 VM (IaaS) 的形式遷移至 SQL Server</span><span class="sxs-lookup"><span data-stu-id="fd2eb-166">When to migrate to SQL Server as a VM (IaaS)</span></span>

<span data-ttu-id="fd2eb-167">在一些情況下, 您仍然需要以一般 VM 的方式遷移至 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-167">There might be a few cases where you still need to migrate to SQL Server as a regular VM.</span></span> <span data-ttu-id="fd2eb-168">例如, 如果您需要使用 SQL Server Reporting Services, 就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-168">An example scenario is if you need to use SQL Server Reporting Services.</span></span> <span data-ttu-id="fd2eb-169">不過, 在大多數情況下, Azure SQL Database 受控執行個體可以提供從內部部署 SQL 伺服器進行遷移所需的所有專案, 因此您必須先嘗試遷移至 SQL Server VM。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-169">In most cases, though, Azure SQL Database Managed Instance can provide everything you need to migrate from on-premises SQL servers, so migration to a SQL Server VM should be your last resort to try.</span></span>

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a><span data-ttu-id="fd2eb-170">使用 Azure 資料庫移轉服務, 將您的關係資料庫移轉至 Azure</span><span class="sxs-lookup"><span data-stu-id="fd2eb-170">Use Azure Database Migration Service to migrate your relational databases to Azure</span></span> 

<span data-ttu-id="fd2eb-171">您可以使用 Azure 資料庫移轉服務, 將 SQL Server、Oracle 和 MySQL 之類的關係資料庫移轉至 Azure, 不論您的目標資料庫是在 Azure VM 上 Azure SQL Database、Azure SQL Database 受控執行個體或 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-171">You can use Azure Database Migration Service to migrate relational databases like SQL Server, Oracle, and MySQL to Azure, whether your target database is Azure SQL Database, Azure SQL Database Managed Instance, or SQL Server on an Azure VM.</span></span>

<span data-ttu-id="fd2eb-172">自動化的工作流程和評量報告, 會引導您完成在遷移資料庫之前所需進行的變更。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-172">The automated workflow, with assessment reporting, guides you through the changes you need to make before you migrate the database.</span></span> <span data-ttu-id="fd2eb-173">當您準備好時, 服務會將源資料庫移轉至 Azure。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-173">When you are ready, the service migrates the source database to Azure.</span></span>

<span data-ttu-id="fd2eb-174">每當您變更原始 RDBMS 時, 可能需要重新測試。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-174">Whenever you change an original RDBMS, you might need to retest.</span></span> <span data-ttu-id="fd2eb-175">視測試結果而定, 您也可能需要變更應用程式中的 SQL 句子或物件關聯式對應 (ORM) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-175">You also might need to change the SQL sentences or Object-Relational Mapping (ORM) code in your application, depending on testing results.</span></span>

<span data-ttu-id="fd2eb-176">如果您有任何其他資料庫 (例如, IBM DB2), 而您選擇了隨即轉移方法, 您可能會想要在 Azure 中繼續使用這些資料庫做為 IaaS Vm, 除非您願意執行更複雜的資料移轉。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-176">If you have any other database (for example, IBM DB2) and you opt for a lift and shift approach, you might want to continue using those databases as IaaS VMs in Azure, unless you are willing to perform a more complex data migration.</span></span> <span data-ttu-id="fd2eb-177">較複雜的資料移轉需要額外的工作, 因為您會使用新的架構和不同的程式設計程式庫來遷移至不同的資料庫類型。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-177">A more complex data migration will require additional effort because you'd be migrating to a different database type with new schema and different programming libraries.</span></span>

<span data-ttu-id="fd2eb-178">若要瞭解如何使用 Azure 資料庫移轉服務來遷移資料庫, 請參閱[使用 Azure SQL Database 受控執行個體和 Azure 資料庫移轉服務更快取得雲端](https://channel9.msdn.com/Events/Build/2017/P4008)。</span><span class="sxs-lookup"><span data-stu-id="fd2eb-178">To learn how to migrate databases by using Azure Database Migration Service, see [Get to the cloud faster with Azure SQL Database Managed Instance and Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fd2eb-179">其他資源</span><span class="sxs-lookup"><span data-stu-id="fd2eb-179">Additional resources</span></span>

- <span data-ttu-id="fd2eb-180">**選擇雲端 SQL Server 選項:在 Azure VM (IaaS) 上 Azure SQL Database (PaaS) 或 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fd2eb-180">**Choose a cloud SQL Server option: Azure SQL Database (PaaS) or SQL Server on Azure VM (IaaS)**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- <span data-ttu-id="fd2eb-181">**使用 Azure SQL DB 受控執行個體和資料庫移轉服務, 更快取得雲端**</span><span class="sxs-lookup"><span data-stu-id="fd2eb-181">**Get to the cloud faster with Azure SQL DB Managed Instance and Database Migration Service**</span></span>

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- <span data-ttu-id="fd2eb-182">**SQL Server 資料庫移轉至雲端 SQL Database**</span><span class="sxs-lookup"><span data-stu-id="fd2eb-182">**SQL Server database migration to SQL Database in the cloud**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- <span data-ttu-id="fd2eb-183">**Azure SQL Database**</span><span class="sxs-lookup"><span data-stu-id="fd2eb-183">**Azure SQL Database**</span></span>

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- <span data-ttu-id="fd2eb-184">**虛擬機器上的 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fd2eb-184">**SQL Server on virtual machines**</span></span>

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> <span data-ttu-id="fd2eb-185">[上一頁](lift-and-shift-existing-apps-azure-iaas.md)
> [下一頁](modernize-existing-apps-to-cloud-optimized/index.md)</span><span class="sxs-lookup"><span data-stu-id="fd2eb-185">[Previous](lift-and-shift-existing-apps-azure-iaas.md)
[Next](modernize-existing-apps-to-cloud-optimized/index.md)</span></span> <!-- Next Chapter -->
