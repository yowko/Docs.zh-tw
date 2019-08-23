---
title: 高可用性、嚴重損壞修復的 SqlClient 支援
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 104fdd78ce3f4b9c18f09fc41fddebe46815d217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938476"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="6102a-102">高可用性、嚴重損壞修復的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="6102a-102">SqlClient Support for High Availability, Disaster Recovery</span></span>
<span data-ttu-id="6102a-103">本主題討論適用于高可用性、嚴重損壞修復的 SqlClient 支援 (新增于 .NET Framework 4.5)--AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="6102a-103">This topic discusses SqlClient support (added in .NET Framework 4.5) for high-availability, disaster recovery -- AlwaysOn Availability Groups.</span></span>  <span data-ttu-id="6102a-104">AlwaysOn 可用性群組功能已新增至 SQL Server 2012。</span><span class="sxs-lookup"><span data-stu-id="6102a-104">AlwaysOn Availability Groups feature was added to SQL Server 2012.</span></span> <span data-ttu-id="6102a-105">如需 AlwaysOn 可用性群組的詳細資訊, 請參閱 SQL Server 線上叢書。</span><span class="sxs-lookup"><span data-stu-id="6102a-105">For more information about AlwaysOn Availability Groups, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="6102a-106">您現在可以在連接屬性中指定 (高可用性、嚴重損壞修復) 可用性群組 (AG) 或 SQL Server 2012 容錯移轉叢集實例的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6102a-106">You can now specify the availability group listener of a (high-availability, disaster-recovery) availability group (AG) or SQL Server 2012 Failover Cluster Instance in the connection property.</span></span> <span data-ttu-id="6102a-107">如果 SqlClient 應用程式連接到容錯移轉的 AlwaysOn 資料庫，原始連接會中斷。容錯移轉之後，應用程式必須開啟新的連接才能繼續工作。</span><span class="sxs-lookup"><span data-stu-id="6102a-107">If a SqlClient application is connected to an AlwaysOn database that fails over, the original connection is broken and the application must open a new connection to continue work after the failover.</span></span>  
  
 <span data-ttu-id="6102a-108">如果您不是連接到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集實例, 而且如果有多個 IP 位址與主機名稱相關聯, SqlClient 會依序逐一查看所有與 DNS 專案相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6102a-108">If you are not connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, and if multiple IP addresses are associated with a hostname, SqlClient will iterate sequentially through all IP addresses associated with DNS entry.</span></span> <span data-ttu-id="6102a-109">如果 DNS 傳回的第一個 IP 位址未繫結至任何網路介面卡 (NIC)，可能會很耗時。</span><span class="sxs-lookup"><span data-stu-id="6102a-109">This can be time consuming if the first IP address returned by DNS server is not bound to any network interface card (NIC).</span></span> <span data-ttu-id="6102a-110">當連接到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集實例時, SqlClient 會嘗試平行建立與所有 IP 位址的連線, 如果連線嘗試成功, 驅動程式就會捨棄任何暫止的連接機會.</span><span class="sxs-lookup"><span data-stu-id="6102a-110">When connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, SqlClient attempts to establish connections to all IP addresses in parallel and if a connection attempt succeeds, the driver will discard any pending connection attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6102a-111">增加連接逾時和實作連接重試邏輯，可提高應用程式連接到可用性群組的可能性。</span><span class="sxs-lookup"><span data-stu-id="6102a-111">Increasing connection timeout and implementing connection retry logic will increase the probability that an application will connect to an availability group.</span></span> <span data-ttu-id="6102a-112">此外，由於連接可能因為容錯移轉而失敗，因此您應實作連接重試邏輯，重試失敗的連接直到重新連接為止。</span><span class="sxs-lookup"><span data-stu-id="6102a-112">Also, because a connection can fail because of a failover, you should implement connection retry logic, retrying a failed connection until it reconnects.</span></span>  
  
 <span data-ttu-id="6102a-113">下列連接屬性已新增至 .NET Framework 4.5 中的 SqlClient:</span><span class="sxs-lookup"><span data-stu-id="6102a-113">The following connection properties were added to SqlClient in .NET Framework 4.5:</span></span>  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 <span data-ttu-id="6102a-114">您可以利用程式設計方式修改這些連接字串關鍵字：</span><span class="sxs-lookup"><span data-stu-id="6102a-114">You can programmatically modify these connection string keywords with:</span></span>  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> <span data-ttu-id="6102a-115">.NET Framework `MultiSubnetFailover` 4.6.1 `true`或更新版本不需要將設定為。</span><span class="sxs-lookup"><span data-stu-id="6102a-115">Setting `MultiSubnetFailover` to `true` isn't required with .NET Framework 4.6.1 or later versions.</span></span>
  
## <a name="connecting-with-multisubnetfailover"></a><span data-ttu-id="6102a-116">連接 MultiSubnetFailover</span><span class="sxs-lookup"><span data-stu-id="6102a-116">Connecting With MultiSubnetFailover</span></span>  
 <span data-ttu-id="6102a-117">當連接`MultiSubnetFailover=True`到 SQL Server 2012 可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集實例時, 一律指定。</span><span class="sxs-lookup"><span data-stu-id="6102a-117">Always specify `MultiSubnetFailover=True` when connecting to a SQL Server 2012 availability group listener or SQL Server 2012 Failover Cluster Instance.</span></span> <span data-ttu-id="6102a-118">`MultiSubnetFailover`針對 SQL Server 2012 中的所有可用性群組和或容錯移轉叢集實例啟用更快速的容錯移轉, 並大幅縮短單一和多重子網 AlwaysOn 拓撲的容錯移轉時間。</span><span class="sxs-lookup"><span data-stu-id="6102a-118">`MultiSubnetFailover` enables faster failover for all Availability Groups and or Failover Cluster Instance in SQL Server 2012 and will significantly reduce failover time for single and multi-subnet AlwaysOn topologies.</span></span> <span data-ttu-id="6102a-119">在多重子網路容錯移轉時，用戶端將嘗試並行連接。</span><span class="sxs-lookup"><span data-stu-id="6102a-119">During a multi-subnet failover, the client will attempt connections in parallel.</span></span> <span data-ttu-id="6102a-120">子網路容錯移轉期間，將積極重試 TCP 連接。</span><span class="sxs-lookup"><span data-stu-id="6102a-120">During a subnet failover, will aggressively retry the TCP connection.</span></span>  
  
 <span data-ttu-id="6102a-121">`MultiSubnetFailover`連接屬性工作表示應用程式正在可用性群組或 SQL Server 2012 容錯移轉叢集實例中部署, 而且 SqlClient 會嘗試連接到主要 SQL Server 實例上的資料庫, 方法是嘗試連接到所有 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6102a-121">The `MultiSubnetFailover` connection property indicates that the application is being deployed in an availability group or SQL Server 2012 Failover Cluster Instance and that SqlClient will try to connect to the database on the primary SQL Server instance by trying to connect to all the IP addresses.</span></span> <span data-ttu-id="6102a-122">指定連接的 `MultiSubnetFailover=True` 時，用戶端重試 TCP 連接嘗試的速度會比作業系統預設的 TCP 重新傳送間隔更快。</span><span class="sxs-lookup"><span data-stu-id="6102a-122">When `MultiSubnetFailover=True` is specified for a connection, the client retries TCP connection attempts faster than the operating system’s default TCP retransmit intervals.</span></span> <span data-ttu-id="6102a-123">這樣可以在 AlwaysOn 可用性群組或 AlwaysOn 容錯移轉叢集執行個體容錯移轉後更快重新連接，而且適用於單一子網路和多重子網路可用性群組與容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="6102a-123">This enables faster reconnection after failover of either an AlwaysOn Availability Group or an AlwaysOn Failover Cluster Instance, and is applicable to both single- and multi-subnet Availability Groups and Failover Cluster Instances.</span></span>  
  
 <span data-ttu-id="6102a-124">如需 SqlClient 中有關連接字串關鍵字的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="6102a-124">For more information about connection string keywords in SqlClient, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="6102a-125">指定`MultiSubnetFailover=True`連接到可用性群組接聽程式以外的專案或 SQL Server 2012 容錯移轉叢集實例時, 可能會造成負面的效能影響, 而且不受支援。</span><span class="sxs-lookup"><span data-stu-id="6102a-125">Specifying `MultiSubnetFailover=True` when connecting to something other than a availability group listener or SQL Server 2012 Failover Cluster Instance may result in a negative performance impact, and is not supported.</span></span>  
  
 <span data-ttu-id="6102a-126">使用下列指導方針, 連接到可用性群組中的伺服器或 SQL Server 2012 容錯移轉叢集實例:</span><span class="sxs-lookup"><span data-stu-id="6102a-126">Use the following guidelines to connect to a server in an availability group or SQL Server 2012 Failover Cluster Instance:</span></span>  
  
- <span data-ttu-id="6102a-127">連接至單一子網路或多重子網路時，使用 `MultiSubnetFailover` 連接屬性可以提高兩者的效能。</span><span class="sxs-lookup"><span data-stu-id="6102a-127">Use the `MultiSubnetFailover` connection property when connecting to a single subnet or multi-subnet; it will improve performance for both.</span></span>  
  
- <span data-ttu-id="6102a-128">若要連接到可用性群組，請在連接字串中將該可用性群組的可用性群組接聽程式指定為伺服器。</span><span class="sxs-lookup"><span data-stu-id="6102a-128">To connect to an availability group, specify the availability group listener of the availability group as the server in your connection string.</span></span>  
  
- <span data-ttu-id="6102a-129">連接到設定了超過64個 IP 位址的 SQL Server 實例, 將會導致連線失敗。</span><span class="sxs-lookup"><span data-stu-id="6102a-129">Connecting to a SQL Server instance configured with more than 64 IP addresses will cause a connection failure.</span></span>  
  
- <span data-ttu-id="6102a-130">根據驗證類型, 使用`MultiSubnetFailover`連接屬性之應用程式的行為不會受到影響:SQL Server 驗證、Kerberos 驗證或 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="6102a-130">Behavior of an application that uses the `MultiSubnetFailover` connection property is not affected based on the type of authentication: SQL Server Authentication, Kerberos Authentication, or Windows Authentication.</span></span>  
  
- <span data-ttu-id="6102a-131">提高 `Connect Timeout` 的值可延長容錯移轉時間並減少應用程式重試連接的次數。</span><span class="sxs-lookup"><span data-stu-id="6102a-131">Increase the value of `Connect Timeout` to accommodate for failover time and reduce application connection retry attempts.</span></span>  
  
- <span data-ttu-id="6102a-132">不支援分散式異動。</span><span class="sxs-lookup"><span data-stu-id="6102a-132">Distributed transactions are not supported.</span></span>  
  
 <span data-ttu-id="6102a-133">如果唯讀路由沒有作用，在下列情況下連接到次要複本位置會失敗：</span><span class="sxs-lookup"><span data-stu-id="6102a-133">If read-only routing is not in effect, connecting to a secondary replica location will fail in the following situations:</span></span>  
  
1. <span data-ttu-id="6102a-134">如果未將次要複本位置設定為接受連接。</span><span class="sxs-lookup"><span data-stu-id="6102a-134">If the secondary replica location is not configured to accept connections.</span></span>  
  
2. <span data-ttu-id="6102a-135">如果應用程式使用 `ApplicationIntent=ReadWrite` (討論如下)，且次要複本位置設定為唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="6102a-135">If an application uses `ApplicationIntent=ReadWrite` (discussed below) and the secondary replica location is configured for read-only access.</span></span>  
  
 <span data-ttu-id="6102a-136">唯讀次要複本不支援 <xref:System.Data.SqlClient.SqlDependency>。</span><span class="sxs-lookup"><span data-stu-id="6102a-136"><xref:System.Data.SqlClient.SqlDependency> is not supported on read-only secondary replicas.</span></span>  
  
 <span data-ttu-id="6102a-137">如果主要複本設定為拒絕唯讀工作負載，且連接字串包含 `ApplicationIntent=ReadOnly`，連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="6102a-137">A connection will fail if a primary replica is configured to reject read-only workloads and the connection string contains `ApplicationIntent=ReadOnly`.</span></span>  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a><span data-ttu-id="6102a-138">從資料庫鏡像升級以使用多重子網路叢集</span><span class="sxs-lookup"><span data-stu-id="6102a-138">Upgrading to Use Multi-Subnet Clusters from Database Mirroring</span></span>  
 <span data-ttu-id="6102a-139">如果連接字串中出現 <xref:System.ArgumentException> 和 `MultiSubnetFailover` 連接關鍵字，或者使用了 `Failover Partner` 和 TCP 以外的通訊協定，就會發生連接錯誤 (`MultiSubnetFailover=True`)。</span><span class="sxs-lookup"><span data-stu-id="6102a-139">A connection error (<xref:System.ArgumentException>) will occur if the `MultiSubnetFailover` and `Failover Partner` connection keywords are present in the connection string, or if `MultiSubnetFailover=True` and a protocol other than TCP is used.</span></span> <span data-ttu-id="6102a-140"><xref:System.Data.SqlClient.SqlException>如果`MultiSubnetFailover`使用, 而且 SQL Server 傳回容錯移轉夥伴回應, 指出它是資料庫鏡像配對的一部分, 也會發生錯誤 ()。</span><span class="sxs-lookup"><span data-stu-id="6102a-140">An error (<xref:System.Data.SqlClient.SqlException>) will also occur if `MultiSubnetFailover` is used and the SQL Server returns a failover partner response indicating it is part of a database mirroring pair.</span></span>  
  
 <span data-ttu-id="6102a-141">如果將目前使用資料庫鏡像的 SqlClient 應用程式升級至多重子網路案例，您應該移除 `Failover Partner` 連接屬性，並將 `MultiSubnetFailover` 集合設為 `True` 以取代該連接屬性，然後將連接字串中的伺服器名稱取代為可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6102a-141">If you upgrade a SqlClient application that currently uses database mirroring to a multi-subnet scenario, you should remove the `Failover Partner` connection property and replace it with `MultiSubnetFailover` set to `True` and replace the server name in the connection string with an availability group listener.</span></span> <span data-ttu-id="6102a-142">如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=True`，驅動程式將產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6102a-142">If a connection string uses `Failover Partner` and `MultiSubnetFailover=True`, the driver will generate an error.</span></span> <span data-ttu-id="6102a-143">但是，如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=False` (或 `ApplicationIntent=ReadWrite`)，應用程式將使用資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="6102a-143">However, if a connection string uses `Failover Partner` and `MultiSubnetFailover=False` (or `ApplicationIntent=ReadWrite`), the application will use database mirroring.</span></span>  
  
 <span data-ttu-id="6102a-144">如果在 AG 的主要資料庫中使用資料庫鏡像，且若在連接至主要資料庫而非可用性群組接聽程式的連接字串中使用 `MultiSubnetFailover=True`，驅動程式會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="6102a-144">The driver will return an error if database mirroring is used on the primary database in the AG, and if `MultiSubnetFailover=True` is used in the connection string that connects to a primary database instead of to an availability group listener.</span></span>  
  
## <a name="specifying-application-intent"></a><span data-ttu-id="6102a-145">指定應用程式用途</span><span class="sxs-lookup"><span data-stu-id="6102a-145">Specifying Application Intent</span></span>  
 <span data-ttu-id="6102a-146">當 `ApplicationIntent=ReadOnly` 時，用戶端會在連接至啟用 AlwaysOn 的資料庫時要求讀取工作負載。</span><span class="sxs-lookup"><span data-stu-id="6102a-146">When `ApplicationIntent=ReadOnly`, the client requests a read workload when connecting to an AlwaysOn enabled database.</span></span> <span data-ttu-id="6102a-147">伺服器將在連接及 USE 資料庫陳述式時強制該用途，但僅限於啟用 Always On 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6102a-147">The server will enforce the intent at connection time and during a USE database statement but only to an Always On enabled database.</span></span>  
  
 <span data-ttu-id="6102a-148">`ApplicationIntent` 關鍵字不適用於舊式的唯讀資料庫。</span><span class="sxs-lookup"><span data-stu-id="6102a-148">The `ApplicationIntent` keyword does not work with legacy, read-only databases.</span></span>  
  
 <span data-ttu-id="6102a-149">資料庫可以允許或不允許目標 AlwaysOn 資料庫上的讀取工作負載。</span><span class="sxs-lookup"><span data-stu-id="6102a-149">A database can allow or disallow read workloads on the targeted AlwaysOn database.</span></span> <span data-ttu-id="6102a-150">(這是透過`ALLOW_CONNECTIONS` `PRIMARY_ROLE`和`SECONDARY_ROLE`transact-sql 語句的子句來完成)。</span><span class="sxs-lookup"><span data-stu-id="6102a-150">(This is done with the `ALLOW_CONNECTIONS` clause of the `PRIMARY_ROLE` and `SECONDARY_ROLE`Transact-SQL statements.)</span></span>  
  
 <span data-ttu-id="6102a-151">`ApplicationIntent` 關鍵字可用於啟用唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="6102a-151">The `ApplicationIntent` keyword is used to enable read-only routing.</span></span>  
  
## <a name="read-only-routing"></a><span data-ttu-id="6102a-152">唯讀路由</span><span class="sxs-lookup"><span data-stu-id="6102a-152">Read-Only Routing</span></span>  
 <span data-ttu-id="6102a-153">唯讀路由功能可確保唯讀資料庫複本的可用性。</span><span class="sxs-lookup"><span data-stu-id="6102a-153">Read-only routing is a feature that can ensure the availability of a read only replica of a database.</span></span> <span data-ttu-id="6102a-154">若要啟用唯讀路由：</span><span class="sxs-lookup"><span data-stu-id="6102a-154">To enable read-only routing:</span></span>  
  
1. <span data-ttu-id="6102a-155">您必須連接到 AlwaysOn 可用性群組的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6102a-155">You must connect to an Always On Availability Group availability group listener.</span></span>  
  
2. <span data-ttu-id="6102a-156">`ApplicationIntent` 連接字串關鍵字必須設為 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="6102a-156">The `ApplicationIntent` connection string keyword must be set to `ReadOnly`.</span></span>  
  
3. <span data-ttu-id="6102a-157">資料庫管理員必須設定可用性群組以啟用唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="6102a-157">The Availability Group must be configured by the database administrator to enable read-only routing.</span></span>  
  
 <span data-ttu-id="6102a-158">使用唯讀路由的多個連接可能不會全數連接至同一個唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="6102a-158">It is possible that multiple connections using read-only routing will not all connect to the same read-only replica.</span></span> <span data-ttu-id="6102a-159">資料庫同步作業或伺服器路由組態中的變更可能會導致用戶端連接至不同的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="6102a-159">Changes in database synchronization or changes in the server's routing configuration can result in client connections to different read-only replicas.</span></span> <span data-ttu-id="6102a-160">為確保所有唯讀要求能連接到同一個唯讀複本，請勿將可用性群組接聽程式傳送到 `Data Source` 連接字串關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6102a-160">To ensure that all read-only requests connect to the same read-only replica, do not pass an availability group listener to the `Data Source` connection string keyword.</span></span> <span data-ttu-id="6102a-161">相反地，請指定唯讀執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="6102a-161">Instead, specify the name of the read-only instance.</span></span>  
  
 <span data-ttu-id="6102a-162">唯讀路由連接到主要複本的時間較長，因為唯讀路由會先連接到主要複本，再尋找最適合的可讀次要複本。</span><span class="sxs-lookup"><span data-stu-id="6102a-162">Read-only routing may take longer than connecting to the primary because read only routing first connects to the primary and then looks for the best available readable secondary.</span></span> <span data-ttu-id="6102a-163">因此，您應延長登入逾時。</span><span class="sxs-lookup"><span data-stu-id="6102a-163">Because of this, you should increase your login timeout.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6102a-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6102a-164">See also</span></span>

- [<span data-ttu-id="6102a-165">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6102a-165">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [<span data-ttu-id="6102a-166">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6102a-166">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
