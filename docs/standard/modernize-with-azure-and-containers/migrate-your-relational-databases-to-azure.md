---
title: 將關聯式資料庫移轉至 azure
description: 將現有.NET 應用程式與 Azure 雲端和 Windows 容器現代化 |將關聯式資料庫移轉至 azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 600c47b6b0ccaf704c8e7b638c759e990acaaacf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61812774"
---
# <a name="migrate-your-relational-databases-to-azure"></a><span data-ttu-id="ac686-103">將關聯式資料庫移轉至 azure</span><span class="sxs-lookup"><span data-stu-id="ac686-103">Migrate your relational databases to azure</span></span>

<span data-ttu-id="ac686-104">願景：Azure 提供最完整的資料庫移轉。</span><span class="sxs-lookup"><span data-stu-id="ac686-104">Vision: Azure offers the most comprehensive database migration.</span></span>

<span data-ttu-id="ac686-105">在 Azure 中，您可以直接到 IaaS Vm （純提升與轉變），移轉您的資料庫伺服器，或您可以移轉至 Azure SQL Database，額外的好處。</span><span class="sxs-lookup"><span data-stu-id="ac686-105">In Azure, you can migrate your database servers directly to IaaS VMs (pure lift and shift), or you can migrate to Azure SQL Database, for additional benefits.</span></span> <span data-ttu-id="ac686-106">Azure SQL Database 提供受控執行個體和完整資料庫做為-即服務 (DBaaS) 選項。</span><span class="sxs-lookup"><span data-stu-id="ac686-106">Azure SQL Database offers managed instance and full database-as-a-service (DBaaS) options.</span></span> <span data-ttu-id="ac686-107">圖 3-1 顯示多個關聯式資料庫在 Azure 中可用的移轉路徑。</span><span class="sxs-lookup"><span data-stu-id="ac686-107">Figure 3-1 shows the multiple relational database migration paths available in Azure.</span></span>

![在 Azure 中的資料庫移轉路徑](./media/image3-1.png)

> <span data-ttu-id="ac686-109">**圖 3-1**</span><span class="sxs-lookup"><span data-stu-id="ac686-109">**Figure 3-1.**</span></span> <span data-ttu-id="ac686-110">在 Azure 中的資料庫移轉路徑</span><span class="sxs-lookup"><span data-stu-id="ac686-110">Database migration paths in Azure</span></span>

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a><span data-ttu-id="ac686-111">移轉至 Azure SQL Database 受控執行個體</span><span class="sxs-lookup"><span data-stu-id="ac686-111">When to migrate to Azure SQL Database Managed Instance</span></span>

<span data-ttu-id="ac686-112">在大部分情況下，Azure SQL Database 受控執行個體將會是您最佳的選項，您將資料移轉至 Azure 時，請考慮。</span><span class="sxs-lookup"><span data-stu-id="ac686-112">In most cases, Azure SQL Database Managed Instance will be your best option to consider when you migrate your data to Azure.</span></span> <span data-ttu-id="ac686-113">如果您要移轉 SQL Server 資料庫，並需要近 100%保證，證明您不需要重新架構您的應用程式，或變更您的資料或資料存取程式碼，請選擇 Azure SQL Database 受控執行個體功能。</span><span class="sxs-lookup"><span data-stu-id="ac686-113">If you are migrating SQL Server databases and need nearly 100% assurance that you won't need to rearchitect your application or make changes to your data or data access code, choose the Managed Instance feature of Azure SQL Database.</span></span>

<span data-ttu-id="ac686-114">如果您有其他需求，如需 SQL Server 執行個體層級功能或隔離需求，提供標準的 Azure SQL Database （單一資料庫模型） 中的功能之外，azure SQL Database 受控執行個體是最佳選項。</span><span class="sxs-lookup"><span data-stu-id="ac686-114">Azure SQL Database Managed Instance is the best option if you have additional requirements for SQL Server instance-level functionality, or isolation requirements beyond the features provided in a standard Azure SQL Database (single database model).</span></span> <span data-ttu-id="ac686-115">最後一項最以 PaaS 為導向的選擇，但它不會提供與傳統的 SQL server 的相同功能。</span><span class="sxs-lookup"><span data-stu-id="ac686-115">This last one is the most PaaS-oriented choice, but it doesn't offer the same features as that of a traditional SQL server.</span></span> <span data-ttu-id="ac686-116">移轉可能會出現的摩擦。</span><span class="sxs-lookup"><span data-stu-id="ac686-116">Migration might surface frictions.</span></span>

<span data-ttu-id="ac686-117">例如，組織方面所做深入的投資執行個體層級 SQL Server 功能受益於移轉至 SQL 受控執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac686-117">For example, an organization that has made deep investments in instance-level SQL Server capabilities would benefit from migrating to SQL Managed Instance.</span></span> <span data-ttu-id="ac686-118">執行個體層級 SQL Server 功能的範例包括 SQL common language runtime (CLR) 整合，SQL Server Agent，以及跨資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="ac686-118">Examples of instance-level SQL Server capabilities include SQL common language runtime (CLR) integration, SQL Server Agent, and cross-database querying.</span></span> <span data-ttu-id="ac686-119">無法使用標準的 Azure SQL Database （單一資料庫模型） 中支援這些功能。</span><span class="sxs-lookup"><span data-stu-id="ac686-119">Support for these features is not available in standard Azure SQL Database (a single-database model).</span></span>

<span data-ttu-id="ac686-120">組織，在高管制的產業中運作，並需要維護隔離，基於安全考量，也可能會受益於選擇 SQL 受控執行個體模型。</span><span class="sxs-lookup"><span data-stu-id="ac686-120">An organization that operates in a highly regulated industry, and which needs to maintain isolation for security purposes, also might benefit from choosing the SQL Managed Instance model.</span></span>

<span data-ttu-id="ac686-121">在 Azure SQL Database 受控執行個體具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="ac686-121">Managed Instance in Azure SQL Database has the following characteristics:</span></span>

- <span data-ttu-id="ac686-122">透過 Azure 虛擬網路的安全性隔離</span><span class="sxs-lookup"><span data-stu-id="ac686-122">Security isolation through Azure Virtual Network</span></span>

- <span data-ttu-id="ac686-123">應用程式介面相容，這些功能：</span><span class="sxs-lookup"><span data-stu-id="ac686-123">Application surface compatibility, with these features:</span></span>

  - <span data-ttu-id="ac686-124">SQL Server Agent 和 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ac686-124">SQL Server Agent and SQL Server Profiler</span></span>

  - <span data-ttu-id="ac686-125">跨資料庫參考和查詢，SQL CLR、 複寫、 異動資料擷取 (CDC) 和 Service Broker</span><span class="sxs-lookup"><span data-stu-id="ac686-125">Cross-database references and queries, SQL CLR, replication, change data capture (CDC), and Service Broker</span></span>

- <span data-ttu-id="ac686-126">資料庫大小上限為 35 TB</span><span class="sxs-lookup"><span data-stu-id="ac686-126">Database sizes up to 35 TB</span></span>

- <span data-ttu-id="ac686-127">最少停機時間移轉，這些功能：</span><span class="sxs-lookup"><span data-stu-id="ac686-127">Minimum-downtime migration, with these features:</span></span>

  - <span data-ttu-id="ac686-128">Azure 資料庫移轉服務</span><span class="sxs-lookup"><span data-stu-id="ac686-128">Azure Database Migration Service</span></span>

  - <span data-ttu-id="ac686-129">原生備份及還原，記錄傳送</span><span class="sxs-lookup"><span data-stu-id="ac686-129">Native backup and restore, and log shipping</span></span>

<span data-ttu-id="ac686-130">使用這些功能，當您將現有的應用程式資料庫移轉至 Azure SQL Database 受控執行個體模型提供幾乎 100%的 PaaS 優點適用於 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ac686-130">With these capabilities, when you migrate existing application databases to Azure SQL Database, the Managed Instance model offers nearly 100% of the benefits of PaaS for SQL Server.</span></span> <span data-ttu-id="ac686-131">受控執行個體是 SQL Server 環境，您可以繼續使用執行個體層級功能，而不需要變更您的應用程式設計。</span><span class="sxs-lookup"><span data-stu-id="ac686-131">Managed Instance is a SQL Server environment where you continue using instance-level capabilities without changing your application design.</span></span>

<span data-ttu-id="ac686-132">受控執行個體可能是最好的選擇，適用於企業目前使用之 SQL Server，而且必須在其雲端中的網路安全性的彈性。</span><span class="sxs-lookup"><span data-stu-id="ac686-132">Managed Instance is probably the best fit for enterprises that currently are using SQL Server, and which require flexibility in their network security in the cloud.</span></span> <span data-ttu-id="ac686-133">就像您的 SQL database 的私人虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ac686-133">It's like having a private virtual network for your SQL databases.</span></span>

## <a name="when-to-migrate-to-azure-sql-database"></a><span data-ttu-id="ac686-134">移轉至 Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="ac686-134">When to migrate to Azure SQL Database</span></span>

<span data-ttu-id="ac686-135">如前所述，標準的 Azure SQL Database 是完全受控的關聯式 DBaaS。</span><span class="sxs-lookup"><span data-stu-id="ac686-135">As mentioned, the standard Azure SQL Database is a fully managed, relational DBaaS.</span></span> <span data-ttu-id="ac686-136">目前，SQL Database 會管理數以百萬計的生產資料庫，在世界各地的 38 資料中心。</span><span class="sxs-lookup"><span data-stu-id="ac686-136">SQL Database currently manages millions of production databases, across 38 datacenters, around the world.</span></span> <span data-ttu-id="ac686-137">它支援廣泛的應用程式和工作負載，從管理簡單的交易資料，以推動需要全球規模的進階的資料處理的資料密集、 任務關鍵性應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac686-137">It supports a broad range of applications and workloads, from managing straightforward transactional data, to driving the most data-intensive, mission-critical applications that require advanced data processing at a global scale.</span></span>

<span data-ttu-id="ac686-138">因為其完整的 PaaS 功能，更好的定價層和最終降低成本-您應該移至標準的 Azure SQL Database 為您的 「 預設為選擇 「 如果您的應用程式，會使用基本、 標準 SQL database 和任何額外的執行個體功能。</span><span class="sxs-lookup"><span data-stu-id="ac686-138">Because of its full PaaS features, better pricing-and ultimately lower cost-you should move to the standard Azure SQL Database as your "by-default choice" if you have an application that uses basic, standard SQL databases, and no additional instance features.</span></span> <span data-ttu-id="ac686-139">標準的 Azure SQL Database 中不支援 SQL Server 功能，像是 SQL CLR 整合、 SQL Server Agent，以及跨資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="ac686-139">SQL Server features like SQL CLR integration, SQL Server Agent, and cross-database querying are not supported in the standard Azure SQL Database.</span></span> <span data-ttu-id="ac686-140">這些功能是僅適用於 Azure SQL Database 受控執行個體模型。</span><span class="sxs-lookup"><span data-stu-id="ac686-140">Those features are available only in the Azure SQL Database Managed Instance model.</span></span>

<span data-ttu-id="ac686-141">Azure SQL Database 是建置應用程式開發人員只智慧型雲端資料庫服務。</span><span class="sxs-lookup"><span data-stu-id="ac686-141">Azure SQL Database is the only intelligent cloud database service that's built for app developers.</span></span> <span data-ttu-id="ac686-142">它也是唯一的雲端資料庫服務，可擴展上作業，而不需要停機，可協助您有效率地提供多租用戶的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac686-142">It's also the only cloud database service that scales on-the-fly, without downtime, to help you efficiently deliver multitenant apps.</span></span> <span data-ttu-id="ac686-143">最後，Azure SQL Database 會讓您更多時間發揮創意，，而且它加速上市的時間。</span><span class="sxs-lookup"><span data-stu-id="ac686-143">Ultimately, Azure SQL Database leaves you more time to innovate, and it accelerates your time to market.</span></span> <span data-ttu-id="ac686-144">您可以建置安全應用程式，並使用您偏好的平台與語言連線到您的 SQL database。</span><span class="sxs-lookup"><span data-stu-id="ac686-144">You can build secure apps and connect to your SQL database by using the languages and platforms that you prefer.</span></span>

<span data-ttu-id="ac686-145">Azure SQL Database 提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="ac686-145">Azure SQL Database offers the following benefits:</span></span>

- <span data-ttu-id="ac686-146">可學習並適應您的應用程式的內建智慧 （機器學習服務）</span><span class="sxs-lookup"><span data-stu-id="ac686-146">Built-in intelligence (machine learning) that learns and adapts to your app</span></span>

- <span data-ttu-id="ac686-147">視資料庫佈建</span><span class="sxs-lookup"><span data-stu-id="ac686-147">On-demand database provisioning</span></span>

- <span data-ttu-id="ac686-148">範圍的所有工作負載的供應項目</span><span class="sxs-lookup"><span data-stu-id="ac686-148">A range of offers, for all workloads</span></span>

- <span data-ttu-id="ac686-149">99.99%可用性 SLA，不需要維護</span><span class="sxs-lookup"><span data-stu-id="ac686-149">99.99% availability SLA, zero maintenance</span></span>

- <span data-ttu-id="ac686-150">資料保護的異地複寫和還原服務</span><span class="sxs-lookup"><span data-stu-id="ac686-150">Geo-replication and restore services for data protection</span></span>

- <span data-ttu-id="ac686-151">在 還原時間功能的 azure SQL Database 點</span><span class="sxs-lookup"><span data-stu-id="ac686-151">Azure SQL Database Point in Time Restore feature</span></span>

- <span data-ttu-id="ac686-152">使用 SQL Server 2016，包括混合式和移轉的相容性</span><span class="sxs-lookup"><span data-stu-id="ac686-152">Compatibility with SQL Server 2016, including hybrid and migration</span></span>

<span data-ttu-id="ac686-153">標準的 Azure SQL Database 是較接近 PaaS 比 Azure SQL Database 受控執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac686-153">The standard Azure SQL Database is closer to PaaS than Azure SQL Database Managed Instance.</span></span> <span data-ttu-id="ac686-154">偏好使用標準的 Azure SQL Database，因為您會從受管理的雲端中享有更多好處。</span><span class="sxs-lookup"><span data-stu-id="ac686-154">Prefer the standard Azure SQL Database because you'll get more benefits from a managed cloud.</span></span> <span data-ttu-id="ac686-155">不過，Azure SQL Database 已從一般的一些主要差異和內部部署 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac686-155">However, Azure SQL Database has some key differences from regular and on-premises SQL Server instances.</span></span> <span data-ttu-id="ac686-156">根據現有的應用程式的資料庫需求，以及您企業需求和原則，它可能不是最佳選擇在規劃移轉至雲端時。</span><span class="sxs-lookup"><span data-stu-id="ac686-156">Depending on your existing application's database requirements, and your enterprise requirements and policies, it might not be the best choice when you are planning your migration to the cloud.</span></span>

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a><span data-ttu-id="ac686-157">將原始的 RDBMS 移到 VM (IaaS) 的時機</span><span class="sxs-lookup"><span data-stu-id="ac686-157">When to move your original RDBMS to a VM (IaaS)</span></span>

<span data-ttu-id="ac686-158">移轉選項的其中一個是移動您原始關聯式資料庫管理系統 (RDBMS)，包括 Oracle、 IBM DB2、 MySQL、 PostgreSQL 或 SQL Server 到類似的伺服器在 Azure VM 上執行。</span><span class="sxs-lookup"><span data-stu-id="ac686-158">One of your migration options is to move your original relational database management system (RDBMS), including Oracle, IBM DB2, MySQL, PostgreSQL, or SQL Server, to a similar server that's running on an Azure VM.</span></span> <span data-ttu-id="ac686-159">如果您有現有的應用程式完全需要最快速移轉至雲端，幾乎不需要變更或完全不變更時，直接移轉至雲端中的 IaaS 可能是合理的選項。</span><span class="sxs-lookup"><span data-stu-id="ac686-159">If you have existing applications that require the fastest migration to the cloud with minimal changes, or no changes at all, a direct migration to IaaS in the cloud might be a fair option.</span></span> <span data-ttu-id="ac686-160">它可能無法利用所有的雲端優勢的最佳辦法，但它可能是最快速的初始路徑。</span><span class="sxs-lookup"><span data-stu-id="ac686-160">It might not be the best way to take advantage of all the cloud's benefits, but it's probably the fastest initial path.</span></span>

<span data-ttu-id="ac686-161">目前，Microsoft Azure 支援最多[331 不同資料庫伺服器](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all)部署為 IaaS Vm。</span><span class="sxs-lookup"><span data-stu-id="ac686-161">Currently, Microsoft Azure supports up to [331 different database servers](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) deployed as IaaS VMs.</span></span> <span data-ttu-id="ac686-162">這些包括常用的 RDBMS，例如 SQL Server、 Oracle、 MySQL、 PostgreSQL 和 IBM DB2 和 MongoDB、 Cassandra、 DataStax、 MariaDB 和 Cloudera 等許多其他 NoSQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ac686-162">These include popular RDBMS like SQL Server, Oracle, MySQL, PostgreSQL, and IBM DB2, and many other NoSQL databases like MongoDB, Cassandra, DataStax, MariaDB, and Cloudera.</span></span>

> [!NOTE]
> <span data-ttu-id="ac686-163">雖然移動您 RDBMS 至 Azure VM 可能是最快速的方式將資料移轉至雲端 （因為它是 IaaS），這種方法需要大量投資您的 IT 團隊 （資料庫管理員和 IT 專業人員）。</span><span class="sxs-lookup"><span data-stu-id="ac686-163">Although moving your RDBMS to an Azure VM might be the fastest way to migrate your data to the cloud (because it is IaaS), this approach requires a significant investment in your IT teams (database administrators and IT pros).</span></span> <span data-ttu-id="ac686-164">企業團隊必須要能夠設定和管理高可用性、 災害復原及修補 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ac686-164">Enterprise teams need to be able to set up and manage high availability, disaster recovery, and patching for SQL Server.</span></span> <span data-ttu-id="ac686-165">此內容也需要自訂的環境中，以完整系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="ac686-165">This context also needs a customized environment, with full administrative rights.</span></span>

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a><span data-ttu-id="ac686-166">為 VM (IaaS) 移轉至 SQL Server 的時機</span><span class="sxs-lookup"><span data-stu-id="ac686-166">When to migrate to SQL Server as a VM (IaaS)</span></span>

<span data-ttu-id="ac686-167">可能有少數情況下，您仍然需要移轉至 SQL Server 和一般 VM。</span><span class="sxs-lookup"><span data-stu-id="ac686-167">There might be a few cases where you still need to migrate to SQL Server as a regular VM.</span></span> <span data-ttu-id="ac686-168">如果您要使用 SQL Server Reporting Services 即為一例。</span><span class="sxs-lookup"><span data-stu-id="ac686-168">An example scenario is if you need to use SQL Server Reporting Services.</span></span> <span data-ttu-id="ac686-169">在大部分情況下，不過，Azure SQL Database 受控執行個體可以提供您需要讓移轉至 SQL Server VM 應該是您最後的手段，嘗試從內部部署 SQL 伺服器，移轉的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ac686-169">In most cases, though, Azure SQL Database Managed Instance can provide everything you need to migrate from on-premises SQL servers, so migration to a SQL Server VM should be your last resort to try.</span></span>

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a><span data-ttu-id="ac686-170">使用 Azure 資料庫移轉服務來將關聯式資料庫移轉至 Azure</span><span class="sxs-lookup"><span data-stu-id="ac686-170">Use Azure Database Migration Service to migrate your relational databases to Azure</span></span> 

<span data-ttu-id="ac686-171">不論您的目標資料庫是 Azure SQL Database、 Azure SQL Database 受控執行個體或在 Azure VM 上的 SQL Server，您可以將 SQL Server、 Oracle 和 MySQL 等關聯式資料庫移轉至 Azure，使用 Azure 資料庫移轉服務。</span><span class="sxs-lookup"><span data-stu-id="ac686-171">You can use Azure Database Migration Service to migrate relational databases like SQL Server, Oracle, and MySQL to Azure, whether your target database is Azure SQL Database, Azure SQL Database Managed Instance, or SQL Server on an Azure VM.</span></span>

<span data-ttu-id="ac686-172">自動化的工作流程中，透過評估報告，會引導您完成您需要先將資料庫移轉進行的變更。</span><span class="sxs-lookup"><span data-stu-id="ac686-172">The automated workflow, with assessment reporting, guides you through the changes you need to make before you migrate the database.</span></span> <span data-ttu-id="ac686-173">準備好時，服務會將來源資料庫移轉至 Azure。</span><span class="sxs-lookup"><span data-stu-id="ac686-173">When you are ready, the service migrates the source database to Azure.</span></span>

<span data-ttu-id="ac686-174">每當您變更原始 RDBMS 時，您可能需要重新測試。</span><span class="sxs-lookup"><span data-stu-id="ac686-174">Whenever you change an original RDBMS, you might need to retest.</span></span> <span data-ttu-id="ac686-175">您也可能需要變更的 SQL 句子或您的應用程式，根據測試結果中的物件關聯式對應 (ORM) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac686-175">You also might need to change the SQL sentences or Object-Relational Mapping (ORM) code in your application, depending on testing results.</span></span>

<span data-ttu-id="ac686-176">如果您有其他任何資料庫 (例如 IBM DB2)，而且您選擇使用原形方法，您可能想要繼續使用這些資料庫做為 IaaS Vm 在 Azure 中，除非您願意執行更複雜的資料移轉。</span><span class="sxs-lookup"><span data-stu-id="ac686-176">If you have any other database (for example, IBM DB2) and you opt for a lift and shift approach, you might want to continue using those databases as IaaS VMs in Azure, unless you are willing to perform a more complex data migration.</span></span> <span data-ttu-id="ac686-177">更複雜的資料移轉將會需要額外的工作，因為您會移轉至新的結構描述和不同的程式設計程式庫的不同的資料庫型別。</span><span class="sxs-lookup"><span data-stu-id="ac686-177">A more complex data migration will require additional effort because you'd be migrating to a different database type with new schema and different programming libraries.</span></span>

<span data-ttu-id="ac686-178">若要了解如何使用 Azure 資料庫移轉服務來移轉資料庫，請參閱[前往 Azure SQL Database 受控執行個體和 Azure 資料庫移轉服務使用更快速地定域機組](https://channel9.msdn.com/Events/Build/2017/P4008)。</span><span class="sxs-lookup"><span data-stu-id="ac686-178">To learn how to migrate databases by using Azure Database Migration Service, see [Get to the cloud faster with Azure SQL Database Managed Instance and Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ac686-179">其他資源</span><span class="sxs-lookup"><span data-stu-id="ac686-179">Additional resources</span></span>

- <span data-ttu-id="ac686-180">**選擇雲端 SQL Server 選項：Azure SQL Database (PaaS) 或 Azure VM (IaaS) 上的 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ac686-180">**Choose a cloud SQL Server option: Azure SQL Database (PaaS) or SQL Server on Azure VM (IaaS)**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- <span data-ttu-id="ac686-181">**取得雲端使用 Azure SQL DB 受控執行個體和資料庫移轉服務更快**</span><span class="sxs-lookup"><span data-stu-id="ac686-181">**Get to the cloud faster with Azure SQL DB Managed Instance and Database Migration Service**</span></span>

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- <span data-ttu-id="ac686-182">**SQL Server 資料庫移轉至雲端 SQL Database**</span><span class="sxs-lookup"><span data-stu-id="ac686-182">**SQL Server database migration to SQL Database in the cloud**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- <span data-ttu-id="ac686-183">**Azure SQL Database**</span><span class="sxs-lookup"><span data-stu-id="ac686-183">**Azure SQL Database**</span></span>

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- <span data-ttu-id="ac686-184">**在虛擬機器上的 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ac686-184">**SQL Server on virtual machines**</span></span>

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> <span data-ttu-id="ac686-185">[上一頁](lift-and-shift-existing-apps-azure-iaas.md)
> [下一頁](modernize-existing-apps-to-cloud-optimized/index.md)</span><span class="sxs-lookup"><span data-stu-id="ac686-185">[Previous](lift-and-shift-existing-apps-azure-iaas.md)
[Next](modernize-existing-apps-to-cloud-optimized/index.md)</span></span>
