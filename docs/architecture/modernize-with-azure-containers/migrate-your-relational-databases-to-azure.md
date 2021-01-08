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
# <a name="migrate-your-relational-databases-to-azure"></a><span data-ttu-id="ca46b-103">將關聯式資料庫移轉至 Azure</span><span class="sxs-lookup"><span data-stu-id="ca46b-103">Migrate your relational databases to Azure</span></span>

<span data-ttu-id="ca46b-104">願景： Azure 提供最全面的資料庫移轉。</span><span class="sxs-lookup"><span data-stu-id="ca46b-104">Vision: Azure offers the most comprehensive database migration.</span></span>

<span data-ttu-id="ca46b-105">在 Azure 中，您可以將資料庫伺服器直接遷移至 IaaS Vm (單純的隨即轉移) ，也可以遷移至 Azure SQL Database，以獲得更多優點。</span><span class="sxs-lookup"><span data-stu-id="ca46b-105">In Azure, you can migrate your database servers directly to IaaS VMs (pure lift and shift), or you can migrate to Azure SQL Database, for additional benefits.</span></span> <span data-ttu-id="ca46b-106">Azure SQL Database 提供受控實例和完整的資料庫即服務 (DBaaS) 選項。</span><span class="sxs-lookup"><span data-stu-id="ca46b-106">Azure SQL Database offers the managed instance and full database-as-a-service (DBaaS) options.</span></span> <span data-ttu-id="ca46b-107">圖3-1 顯示 Azure 中可使用的多個關係資料庫移轉路徑。</span><span class="sxs-lookup"><span data-stu-id="ca46b-107">Figure 3-1 shows the multiple relational database migration paths available in Azure.</span></span>

![Azure 中的資料庫移轉路徑](./media/image3-1.png)

<span data-ttu-id="ca46b-109">**圖3-1。**</span><span class="sxs-lookup"><span data-stu-id="ca46b-109">**Figure 3-1.**</span></span> <span data-ttu-id="ca46b-110">Azure 中的資料庫移轉路徑</span><span class="sxs-lookup"><span data-stu-id="ca46b-110">Database migration paths in Azure</span></span>

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a><span data-ttu-id="ca46b-111">遷移至 Azure SQL Database 受控執行個體的時機</span><span class="sxs-lookup"><span data-stu-id="ca46b-111">When to migrate to Azure SQL Database Managed Instance</span></span>

<span data-ttu-id="ca46b-112">在大多數情況下，當您將資料移轉至 Azure 時，Azure SQL Database 受控執行個體將是您最好考慮的選項。</span><span class="sxs-lookup"><span data-stu-id="ca46b-112">In most cases, Azure SQL Database Managed Instance will be your best option to consider when you migrate your data to Azure.</span></span> <span data-ttu-id="ca46b-113">如果您要遷移 SQL Server 的資料庫，而且需要將近100% 的保證，您不需要重新架構應用程式，也不需要變更您的資料或資料存取程式碼，請選擇 Azure SQL Database 的受控執行個體功能。</span><span class="sxs-lookup"><span data-stu-id="ca46b-113">If you are migrating SQL Server databases and need nearly 100% assurance that you won't need to rearchitect your application or make changes to your data or data access code, choose the Managed Instance feature of Azure SQL Database.</span></span>

<span data-ttu-id="ca46b-114">如果您有 SQL Server 實例層級功能的額外需求，或是除了標準 Azure SQL Database (單一資料庫模型) 中提供的功能以外的隔離需求，Azure SQL Database 受控執行個體是最佳選項。</span><span class="sxs-lookup"><span data-stu-id="ca46b-114">Azure SQL Database Managed Instance is the best option if you have additional requirements for SQL Server instance-level functionality, or isolation requirements beyond the features provided in a standard Azure SQL Database (single database model).</span></span> <span data-ttu-id="ca46b-115">最後一個是最適合 PaaS 導向的選擇，但它並不提供與傳統 SQL server 相同的功能。</span><span class="sxs-lookup"><span data-stu-id="ca46b-115">This last one is the most PaaS-oriented choice, but it doesn't offer the same features as that of a traditional SQL server.</span></span> <span data-ttu-id="ca46b-116">遷移可能會呈現摩擦。</span><span class="sxs-lookup"><span data-stu-id="ca46b-116">Migration might surface frictions.</span></span>

<span data-ttu-id="ca46b-117">例如，在實例層級 SQL Server 功能中進行深度投資的組織，將可受益于遷移至 SQL 受控執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca46b-117">For example, an organization that has made deep investments in instance-level SQL Server capabilities would benefit from migrating to SQL Managed Instance.</span></span> <span data-ttu-id="ca46b-118">實例層級 SQL Server 功能的範例包括 SQL common language runtime (CLR) 整合、SQL Server Agent 和跨資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="ca46b-118">Examples of instance-level SQL Server capabilities include SQL common language runtime (CLR) integration, SQL Server Agent, and cross-database querying.</span></span> <span data-ttu-id="ca46b-119">標準 Azure SQL Database 不提供這些功能的支援 (單一資料庫模型) 。</span><span class="sxs-lookup"><span data-stu-id="ca46b-119">Support for these features is not available in standard Azure SQL Database (a single-database model).</span></span>

<span data-ttu-id="ca46b-120">在高度管制的產業中運作，而且基於安全性目的而需要維護隔離的組織，也可能會因為選擇 SQL 受控執行個體模型而有所説明。</span><span class="sxs-lookup"><span data-stu-id="ca46b-120">An organization that operates in a highly regulated industry, and which needs to maintain isolation for security purposes, also might benefit from choosing the SQL Managed Instance model.</span></span>

<span data-ttu-id="ca46b-121">Azure SQL Database 中的受控執行個體具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="ca46b-121">Managed Instance in Azure SQL Database has the following characteristics:</span></span>

- <span data-ttu-id="ca46b-122">透過 Azure 虛擬網路的安全性隔離</span><span class="sxs-lookup"><span data-stu-id="ca46b-122">Security isolation through Azure Virtual Network</span></span>

- <span data-ttu-id="ca46b-123">使用這些功能的應用程式介面相容性：</span><span class="sxs-lookup"><span data-stu-id="ca46b-123">Application surface compatibility, with these features:</span></span>

  - <span data-ttu-id="ca46b-124">SQL Server Agent 和 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ca46b-124">SQL Server Agent and SQL Server Profiler</span></span>

  - <span data-ttu-id="ca46b-125">跨資料庫參考和查詢、SQL CLR、複寫、變更資料捕獲 (CDC) 和 Service Broker</span><span class="sxs-lookup"><span data-stu-id="ca46b-125">Cross-database references and queries, SQL CLR, replication, change data capture (CDC), and Service Broker</span></span>

- <span data-ttu-id="ca46b-126">最高達 35 TB 的資料庫大小</span><span class="sxs-lookup"><span data-stu-id="ca46b-126">Database sizes up to 35 TB</span></span>

- <span data-ttu-id="ca46b-127">使用下列功能的最少停機時間遷移：</span><span class="sxs-lookup"><span data-stu-id="ca46b-127">Minimum-downtime migration, with these features:</span></span>

  - <span data-ttu-id="ca46b-128">Azure 資料庫移轉服務</span><span class="sxs-lookup"><span data-stu-id="ca46b-128">Azure Database Migration Service</span></span>

  - <span data-ttu-id="ca46b-129">原生備份和還原，以及記錄傳送</span><span class="sxs-lookup"><span data-stu-id="ca46b-129">Native backup and restore, and log shipping</span></span>

<span data-ttu-id="ca46b-130">使用這些功能時，當您將現有的應用程式資料庫移轉至 Azure SQL Database 時，受控執行個體模型可提供 PaaS for SQL Server 的將近100% 優點。</span><span class="sxs-lookup"><span data-stu-id="ca46b-130">With these capabilities, when you migrate existing application databases to Azure SQL Database, the Managed Instance model offers nearly 100% of the benefits of PaaS for SQL Server.</span></span> <span data-ttu-id="ca46b-131">受控執行個體是一種 SQL Server 的環境，可讓您繼續使用實例層級的功能，而不需要變更應用程式設計。</span><span class="sxs-lookup"><span data-stu-id="ca46b-131">Managed Instance is a SQL Server environment where you continue using instance-level capabilities without changing your application design.</span></span>

<span data-ttu-id="ca46b-132">受控執行個體可能最適合目前使用 SQL Server 的企業，且需要在雲端的網路安全性方面提供彈性。</span><span class="sxs-lookup"><span data-stu-id="ca46b-132">Managed Instance is probably the best fit for enterprises that currently are using SQL Server, and which require flexibility in their network security in the cloud.</span></span> <span data-ttu-id="ca46b-133">它就像是 SQL 資料庫的私人虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ca46b-133">It's like having a private virtual network for your SQL databases.</span></span>

## <a name="when-to-migrate-to-azure-sql-database"></a><span data-ttu-id="ca46b-134">遷移至 Azure SQL Database 的時機</span><span class="sxs-lookup"><span data-stu-id="ca46b-134">When to migrate to Azure SQL Database</span></span>

<span data-ttu-id="ca46b-135">如前所述，標準 Azure SQL Database 是完全受控的關聯式 DBaaS。</span><span class="sxs-lookup"><span data-stu-id="ca46b-135">As mentioned, the standard Azure SQL Database is a fully managed, relational DBaaS.</span></span> <span data-ttu-id="ca46b-136">SQL Database 目前在全球各地的38資料中心管理數百萬個生產資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca46b-136">SQL Database currently manages millions of production databases, across 38 datacenters, around the world.</span></span> <span data-ttu-id="ca46b-137">它支援各種不同的應用程式和工作負載，從管理簡單的交易資料，到需要以全球規模進行先進資料處理的最大量資料、任務關鍵性應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca46b-137">It supports a broad range of applications and workloads, from managing straightforward transactional data, to driving the most data-intensive, mission-critical applications that require advanced data processing at a global scale.</span></span>

<span data-ttu-id="ca46b-138">由於其完整的 PaaS 功能、更好的定價和最終成本較低，因此，如果您的應用程式使用基本、標準 SQL 資料庫，而且沒有其他實例功能，則您應該移至標準 Azure SQL Database 作為「預設選擇」。</span><span class="sxs-lookup"><span data-stu-id="ca46b-138">Because of its full PaaS features, better pricing-and ultimately lower cost-you should move to the standard Azure SQL Database as your "by-default choice" if you have an application that uses basic, standard SQL databases, and no additional instance features.</span></span> <span data-ttu-id="ca46b-139">標準 Azure SQL Database 不支援 SQL CLR 整合、SQL Server Agent 和跨資料庫查詢等 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="ca46b-139">SQL Server features like SQL CLR integration, SQL Server Agent, and cross-database querying are not supported in the standard Azure SQL Database.</span></span> <span data-ttu-id="ca46b-140">這些功能僅適用于 Azure SQL Database 受控執行個體模型。</span><span class="sxs-lookup"><span data-stu-id="ca46b-140">Those features are available only in the Azure SQL Database Managed Instance model.</span></span>

<span data-ttu-id="ca46b-141">Azure SQL Database 是專為應用程式開發人員打造的智慧型雲端資料庫服務。</span><span class="sxs-lookup"><span data-stu-id="ca46b-141">Azure SQL Database is the only intelligent cloud database service that's built for app developers.</span></span> <span data-ttu-id="ca46b-142">這也是唯一可即時調整而不需要停機的雲端資料庫服務，可協助您有效率地提供多組織使用者共用應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca46b-142">It's also the only cloud database service that scales on-the-fly, without downtime, to help you efficiently deliver multitenant apps.</span></span> <span data-ttu-id="ca46b-143">最後，Azure SQL Database 可讓您更輕鬆地進行創新，而且可加速您的上市時間。</span><span class="sxs-lookup"><span data-stu-id="ca46b-143">Ultimately, Azure SQL Database leaves you more time to innovate, and it accelerates your time to market.</span></span> <span data-ttu-id="ca46b-144">您可以使用您偏好的語言和平臺來建立安全的應用程式，並連接到您的 SQL database。</span><span class="sxs-lookup"><span data-stu-id="ca46b-144">You can build secure apps and connect to your SQL database by using the languages and platforms that you prefer.</span></span>

<span data-ttu-id="ca46b-145">Azure SQL Database 提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="ca46b-145">Azure SQL Database offers the following benefits:</span></span>

- <span data-ttu-id="ca46b-146">內建智慧 (機器學習) ，可學習和適應您的應用程式</span><span class="sxs-lookup"><span data-stu-id="ca46b-146">Built-in intelligence (machine learning) that learns and adapts to your app</span></span>

- <span data-ttu-id="ca46b-147">依需求提供的資料庫布建</span><span class="sxs-lookup"><span data-stu-id="ca46b-147">On-demand database provisioning</span></span>

- <span data-ttu-id="ca46b-148">適用于所有工作負載的優惠範圍</span><span class="sxs-lookup"><span data-stu-id="ca46b-148">A range of offers, for all workloads</span></span>

- <span data-ttu-id="ca46b-149">99.99% 可用性 SLA，零維護</span><span class="sxs-lookup"><span data-stu-id="ca46b-149">99.99% availability SLA, zero maintenance</span></span>

- <span data-ttu-id="ca46b-150">適用于資料保護的異地複寫和還原服務</span><span class="sxs-lookup"><span data-stu-id="ca46b-150">Geo-replication and restore services for data protection</span></span>

- <span data-ttu-id="ca46b-151">Azure SQL Database 時間點還原功能</span><span class="sxs-lookup"><span data-stu-id="ca46b-151">Azure SQL Database Point in Time Restore feature</span></span>

- <span data-ttu-id="ca46b-152">與 SQL Server 2016 （包括混合式和遷移）的相容性</span><span class="sxs-lookup"><span data-stu-id="ca46b-152">Compatibility with SQL Server 2016, including hybrid and migration</span></span>

<span data-ttu-id="ca46b-153">標準 Azure SQL Database 比 Azure SQL Database 受控執行個體更接近 PaaS。</span><span class="sxs-lookup"><span data-stu-id="ca46b-153">The standard Azure SQL Database is closer to PaaS than Azure SQL Database Managed Instance.</span></span> <span data-ttu-id="ca46b-154">偏好使用標準 Azure SQL Database，因為您會從受控雲端獲得更多的權益。</span><span class="sxs-lookup"><span data-stu-id="ca46b-154">Prefer the standard Azure SQL Database because you'll get more benefits from a managed cloud.</span></span> <span data-ttu-id="ca46b-155">不過，Azure SQL Database 與一般和內部部署 SQL Server 實例之間有一些重要的差異。</span><span class="sxs-lookup"><span data-stu-id="ca46b-155">However, Azure SQL Database has some key differences from regular and on-premises SQL Server instances.</span></span> <span data-ttu-id="ca46b-156">根據您現有應用程式的資料庫需求，以及您的企業需求和原則，當您計畫遷移至雲端時，這可能不是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="ca46b-156">Depending on your existing application's database requirements, and your enterprise requirements and policies, it might not be the best choice when you are planning your migration to the cloud.</span></span>

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a><span data-ttu-id="ca46b-157">將原始 RDBMS 移至 VM (IaaS) </span><span class="sxs-lookup"><span data-stu-id="ca46b-157">When to move your original RDBMS to a VM (IaaS)</span></span>

<span data-ttu-id="ca46b-158">其中一個遷移選項是將您的原始關係資料庫管理)  (系統（包括 Oracle、IBM DB2、MySQL、于 postgresql 或 SQL Server）移至在 Azure VM 上執行的類似伺服器。</span><span class="sxs-lookup"><span data-stu-id="ca46b-158">One of your migration options is to move your original relational database management system (RDBMS), including Oracle, IBM DB2, MySQL, PostgreSQL, or SQL Server, to a similar server that's running on an Azure VM.</span></span> <span data-ttu-id="ca46b-159">如果您的現有應用程式需要最快速地遷移至雲端，但變更最短，或完全沒有變更，則直接遷移至雲端中的 IaaS 可能是合理的選擇。</span><span class="sxs-lookup"><span data-stu-id="ca46b-159">If you have existing applications that require the fastest migration to the cloud with minimal changes, or no changes at all, a direct migration to IaaS in the cloud might be a fair option.</span></span> <span data-ttu-id="ca46b-160">這可能不是充分利用雲端優勢的最佳方式，但可能是最快的初始路徑。</span><span class="sxs-lookup"><span data-stu-id="ca46b-160">It might not be the best way to take advantage of all the cloud's benefits, but it's probably the fastest initial path.</span></span>

<span data-ttu-id="ca46b-161">目前，Microsoft Azure 支援最多331個部署為 IaaS Vm 的 [不同資料庫伺服器](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) 。</span><span class="sxs-lookup"><span data-stu-id="ca46b-161">Currently, Microsoft Azure supports up to [331 different database servers](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) deployed as IaaS VMs.</span></span> <span data-ttu-id="ca46b-162">這些包括熱門的 RDBMS，例如 SQL Server、Oracle、MySQL、于 postgresql 和 IBM DB2，以及其他許多 NoSQL 資料庫（例如 MongoDB、Cassandra、DataStax、適用于 mariadb 和 Cloudera）。</span><span class="sxs-lookup"><span data-stu-id="ca46b-162">These include popular RDBMS like SQL Server, Oracle, MySQL, PostgreSQL, and IBM DB2, and many other NoSQL databases like MongoDB, Cassandra, DataStax, MariaDB, and Cloudera.</span></span>

> [!NOTE]
> <span data-ttu-id="ca46b-163">雖然將 RDBMS 移至 Azure VM 可能是將資料移轉至雲端的最快方法 (因為它是 IaaS) ，所以這種方法需要在您的 IT 小組 (資料庫管理員和 IT 專業人員) 進行大量投資。</span><span class="sxs-lookup"><span data-stu-id="ca46b-163">Although moving your RDBMS to an Azure VM might be the fastest way to migrate your data to the cloud (because it is IaaS), this approach requires a significant investment in your IT teams (database administrators and IT pros).</span></span> <span data-ttu-id="ca46b-164">企業小組必須能夠設定和管理 SQL Server 的高可用性、嚴重損壞修復和修補。</span><span class="sxs-lookup"><span data-stu-id="ca46b-164">Enterprise teams need to be able to set up and manage high availability, disaster recovery, and patching for SQL Server.</span></span> <span data-ttu-id="ca46b-165">此內容也需要具有完整系統管理許可權的自訂環境。</span><span class="sxs-lookup"><span data-stu-id="ca46b-165">This context also needs a customized environment, with full administrative rights.</span></span>

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a><span data-ttu-id="ca46b-166">遷移至 SQL Server 作為 VM (IaaS) </span><span class="sxs-lookup"><span data-stu-id="ca46b-166">When to migrate to SQL Server as a VM (IaaS)</span></span>

<span data-ttu-id="ca46b-167">在一些情況下，您仍然需要以一般 VM 的形式遷移至 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ca46b-167">There might be a few cases where you still need to migrate to SQL Server as a regular VM.</span></span> <span data-ttu-id="ca46b-168">如果您需要使用 SQL Server Reporting Services，則為範例案例。</span><span class="sxs-lookup"><span data-stu-id="ca46b-168">An example scenario is if you need to use SQL Server Reporting Services.</span></span> <span data-ttu-id="ca46b-169">不過，在大部分情況下，Azure SQL Database 受控執行個體可以提供從內部部署 SQL server 遷移所需的所有專案，因此您必須先嘗試進行遷移至 SQL Server VM。</span><span class="sxs-lookup"><span data-stu-id="ca46b-169">In most cases, though, Azure SQL Database Managed Instance can provide everything you need to migrate from on-premises SQL servers, so migration to a SQL Server VM should be your last resort to try.</span></span>

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a><span data-ttu-id="ca46b-170">使用 Azure 資料庫移轉服務將您的關係資料庫移轉至 Azure</span><span class="sxs-lookup"><span data-stu-id="ca46b-170">Use Azure Database Migration Service to migrate your relational databases to Azure</span></span>

<span data-ttu-id="ca46b-171">您可以使用 Azure 資料庫移轉服務，將 SQL Server、Oracle 和 MySQL 等關係資料庫移轉至 Azure，無論您的目標資料庫是在 Azure VM 上 Azure SQL Database、Azure SQL Database 受控執行個體或 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ca46b-171">You can use Azure Database Migration Service to migrate relational databases like SQL Server, Oracle, and MySQL to Azure, whether your target database is Azure SQL Database, Azure SQL Database Managed Instance, or SQL Server on an Azure VM.</span></span>

<span data-ttu-id="ca46b-172">自動化工作流程（含評量報告）會引導您完成在遷移資料庫之前所需進行的變更。</span><span class="sxs-lookup"><span data-stu-id="ca46b-172">The automated workflow, with assessment reporting, guides you through the changes you need to make before you migrate the database.</span></span> <span data-ttu-id="ca46b-173">當您準備好時，服務會將源資料庫移轉至 Azure。</span><span class="sxs-lookup"><span data-stu-id="ca46b-173">When you are ready, the service migrates the source database to Azure.</span></span>

<span data-ttu-id="ca46b-174">每當您變更原始 RDBMS 時，可能需要重新測試。</span><span class="sxs-lookup"><span data-stu-id="ca46b-174">Whenever you change an original RDBMS, you might need to retest.</span></span> <span data-ttu-id="ca46b-175">您也可能需要根據測試結果，在您的應用程式中變更 SQL 句子或 Object-Relational 對應 (ORM) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ca46b-175">You also might need to change the SQL sentences or Object-Relational Mapping (ORM) code in your application, depending on testing results.</span></span>

<span data-ttu-id="ca46b-176">如果您有任何其他資料庫 (例如 IBM DB2) ，而您選擇了增益和轉移方法，除非您願意執行更複雜的資料移轉，否則您可能會想要繼續在 Azure 中使用這些資料庫作為 IaaS Vm。</span><span class="sxs-lookup"><span data-stu-id="ca46b-176">If you have any other database (for example, IBM DB2) and you opt for a lift and shift approach, you might want to continue using those databases as IaaS VMs in Azure, unless you are willing to perform a more complex data migration.</span></span> <span data-ttu-id="ca46b-177">更複雜的資料移轉將需要額外的工作，因為您要使用新的架構和不同的程式設計程式庫遷移至不同的資料庫類型。</span><span class="sxs-lookup"><span data-stu-id="ca46b-177">A more complex data migration will require additional effort because you'd be migrating to a different database type with the new schema and different programming libraries.</span></span>

<span data-ttu-id="ca46b-178">若要瞭解如何使用 Azure 資料庫移轉服務來遷移資料庫，請參閱 [Azure SQL Database 受控執行個體和 Azure 資料庫移轉服務，以更快的速度進入雲端](https://channel9.msdn.com/Events/Build/2017/P4008)。</span><span class="sxs-lookup"><span data-stu-id="ca46b-178">To learn how to migrate databases by using Azure Database Migration Service, see [Get to the cloud faster with Azure SQL Database Managed Instance and Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ca46b-179">其他資源</span><span class="sxs-lookup"><span data-stu-id="ca46b-179">Additional resources</span></span>

- <span data-ttu-id="ca46b-180">**選擇雲端 SQL Server 選項： Azure SQL Database Azure VM 上的 (PaaS) 或 SQL Server (IaaS)**</span><span class="sxs-lookup"><span data-stu-id="ca46b-180">**Choose a cloud SQL Server option: Azure SQL Database (PaaS) or SQL Server on Azure VM (IaaS)**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- <span data-ttu-id="ca46b-181">**使用 Azure SQL DB 受控執行個體和資料庫移轉服務，更快進入雲端**</span><span class="sxs-lookup"><span data-stu-id="ca46b-181">**Get to the cloud faster with Azure SQL DB Managed Instance and Database Migration Service**</span></span>

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- <span data-ttu-id="ca46b-182">**SQL Server 資料庫移轉至雲端 SQL Database**</span><span class="sxs-lookup"><span data-stu-id="ca46b-182">**SQL Server database migration to SQL Database in the cloud**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- <span data-ttu-id="ca46b-183">**Azure SQL Database**</span><span class="sxs-lookup"><span data-stu-id="ca46b-183">**Azure SQL Database**</span></span>

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- <span data-ttu-id="ca46b-184">**虛擬機器上的 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ca46b-184">**SQL Server on virtual machines**</span></span>

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> <span data-ttu-id="ca46b-185">[上一個](lift-and-shift-existing-apps-azure-iaas.md) 
> [下一步](modernize-existing-apps-to-cloud-optimized/index.md)</span><span class="sxs-lookup"><span data-stu-id="ca46b-185">[Previous](lift-and-shift-existing-apps-azure-iaas.md)
[Next](modernize-existing-apps-to-cloud-optimized/index.md)</span></span> <!-- Next Chapter -->
