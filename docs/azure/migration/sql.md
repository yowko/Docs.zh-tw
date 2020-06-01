---
title: 將 SQL Server 資料庫移轉至 Azure
description: 了解如何從內部部署 SQL Server 將 SQL Server 資料庫移轉到 Azure。
ms.topic: how-to
ms.date: 05/27/2020
ms.openlocfilehash: ed5d6ef9395dca14d8e0ecba82d3fc18cb3d629a
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241444"
---
# <a name="migrate-a-sql-server-database-to-azure"></a><span data-ttu-id="f9cb6-103">將 SQL Server 資料庫移轉至 Azure</span><span class="sxs-lookup"><span data-stu-id="f9cb6-103">Migrate a SQL Server database to Azure</span></span>

<span data-ttu-id="f9cb6-104">本文提供兩個選項的簡要概述，可將 SQL Server 資料庫移轉至 Azure。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-104">This article provides a brief outline of two options for migrating a SQL Server database to Azure.</span></span> <span data-ttu-id="f9cb6-105">Azure 有三個主要選項可用於遷移生產 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-105">Azure has three primary options for migrating a production SQL Server database.</span></span> <span data-ttu-id="f9cb6-106">本文著重于下列兩個選項：</span><span class="sxs-lookup"><span data-stu-id="f9cb6-106">This article focuses on the following two options:</span></span>

1. <span data-ttu-id="f9cb6-107">[Azure VM 上的 SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview)：安裝並裝載在 Azure 中執行的 Windows 虛擬機器上的 SQL Server 執行個體，也稱為基礎結構即服務 (IaaS)。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-107">[SQL Server on Azure VMs](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): A SQL Server instance installed and hosted on a Windows Virtual Machine running in Azure, also known as Infrastructure as a Service (IaaS).</span></span>
2. <span data-ttu-id="f9cb6-108">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)：完全受控的 SQL 資料庫 Azure 服務，也稱為平台即服務 (PaaS)。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-108">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): A fully managed SQL database Azure service, also known as Platform as a Service (PaaS).</span></span>

<span data-ttu-id="f9cb6-109">兩者皆具優缺點，您必須在移轉前進行評估。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-109">Both come with pros and cons that you will need to evaluate before migrating.</span></span> <span data-ttu-id="f9cb6-110">第三個選項是[Azure SQL Database 受控實例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-110">The third option is [Azure SQL Database managed instances](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).</span></span>

## <a name="get-started"></a><span data-ttu-id="f9cb6-111">開始使用</span><span class="sxs-lookup"><span data-stu-id="f9cb6-111">Get started</span></span>

<span data-ttu-id="f9cb6-112">根據您使用的服務選擇下列實用的移轉指南：</span><span class="sxs-lookup"><span data-stu-id="f9cb6-112">The following migration guides will be useful, depending on which service you use:</span></span>

* [<span data-ttu-id="f9cb6-113">將 SQL Server 資料庫移轉至 Azure VM 中的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="f9cb6-113">Migrate a SQL Server database to SQL Server in an Azure VM</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [<span data-ttu-id="f9cb6-114">將 SQL Server Database 移轉至 Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="f9cb6-114">Migrate your SQL Server database to Azure SQL Database</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

<span data-ttu-id="f9cb6-115">此外，下列連結提供概念性的內容，將協助您進一步了解 VM：</span><span class="sxs-lookup"><span data-stu-id="f9cb6-115">Additionally, the following links to conceptual content will help you understand VMs better:</span></span>

* [<span data-ttu-id="f9cb6-116">Azure 虛擬機器中的 SQL Server 高可用性和災害復原</span><span class="sxs-lookup"><span data-stu-id="f9cb6-116">High availability and disaster recovery for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [<span data-ttu-id="f9cb6-117">Azure 虛擬機器中的 SQL Server 效能最佳做法</span><span class="sxs-lookup"><span data-stu-id="f9cb6-117">Performance best practices for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [<span data-ttu-id="f9cb6-118">Azure 虛擬機器中的 SQL Server 應用程式模式和開發策略</span><span class="sxs-lookup"><span data-stu-id="f9cb6-118">Application Patterns and Development Strategies for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

<span data-ttu-id="f9cb6-119">下列連結可協助您進一步了解 Azure SQL Database：</span><span class="sxs-lookup"><span data-stu-id="f9cb6-119">And the following links will help you understand Azure SQL Database better:</span></span>

* [<span data-ttu-id="f9cb6-120">建立和管理 Azure SQL Database 伺服器與資料庫</span><span class="sxs-lookup"><span data-stu-id="f9cb6-120">Create and manage Azure SQL Database servers and databases</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [<span data-ttu-id="f9cb6-121">資料庫交易單位 (DTU) 和彈性資料庫交易單位 (eDTU)</span><span class="sxs-lookup"><span data-stu-id="f9cb6-121">Database Transaction Units (DTUs) and elastic Database Transaction Units (eDTUs)</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [<span data-ttu-id="f9cb6-122">Azure SQL Database 資源限制</span><span class="sxs-lookup"><span data-stu-id="f9cb6-122">Azure SQL Database resource limits</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a><span data-ttu-id="f9cb6-123">選擇 IaaS 或 PaaS</span><span class="sxs-lookup"><span data-stu-id="f9cb6-123">Choosing IaaS or PaaS</span></span>

<span data-ttu-id="f9cb6-124">在評估要遷移資料庫的位置時，請判斷 IaaS 或 PaaS 是否較適合您。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-124">When evaluating where to migrate your database, determine if IaaS or PaaS is more appropriate for you.</span></span>

<span data-ttu-id="f9cb6-125">**如果有下列情況，請選擇 Azure Vm 中的 SQL Server：**</span><span class="sxs-lookup"><span data-stu-id="f9cb6-125">**Choose SQL Server in Azure VMs if:**</span></span>

* <span data-ttu-id="f9cb6-126">您想要「隨即轉移」資料庫和應用程式，且讓變更最少或無變更。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-126">You are looking to "lift and shift" your database and applications with minimal to no changes.</span></span>
* <span data-ttu-id="f9cb6-127">您想要完整控制資料庫伺服器和其執行位置所在的 VM。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-127">You prefer having full control over your database server and the VM it runs on.</span></span>
* <span data-ttu-id="f9cb6-128">您已擁有打算使用的 SQL Server 和 Windows Server 授權。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-128">You already have SQL Server and Windows Server licenses that you intend to use.</span></span>

<span data-ttu-id="f9cb6-129">**如果是下列情形，請選擇 Azure SQL Database ：**</span><span class="sxs-lookup"><span data-stu-id="f9cb6-129">**Choose Azure SQL Database if:**</span></span>

* <span data-ttu-id="f9cb6-130">您想要將應用程式現代化，且正在移轉以使用其他 Azure 中的 PaaS 服務。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-130">You are looking to modernize your applications and are migrating to use other PaaS services in Azure.</span></span>
* <span data-ttu-id="f9cb6-131">您不想管理資料庫伺服器和其執行位置所在的 VM。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-131">You do not wish to manage your database server and the VM it runs on.</span></span>
* <span data-ttu-id="f9cb6-132">您沒有 SQL Server 或 Windows Server 授權，或您打算讓擁有的授權到期。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-132">You do not have SQL Server or Windows Server licenses, or you intend to let licenses you have expire.</span></span>

<span data-ttu-id="f9cb6-133">下表根據各組案例說明每個服務之間的差異。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-133">The following table describes differences between each service based on a set of scenarios.</span></span>

| <span data-ttu-id="f9cb6-134">狀況</span><span class="sxs-lookup"><span data-stu-id="f9cb6-134">Scenario</span></span> | <span data-ttu-id="f9cb6-135">Azure VM 中的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="f9cb6-135">SQL Server in Azure VMs</span></span> | <span data-ttu-id="f9cb6-136">Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="f9cb6-136">Azure SQL Database</span></span> |
|----------|-------------------------|--------------------|
| <span data-ttu-id="f9cb6-137">遷移</span><span class="sxs-lookup"><span data-stu-id="f9cb6-137">Migration</span></span> | <span data-ttu-id="f9cb6-138">資料庫所需變更最少。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-138">Requires minimal changes to your database.</span></span> | <span data-ttu-id="f9cb6-139">如果您使用 Azure SQL 中無法使用的功能 (由[資料移轉小幫手](https://www.microsoft.com/download/details.aspx?id=53595)判定)，或如果您有其他相依性，如在本機安裝的可執行檔，則可能需要變更資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-139">May require changes to your database if you use features unavailable in Azure SQL, as determined by the [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595), or if you have other dependencies such as locally installed executables.</span></span>|
| <span data-ttu-id="f9cb6-140">管理可用性、復原及升級</span><span class="sxs-lookup"><span data-stu-id="f9cb6-140">Managing availability, recovery, and upgrades</span></span> | <span data-ttu-id="f9cb6-141">可用性和復原是以手動方式設定。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-141">Availability and recovery are configured manually.</span></span> <span data-ttu-id="f9cb6-142">升級可以透過 [VM 擴展集](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)自動化。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-142">Upgrades can be automated with [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade).</span></span> | <span data-ttu-id="f9cb6-143">為您自動管理。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-143">Automatically managed for you.</span></span> |
| <span data-ttu-id="f9cb6-144">基礎作業系統設定</span><span class="sxs-lookup"><span data-stu-id="f9cb6-144">Underlying OS configuration</span></span> | <span data-ttu-id="f9cb6-145">手動設定。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-145">Manual configuration.</span></span> | <span data-ttu-id="f9cb6-146">為您自動管理。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-146">Automatically managed for you.</span></span> |
| <span data-ttu-id="f9cb6-147">管理資料庫大小</span><span class="sxs-lookup"><span data-stu-id="f9cb6-147">Managing database size</span></span> | <span data-ttu-id="f9cb6-148">針對每個 SQL Server 實例最多支援 256 TB 的儲存體。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-148">Supports up to 256 TB of storage per SQL Server instance.</span></span> | <span data-ttu-id="f9cb6-149">在需要水準資料分割之前，支援 8 TB 的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-149">Supports 8 TB of storage before needing a horizontal partition.</span></span> |
| <span data-ttu-id="f9cb6-150">管理成本</span><span class="sxs-lookup"><span data-stu-id="f9cb6-150">Managing costs</span></span> | <span data-ttu-id="f9cb6-151">您必須管理 SQL Server 授權成本、Windows Server 授權成本以及 VM 成本 (根據核心、RAM 和儲存體)。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-151">You must manage SQL Server license costs, Windows Server license costs, and VM costs (based on cores, RAM, and storage).</span></span> | <span data-ttu-id="f9cb6-152">您必須管理服務成本 (根據 [eDTU 或 DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)、儲存體以及資料庫數目 (如果使用彈性集區))。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-152">You must manage service costs (based on [eDTUs or DTUs](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), storage, and number of databases if using an elastic pool).</span></span> <span data-ttu-id="f9cb6-153">您也必須管理任何 SLA 的成本。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-153">You must also manage the cost of any SLA.</span></span> |

<span data-ttu-id="f9cb6-154">若要深入瞭解兩者之間的差異，請參閱[在 AZURE SQL 中選擇正確的部署選項](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-154">To learn more about the differences between the two, see [Choose the right deployment option in Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).</span></span>

## <a name="faq"></a><span data-ttu-id="f9cb6-155">常見問題集</span><span class="sxs-lookup"><span data-stu-id="f9cb6-155">FAQ</span></span>

* <span data-ttu-id="f9cb6-156">**我仍然可以使用如 SQL Server Management Studio 和 SQL Server Reporting Services (SSRS) 等工具，搭配 Azure VM 中的 SQL Server 或 Azure SQL Database 嗎？**</span><span class="sxs-lookup"><span data-stu-id="f9cb6-156">**Can I still use tools such as SQL Server Management Studio and SQL Server Reporting Services (SSRS) with SQL Server in Azure VMs or Azure SQL Database?**</span></span>

    <span data-ttu-id="f9cb6-157">是。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-157">Yes.</span></span> <span data-ttu-id="f9cb6-158">所有 Microsoft SQL 工具皆可搭配使用這兩項服務。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-158">All Microsoft SQL tooling works with both services.</span></span> <span data-ttu-id="f9cb6-159">但 SSRS 並非 Azure SQL Database 的一部分，建議您在 Azure VM 中執行它，然後將其指向您的資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-159">SSRS is not part of Azure SQL Database, though, and it's recommended that you run it in an Azure VM and then point it to your database instance.</span></span>

* <span data-ttu-id="f9cb6-160">**我想要用 PaaS，但我不確定資料庫是否相容。有工具可以協助嗎？**</span><span class="sxs-lookup"><span data-stu-id="f9cb6-160">**I want to go PaaS but I'm not sure if my database is compatible. Are there tools to help?**</span></span>

    <span data-ttu-id="f9cb6-161">是。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-161">Yes.</span></span> <span data-ttu-id="f9cb6-162">[資料移轉小幫手](https://www.microsoft.com/download/details.aspx?id=53595)是移轉到 Azure SQL Database 的一部分所用工具。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-162">The [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) is a tool that is used as a part of migrating to Azure SQL Database.</span></span> <span data-ttu-id="f9cb6-163">[Azure 資料庫移轉服務](https://azure.microsoft.com/campaigns/database-migration/)是一項預覽服務，可供您用於 IaaS 或 PaaS。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-163">The [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) is a preview service that you can use for either IaaS or PaaS.</span></span>

* <span data-ttu-id="f9cb6-164">**我可以預估成本嗎？**</span><span class="sxs-lookup"><span data-stu-id="f9cb6-164">**Can I estimate costs?**</span></span>

    <span data-ttu-id="f9cb6-165">是。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-165">Yes.</span></span> <span data-ttu-id="f9cb6-166">[Azure 價格計算機](https://azure.microsoft.com/pricing/calculator/)可針對所有 Azure 服務 (包括 VM 及資料庫服務) 進行成本預估。</span><span class="sxs-lookup"><span data-stu-id="f9cb6-166">The [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/) can be used for estimating costs for all Azure services, including VMs and database services.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9cb6-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f9cb6-167">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9cb6-168">選擇正確的 Azure 裝載選項</span><span class="sxs-lookup"><span data-stu-id="f9cb6-168">Choose the right Azure hosting option</span></span>](choose.md)
