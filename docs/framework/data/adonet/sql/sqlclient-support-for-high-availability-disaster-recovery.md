---
title: 高可用性、嚴重損壞修復的 SqlClient 支援
description: 瞭解如何使用 AlwaysOn 可用性群組在 SQL Server 中 SqlClient 應用程式支援，以取得高可用性、嚴重損壞修復。
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: eba243d37db8262970d161cfa786d3aee4462950
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286206"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="32ca2-103">高可用性、嚴重損壞修復的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="32ca2-103">SqlClient Support for High Availability, Disaster Recovery</span></span>
<span data-ttu-id="32ca2-104">本主題討論適用于高可用性、嚴重損壞修復的 SqlClient 支援（新增于 .NET Framework 4.5）--AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="32ca2-104">This topic discusses SqlClient support (added in .NET Framework 4.5) for high-availability, disaster recovery -- AlwaysOn Availability Groups.</span></span>  <span data-ttu-id="32ca2-105">SQL Server 2012 新增了 AlwaysOn 可用性群組功能。</span><span class="sxs-lookup"><span data-stu-id="32ca2-105">AlwaysOn Availability Groups feature was added to SQL Server 2012.</span></span> <span data-ttu-id="32ca2-106">如需 AlwaysOn 可用性群組的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="32ca2-106">For more information about AlwaysOn Availability Groups, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="32ca2-107">現在，您可以在連線屬性中指定 (高可用性、災害復原) 可用性群組 (AG) 的可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="32ca2-107">You can now specify the availability group listener of a (high-availability, disaster-recovery) availability group (AG) or SQL Server 2012 Failover Cluster Instance in the connection property.</span></span> <span data-ttu-id="32ca2-108">如果 SqlClient 應用程式連線到容錯移轉的 AlwaysOn 資料庫，原始連線會中斷，應用程式必須開啟新的連線，才能在容錯移轉後繼續工作。</span><span class="sxs-lookup"><span data-stu-id="32ca2-108">If a SqlClient application is connected to an AlwaysOn database that fails over, the original connection is broken and the application must open a new connection to continue work after the failover.</span></span>  
  
 <span data-ttu-id="32ca2-109">如果您沒有連線到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體，或是有多個 IP 位址與主機名稱相關聯，則 SqlClient 會依序逐一查看所有與 DNS 項目相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="32ca2-109">If you are not connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, and if multiple IP addresses are associated with a hostname, SqlClient will iterate sequentially through all IP addresses associated with DNS entry.</span></span> <span data-ttu-id="32ca2-110">如果 DNS 伺服器所傳回的第一個 IP 位址未繫結至任何網路介面卡 (NIC)，這項作業可能會很費時。</span><span class="sxs-lookup"><span data-stu-id="32ca2-110">This can be time consuming if the first IP address returned by DNS server is not bound to any network interface card (NIC).</span></span> <span data-ttu-id="32ca2-111">連線到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體時，SqlClient 會嘗試平行建立與所有 IP 位址的連線，若其中一個連線嘗試成功，驅動程式會捨棄所有擱置中的連線嘗試。</span><span class="sxs-lookup"><span data-stu-id="32ca2-111">When connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, SqlClient attempts to establish connections to all IP addresses in parallel and if a connection attempt succeeds, the driver will discard any pending connection attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32ca2-112">增加連接逾時並實作連接重試邏輯可提高應用程式連接到可用性群組的機率。</span><span class="sxs-lookup"><span data-stu-id="32ca2-112">Increasing connection timeout and implementing connection retry logic will increase the probability that an application will connect to an availability group.</span></span> <span data-ttu-id="32ca2-113">此外，因為連線可能會由於容錯移轉而失敗，所以您應該實作連線重試邏輯，並重試失敗的連線，直到重新連線為止。</span><span class="sxs-lookup"><span data-stu-id="32ca2-113">Also, because a connection can fail because of a failover, you should implement connection retry logic, retrying a failed connection until it reconnects.</span></span>  
  
 <span data-ttu-id="32ca2-114">下列連接屬性已新增至 .NET Framework 4.5 中的 SqlClient：</span><span class="sxs-lookup"><span data-stu-id="32ca2-114">The following connection properties were added to SqlClient in .NET Framework 4.5:</span></span>  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 <span data-ttu-id="32ca2-115">您可以透過下列方式，以程式設計方式修改這些連接字串關鍵字：</span><span class="sxs-lookup"><span data-stu-id="32ca2-115">You can programmatically modify these connection string keywords with:</span></span>  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> <span data-ttu-id="32ca2-116">`MultiSubnetFailover` `true` .NET Framework 4.6.1 或更新版本不需要將設定為。</span><span class="sxs-lookup"><span data-stu-id="32ca2-116">Setting `MultiSubnetFailover` to `true` isn't required with .NET Framework 4.6.1 or later versions.</span></span>
  
## <a name="connecting-with-multisubnetfailover"></a><span data-ttu-id="32ca2-117">使用 MultiSubnetFailover 進行連接</span><span class="sxs-lookup"><span data-stu-id="32ca2-117">Connecting With MultiSubnetFailover</span></span>  
 <span data-ttu-id="32ca2-118">在連接到 SQL Server 2012 可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體時，永遠指定 `MultiSubnetFailover=True`。</span><span class="sxs-lookup"><span data-stu-id="32ca2-118">Always specify `MultiSubnetFailover=True` when connecting to a SQL Server 2012 availability group listener or SQL Server 2012 Failover Cluster Instance.</span></span> <span data-ttu-id="32ca2-119">`MultiSubnetFailover` 對於 SQL Server 2012 中的所有可用性群組和容錯移轉叢集執行個體可促進更快的容錯移轉，並大幅縮短單一和多重子網路 AlwaysOn 拓撲的容錯移轉時間。</span><span class="sxs-lookup"><span data-stu-id="32ca2-119">`MultiSubnetFailover` enables faster failover for all Availability Groups and or Failover Cluster Instance in SQL Server 2012 and will significantly reduce failover time for single and multi-subnet AlwaysOn topologies.</span></span> <span data-ttu-id="32ca2-120">在多重子網路容錯移轉期間，用戶端會平行嘗試連接。</span><span class="sxs-lookup"><span data-stu-id="32ca2-120">During a multi-subnet failover, the client will attempt connections in parallel.</span></span> <span data-ttu-id="32ca2-121">在子網路容錯移轉期間，會積極重試 TCP 連線。</span><span class="sxs-lookup"><span data-stu-id="32ca2-121">During a subnet failover, will aggressively retry the TCP connection.</span></span>  
  
 <span data-ttu-id="32ca2-122">`MultiSubnetFailover` 連線屬性表示會將應用程式部署至可用性群組或 SQL Server 2012 容錯移轉叢集執行個體，且 SqlClient 將透過嘗試連線至所有 IP 位址，嘗試連線至主要 SQL Server 執行個體上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32ca2-122">The `MultiSubnetFailover` connection property indicates that the application is being deployed in an availability group or SQL Server 2012 Failover Cluster Instance and that SqlClient will try to connect to the database on the primary SQL Server instance by trying to connect to all the IP addresses.</span></span> <span data-ttu-id="32ca2-123">為連線指定 `MultiSubnetFailover=True` 時，用戶端會重試 TCP 連線，其速度比作業系統的預設 TCP 重新傳輸間隔更快。</span><span class="sxs-lookup"><span data-stu-id="32ca2-123">When `MultiSubnetFailover=True` is specified for a connection, the client retries TCP connection attempts faster than the operating system’s default TCP retransmit intervals.</span></span> <span data-ttu-id="32ca2-124">這種方式可在容錯移轉 AlwaysOn 可用性群組或 AlwaysOn 容錯移轉叢集執行個體之後更快重新連線，且同時適用於單一和多重子網路可用性群組和容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="32ca2-124">This enables faster reconnection after failover of either an AlwaysOn Availability Group or an AlwaysOn Failover Cluster Instance, and is applicable to both single- and multi-subnet Availability Groups and Failover Cluster Instances.</span></span>  
  
 <span data-ttu-id="32ca2-125">如需 SqlClient 中連接字串關鍵字的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="32ca2-125">For more information about connection string keywords in SqlClient, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="32ca2-126">若在連線非可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體時指定 `MultiSubnetFailover=True`，可能會對效能產生負面影響，因此不受支援。</span><span class="sxs-lookup"><span data-stu-id="32ca2-126">Specifying `MultiSubnetFailover=True` when connecting to something other than a availability group listener or SQL Server 2012 Failover Cluster Instance may result in a negative performance impact, and is not supported.</span></span>  
  
 <span data-ttu-id="32ca2-127">請使用下列指導方針，連線到可用性群組或 SQL Server 2012 容錯移轉叢集執行個體中的伺服器：</span><span class="sxs-lookup"><span data-stu-id="32ca2-127">Use the following guidelines to connect to a server in an availability group or SQL Server 2012 Failover Cluster Instance:</span></span>  
  
- <span data-ttu-id="32ca2-128">在連接到單一子網路或多重子網路時，使用 `MultiSubnetFailover` 連接屬性；這會提高這兩種可用性群組接聽程式的效能。</span><span class="sxs-lookup"><span data-stu-id="32ca2-128">Use the `MultiSubnetFailover` connection property when connecting to a single subnet or multi-subnet; it will improve performance for both.</span></span>  
  
- <span data-ttu-id="32ca2-129">若要連接到可用性群組，在連接字串中指定可用性群組的可用性群組接聽程式做為伺服器。</span><span class="sxs-lookup"><span data-stu-id="32ca2-129">To connect to an availability group, specify the availability group listener of the availability group as the server in your connection string.</span></span>  
  
- <span data-ttu-id="32ca2-130">連線到設定超過 64 個 IP 位址的 SQL Server 執行個體會導致連線失敗。</span><span class="sxs-lookup"><span data-stu-id="32ca2-130">Connecting to a SQL Server instance configured with more than 64 IP addresses will cause a connection failure.</span></span>  
  
- <span data-ttu-id="32ca2-131">使用 `MultiSubnetFailover` 連線屬性之應用程式的行為不受驗證類型影響：SQL Server 驗證、Kerberos 驗證或 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="32ca2-131">Behavior of an application that uses the `MultiSubnetFailover` connection property is not affected based on the type of authentication: SQL Server Authentication, Kerberos Authentication, or Windows Authentication.</span></span>  
  
- <span data-ttu-id="32ca2-132">提高 `Connect Timeout` 的值來配合容錯移轉時間，並減少應用程式連線重試次數。</span><span class="sxs-lookup"><span data-stu-id="32ca2-132">Increase the value of `Connect Timeout` to accommodate for failover time and reduce application connection retry attempts.</span></span>  
  
- <span data-ttu-id="32ca2-133">不支援分散式工作階段。</span><span class="sxs-lookup"><span data-stu-id="32ca2-133">Distributed transactions are not supported.</span></span>  
  
 <span data-ttu-id="32ca2-134">如果唯讀路由不在作用中，在下列狀況下，連線到次要複本位置將會失敗：</span><span class="sxs-lookup"><span data-stu-id="32ca2-134">If read-only routing is not in effect, connecting to a secondary replica location will fail in the following situations:</span></span>  
  
1. <span data-ttu-id="32ca2-135">如果未設定次要複本位置接受連接。</span><span class="sxs-lookup"><span data-stu-id="32ca2-135">If the secondary replica location is not configured to accept connections.</span></span>  
  
2. <span data-ttu-id="32ca2-136">如果應用程式使用 `ApplicationIntent=ReadWrite` (下文討論)，而且已針對唯讀存取設定次要複本位置。</span><span class="sxs-lookup"><span data-stu-id="32ca2-136">If an application uses `ApplicationIntent=ReadWrite` (discussed below) and the secondary replica location is configured for read-only access.</span></span>  
  
 <span data-ttu-id="32ca2-137">唯讀的次要複本不支援 <xref:System.Data.SqlClient.SqlDependency>。</span><span class="sxs-lookup"><span data-stu-id="32ca2-137"><xref:System.Data.SqlClient.SqlDependency> is not supported on read-only secondary replicas.</span></span>  
  
 <span data-ttu-id="32ca2-138">如果設定主要複本拒絕唯讀工作負載，而且連接字串包含 `ApplicationIntent=ReadOnly`，則連接會失敗。</span><span class="sxs-lookup"><span data-stu-id="32ca2-138">A connection will fail if a primary replica is configured to reject read-only workloads and the connection string contains `ApplicationIntent=ReadOnly`.</span></span>  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a><span data-ttu-id="32ca2-139">從資料庫鏡像升級到使用多子重網路叢集</span><span class="sxs-lookup"><span data-stu-id="32ca2-139">Upgrading to Use Multi-Subnet Clusters from Database Mirroring</span></span>  
 <span data-ttu-id="32ca2-140">如果連接字串中有 `MultiSubnetFailover` 和 `Failover Partner` 連線關鍵字，或者如果使用了 `MultiSubnetFailover=True` 和 TCP 以外的通訊協定，則將會發生連線錯誤 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="32ca2-140">A connection error (<xref:System.ArgumentException>) will occur if the `MultiSubnetFailover` and `Failover Partner` connection keywords are present in the connection string, or if `MultiSubnetFailover=True` and a protocol other than TCP is used.</span></span> <span data-ttu-id="32ca2-141">如果使用 `MultiSubnetFailover` 而且 SQL Server 傳回容錯移轉夥伴回應，指出其是資料庫鏡像配對的一部分，也會發生錯誤 (<xref:System.Data.SqlClient.SqlException>)。</span><span class="sxs-lookup"><span data-stu-id="32ca2-141">An error (<xref:System.Data.SqlClient.SqlException>) will also occur if `MultiSubnetFailover` is used and the SQL Server returns a failover partner response indicating it is part of a database mirroring pair.</span></span>  
  
 <span data-ttu-id="32ca2-142">如果您將目前使用資料庫鏡像的 SqlClient 應用程式升級為多重子網路案例，應該移除 `Failover Partner` 連線屬性，並以設為 `True` 的 `MultiSubnetFailover` 加以取代，然後以可用性群組接聽程式取代連接字串中的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="32ca2-142">If you upgrade a SqlClient application that currently uses database mirroring to a multi-subnet scenario, you should remove the `Failover Partner` connection property and replace it with `MultiSubnetFailover` set to `True` and replace the server name in the connection string with an availability group listener.</span></span> <span data-ttu-id="32ca2-143">如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=True`，驅動程式會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="32ca2-143">If a connection string uses `Failover Partner` and `MultiSubnetFailover=True`, the driver will generate an error.</span></span> <span data-ttu-id="32ca2-144">不過，如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=False` (或 `ApplicationIntent=ReadWrite`)，應用程式就會使用資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="32ca2-144">However, if a connection string uses `Failover Partner` and `MultiSubnetFailover=False` (or `ApplicationIntent=ReadWrite`), the application will use database mirroring.</span></span>  
  
 <span data-ttu-id="32ca2-145">如果在 AG 的主要資料庫上使用資料庫鏡像，而且在連線至主要資料庫 (而非可用性群組接聽程式) 的連接字串中使用 `MultiSubnetFailover=True`，則驅動程式會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="32ca2-145">The driver will return an error if database mirroring is used on the primary database in the AG, and if `MultiSubnetFailover=True` is used in the connection string that connects to a primary database instead of to an availability group listener.</span></span>  
  
## <a name="specifying-application-intent"></a><span data-ttu-id="32ca2-146">指定應用程式意圖</span><span class="sxs-lookup"><span data-stu-id="32ca2-146">Specifying Application Intent</span></span>  
 <span data-ttu-id="32ca2-147">當 `ApplicationIntent=ReadOnly` 時，用戶端在連接到啟用 AlwaysOn 的資料庫時會要求讀取工作負載。</span><span class="sxs-lookup"><span data-stu-id="32ca2-147">When `ApplicationIntent=ReadOnly`, the client requests a read workload when connecting to an AlwaysOn enabled database.</span></span> <span data-ttu-id="32ca2-148">伺服器會在連接時和在 USE 資料庫陳述式期間，只針對啟用 AlwaysOn 的資料庫強制執行此意圖。</span><span class="sxs-lookup"><span data-stu-id="32ca2-148">The server will enforce the intent at connection time and during a USE database statement but only to an Always On enabled database.</span></span>  
  
 <span data-ttu-id="32ca2-149">`ApplicationIntent` 關鍵字不適用於舊版唯讀資料庫。</span><span class="sxs-lookup"><span data-stu-id="32ca2-149">The `ApplicationIntent` keyword does not work with legacy, read-only databases.</span></span>  
  
 <span data-ttu-id="32ca2-150">資料庫可以允許或不允許 AlwaysOn 目標資料庫上的讀取工作負載</span><span class="sxs-lookup"><span data-stu-id="32ca2-150">A database can allow or disallow read workloads on the targeted AlwaysOn database.</span></span> <span data-ttu-id="32ca2-151">(這會透過 `PRIMARY_ROLE` 和 `SECONDARY_ROLE` Transact-SQL 陳述式的 `ALLOW_CONNECTIONS` 子句來完成)。</span><span class="sxs-lookup"><span data-stu-id="32ca2-151">(This is done with the `ALLOW_CONNECTIONS` clause of the `PRIMARY_ROLE` and `SECONDARY_ROLE`Transact-SQL statements.)</span></span>  
  
 <span data-ttu-id="32ca2-152">`ApplicationIntent` 關鍵字用於啟用唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="32ca2-152">The `ApplicationIntent` keyword is used to enable read-only routing.</span></span>  
  
## <a name="read-only-routing"></a><span data-ttu-id="32ca2-153">唯讀路由</span><span class="sxs-lookup"><span data-stu-id="32ca2-153">Read-Only Routing</span></span>  
 <span data-ttu-id="32ca2-154">唯讀路由是可確保資料庫的唯讀複本之可用性的功能。</span><span class="sxs-lookup"><span data-stu-id="32ca2-154">Read-only routing is a feature that can ensure the availability of a read only replica of a database.</span></span> <span data-ttu-id="32ca2-155">若要啟用唯讀路由：</span><span class="sxs-lookup"><span data-stu-id="32ca2-155">To enable read-only routing:</span></span>  
  
1. <span data-ttu-id="32ca2-156">您必須連接到 AlwaysOn 可用性群組的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="32ca2-156">You must connect to an Always On Availability Group availability group listener.</span></span>  
  
2. <span data-ttu-id="32ca2-157">`ApplicationIntent` 連接字串關鍵字必須設為 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="32ca2-157">The `ApplicationIntent` connection string keyword must be set to `ReadOnly`.</span></span>  
  
3. <span data-ttu-id="32ca2-158">可用性群組必須由資料庫管理員設定為啟用唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="32ca2-158">The Availability Group must be configured by the database administrator to enable read-only routing.</span></span>  
  
 <span data-ttu-id="32ca2-159">使用唯讀路由的多個連接可能不會連接至相同的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="32ca2-159">It is possible that multiple connections using read-only routing will not all connect to the same read-only replica.</span></span> <span data-ttu-id="32ca2-160">資料庫同步處理的變更或伺服器路由組態的變更，可能會導致用戶端連接至不同的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="32ca2-160">Changes in database synchronization or changes in the server's routing configuration can result in client connections to different read-only replicas.</span></span> <span data-ttu-id="32ca2-161">若要確保所有唯讀要求連接至相同的唯讀複本，請勿將可用性群組接聽程式傳遞給 `Data Source` 連接字串關鍵字。</span><span class="sxs-lookup"><span data-stu-id="32ca2-161">To ensure that all read-only requests connect to the same read-only replica, do not pass an availability group listener to the `Data Source` connection string keyword.</span></span> <span data-ttu-id="32ca2-162">請改為指定唯讀執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="32ca2-162">Instead, specify the name of the read-only instance.</span></span>  
  
 <span data-ttu-id="32ca2-163">唯讀路由可能比連接到主要複本的時間更長，因為唯讀路由先連接到主要複本，再尋找最佳的可讀取次要複本。</span><span class="sxs-lookup"><span data-stu-id="32ca2-163">Read-only routing may take longer than connecting to the primary because read only routing first connects to the primary and then looks for the best available readable secondary.</span></span> <span data-ttu-id="32ca2-164">因此，您應該增加登入逾時。</span><span class="sxs-lookup"><span data-stu-id="32ca2-164">Because of this, you should increase your login timeout.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ca2-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32ca2-165">See also</span></span>

- [<span data-ttu-id="32ca2-166">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="32ca2-166">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- <span data-ttu-id="32ca2-167">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="32ca2-167">[ADO.NET Overview](../ado-net-overview.md)</span></span>
