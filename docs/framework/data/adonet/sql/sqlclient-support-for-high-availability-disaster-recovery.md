---
title: 高可用性、嚴重損壞修復的 SqlClient 支援
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 40054378319b81113dcb8f40cb82a8b1d02fc594
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307588"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="1bd5e-102">高可用性、嚴重損壞修復的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="1bd5e-102">SqlClient Support for High Availability, Disaster Recovery</span></span>
<span data-ttu-id="1bd5e-103">本主題討論高可用性、嚴重損壞修復 (AlwaysOn 可用性群組) 的 SqlClient 支援 (在 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 中新增)。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-103">This topic discusses SqlClient support (added in [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]) for high-availability, disaster recovery -- AlwaysOn Availability Groups.</span></span>  <span data-ttu-id="1bd5e-104">AlwaysOn 可用性群組功能已新增至 SQL Server 2012。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-104">AlwaysOn Availability Groups feature was added to SQL Server 2012.</span></span> <span data-ttu-id="1bd5e-105">如需 AlwaysOn 可用性群組的詳細資訊，請參閱 SQL Server 線上叢書 》。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-105">For more information about AlwaysOn Availability Groups, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="1bd5e-106">您現在可以指定的可用性群組接聽程式 （高可用性、 災害復原） 可用性群組 (AG) 或 SQL Server 2012 容錯移轉叢集執行個體的連接屬性中。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-106">You can now specify the availability group listener of a (high-availability, disaster-recovery) availability group (AG) or SQL Server 2012 Failover Cluster Instance in the connection property.</span></span> <span data-ttu-id="1bd5e-107">如果 SqlClient 應用程式連接到容錯移轉的 AlwaysOn 資料庫，原始連接會中斷。容錯移轉之後，應用程式必須開啟新的連接才能繼續工作。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-107">If a SqlClient application is connected to an AlwaysOn database that fails over, the original connection is broken and the application must open a new connection to continue work after the failover.</span></span>  
  
 <span data-ttu-id="1bd5e-108">如果您未連接到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體，而且如果多個 IP 位址與主機名稱相關聯，SqlClient 會依序逐一 DNS 項目相關聯的所有 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-108">If you are not connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, and if multiple IP addresses are associated with a hostname, SqlClient will iterate sequentially through all IP addresses associated with DNS entry.</span></span> <span data-ttu-id="1bd5e-109">如果 DNS 傳回的第一個 IP 位址未繫結至任何網路介面卡 (NIC)，可能會很耗時。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-109">This can be time consuming if the first IP address returned by DNS server is not bound to any network interface card (NIC).</span></span> <span data-ttu-id="1bd5e-110">連接到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體時，SqlClient 會嘗試平行建立所有的 IP 位址和連接嘗試成功，如果驅動程式將會捨棄任何暫止的連接嘗試。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-110">When connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, SqlClient attempts to establish connections to all IP addresses in parallel and if a connection attempt succeeds, the driver will discard any pending connection attempts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bd5e-111">增加連接逾時和實作連接重試邏輯，可提高應用程式連接到可用性群組的可能性。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-111">Increasing connection timeout and implementing connection retry logic will increase the probability that an application will connect to an availability group.</span></span> <span data-ttu-id="1bd5e-112">此外，由於連接可能因為容錯移轉而失敗，因此您應實作連接重試邏輯，重試失敗的連接直到重新連接為止。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-112">Also, because a connection can fail because of a failover, you should implement connection retry logic, retrying a failed connection until it reconnects.</span></span>  
  
 <span data-ttu-id="1bd5e-113">[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 中的 SqlClient 新增了下列連接屬性：</span><span class="sxs-lookup"><span data-stu-id="1bd5e-113">The following connection properties were added to SqlClient in [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]:</span></span>  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 <span data-ttu-id="1bd5e-114">您可以利用程式設計方式修改這些連接字串關鍵字：</span><span class="sxs-lookup"><span data-stu-id="1bd5e-114">You can programmatically modify these connection string keywords with:</span></span>  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  <span data-ttu-id="1bd5e-115">設定`MultiSubnetFailover`要`true`所以不需要[!INCLUDE[net_v461](../../../../../includes/net-v461-md.md)]或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-115">Setting `MultiSubnetFailover` to `true` isn't required with [!INCLUDE[net_v461](../../../../../includes/net-v461-md.md)] or later versions.</span></span>
  
## <a name="connecting-with-multisubnetfailover"></a><span data-ttu-id="1bd5e-116">連接 MultiSubnetFailover</span><span class="sxs-lookup"><span data-stu-id="1bd5e-116">Connecting With MultiSubnetFailover</span></span>  
 <span data-ttu-id="1bd5e-117">一定要指定`MultiSubnetFailover=True`連接到 SQL Server 2012 可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體時。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-117">Always specify `MultiSubnetFailover=True` when connecting to a SQL Server 2012 availability group listener or SQL Server 2012 Failover Cluster Instance.</span></span> <span data-ttu-id="1bd5e-118">`MultiSubnetFailover` 啟用所有可用性群組，或容錯移轉叢集執行個體，在 SQL Server 2012 和會大幅減少單一和多重子網路 AlwaysOn 拓撲的容錯移轉時間更快的容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-118">`MultiSubnetFailover` enables faster failover for all Availability Groups and or Failover Cluster Instance in SQL Server 2012 and will significantly reduce failover time for single and multi-subnet AlwaysOn topologies.</span></span> <span data-ttu-id="1bd5e-119">在多重子網路容錯移轉時，用戶端將嘗試並行連接。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-119">During a multi-subnet failover, the client will attempt connections in parallel.</span></span> <span data-ttu-id="1bd5e-120">子網路容錯移轉期間，將積極重試 TCP 連接。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-120">During a subnet failover, will aggressively retry the TCP connection.</span></span>  
  
 <span data-ttu-id="1bd5e-121">`MultiSubnetFailover`連接屬性表示，應用程式正在可用性群組或 SQL Server 2012 容錯移轉叢集執行個體中部署和 SqlClient 會嘗試透過嘗試連接到主要的 SQL Server 執行個體上的資料庫連接到所有 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-121">The `MultiSubnetFailover` connection property indicates that the application is being deployed in an availability group or SQL Server 2012 Failover Cluster Instance and that SqlClient will try to connect to the database on the primary SQL Server instance by trying to connect to all the IP addresses.</span></span> <span data-ttu-id="1bd5e-122">指定連接的 `MultiSubnetFailover=True` 時，用戶端重試 TCP 連接嘗試的速度會比作業系統預設的 TCP 重新傳送間隔更快。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-122">When `MultiSubnetFailover=True` is specified for a connection, the client retries TCP connection attempts faster than the operating system’s default TCP retransmit intervals.</span></span> <span data-ttu-id="1bd5e-123">這樣可以在 AlwaysOn 可用性群組或 AlwaysOn 容錯移轉叢集執行個體容錯移轉後更快重新連接，而且適用於單一子網路和多重子網路可用性群組與容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-123">This enables faster reconnection after failover of either an AlwaysOn Availability Group or an AlwaysOn Failover Cluster Instance, and is applicable to both single- and multi-subnet Availability Groups and Failover Cluster Instances.</span></span>  
  
 <span data-ttu-id="1bd5e-124">如需 SqlClient 中有關連接字串關鍵字的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-124">For more information about connection string keywords in SqlClient, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="1bd5e-125">指定`MultiSubnetFailover=True`當連接到的項目以外的可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集執行個體可能會導致負面效能影響，並不支援。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-125">Specifying `MultiSubnetFailover=True` when connecting to something other than a availability group listener or SQL Server 2012 Failover Cluster Instance may result in a negative performance impact, and is not supported.</span></span>  
  
 <span data-ttu-id="1bd5e-126">您可以使用下列指導方針，連接到可用性群組中的伺服器或 SQL Server 2012 容錯移轉叢集執行個體：</span><span class="sxs-lookup"><span data-stu-id="1bd5e-126">Use the following guidelines to connect to a server in an availability group or SQL Server 2012 Failover Cluster Instance:</span></span>  
  
-   <span data-ttu-id="1bd5e-127">連接至單一子網路或多重子網路時，使用 `MultiSubnetFailover` 連接屬性可以提高兩者的效能。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-127">Use the `MultiSubnetFailover` connection property when connecting to a single subnet or multi-subnet; it will improve performance for both.</span></span>  
  
-   <span data-ttu-id="1bd5e-128">若要連接到可用性群組，請在連接字串中將該可用性群組的可用性群組接聽程式指定為伺服器。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-128">To connect to an availability group, specify the availability group listener of the availability group as the server in your connection string.</span></span>  
  
-   <span data-ttu-id="1bd5e-129">連接到 SQL Server 使用超過 64 個 IP 位址設定的執行個體，將會導致連接失敗。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-129">Connecting to a SQL Server instance configured with more than 64 IP addresses will cause a connection failure.</span></span>  
  
-   <span data-ttu-id="1bd5e-130">使用的應用程式的行為`MultiSubnetFailover`連接屬性不會影響基礎的驗證類型：SQL Server 驗證、 Kerberos 驗證或 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-130">Behavior of an application that uses the `MultiSubnetFailover` connection property is not affected based on the type of authentication: SQL Server Authentication, Kerberos Authentication, or Windows Authentication.</span></span>  
  
-   <span data-ttu-id="1bd5e-131">提高 `Connect Timeout` 的值可延長容錯移轉時間並減少應用程式重試連接的次數。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-131">Increase the value of `Connect Timeout` to accommodate for failover time and reduce application connection retry attempts.</span></span>  
  
-   <span data-ttu-id="1bd5e-132">不支援分散式異動。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-132">Distributed transactions are not supported.</span></span>  
  
 <span data-ttu-id="1bd5e-133">如果唯讀路由沒有作用，在下列情況下連接到次要複本位置會失敗：</span><span class="sxs-lookup"><span data-stu-id="1bd5e-133">If read-only routing is not in effect, connecting to a secondary replica location will fail in the following situations:</span></span>  
  
1. <span data-ttu-id="1bd5e-134">如果未將次要複本位置設定為接受連接。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-134">If the secondary replica location is not configured to accept connections.</span></span>  
  
2. <span data-ttu-id="1bd5e-135">如果應用程式使用 `ApplicationIntent=ReadWrite` (討論如下)，且次要複本位置設定為唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-135">If an application uses `ApplicationIntent=ReadWrite` (discussed below) and the secondary replica location is configured for read-only access.</span></span>  
  
 <span data-ttu-id="1bd5e-136">唯讀次要複本不支援 <xref:System.Data.SqlClient.SqlDependency>。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-136"><xref:System.Data.SqlClient.SqlDependency> is not supported on read-only secondary replicas.</span></span>  
  
 <span data-ttu-id="1bd5e-137">如果主要複本設定為拒絕唯讀工作負載，且連接字串包含 `ApplicationIntent=ReadOnly`，連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-137">A connection will fail if a primary replica is configured to reject read-only workloads and the connection string contains `ApplicationIntent=ReadOnly`.</span></span>  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a><span data-ttu-id="1bd5e-138">從資料庫鏡像升級以使用多重子網路叢集</span><span class="sxs-lookup"><span data-stu-id="1bd5e-138">Upgrading to Use Multi-Subnet Clusters from Database Mirroring</span></span>  
 <span data-ttu-id="1bd5e-139">如果連接字串中出現 <xref:System.ArgumentException> 和 `MultiSubnetFailover` 連接關鍵字，或者使用了 `Failover Partner` 和 TCP 以外的通訊協定，就會發生連接錯誤 (`MultiSubnetFailover=True`)。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-139">A connection error (<xref:System.ArgumentException>) will occur if the `MultiSubnetFailover` and `Failover Partner` connection keywords are present in the connection string, or if `MultiSubnetFailover=True` and a protocol other than TCP is used.</span></span> <span data-ttu-id="1bd5e-140">錯誤 (<xref:System.Data.SqlClient.SqlException>) 也會發生，如果`MultiSubnetFailover`會使用與 SQL Server 傳回容錯移轉夥伴回應，指出它資料庫鏡像配對的一部分。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-140">An error (<xref:System.Data.SqlClient.SqlException>) will also occur if `MultiSubnetFailover` is used and the SQL Server returns a failover partner response indicating it is part of a database mirroring pair.</span></span>  
  
 <span data-ttu-id="1bd5e-141">如果將目前使用資料庫鏡像的 SqlClient 應用程式升級至多重子網路案例，您應該移除 `Failover Partner` 連接屬性，並將 `MultiSubnetFailover` 集合設為 `True` 以取代該連接屬性，然後將連接字串中的伺服器名稱取代為可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-141">If you upgrade a SqlClient application that currently uses database mirroring to a multi-subnet scenario, you should remove the `Failover Partner` connection property and replace it with `MultiSubnetFailover` set to `True` and replace the server name in the connection string with an availability group listener.</span></span> <span data-ttu-id="1bd5e-142">如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=True`，驅動程式將產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-142">If a connection string uses `Failover Partner` and `MultiSubnetFailover=True`, the driver will generate an error.</span></span> <span data-ttu-id="1bd5e-143">但是，如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=False` (或 `ApplicationIntent=ReadWrite`)，應用程式將使用資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-143">However, if a connection string uses `Failover Partner` and `MultiSubnetFailover=False` (or `ApplicationIntent=ReadWrite`), the application will use database mirroring.</span></span>  
  
 <span data-ttu-id="1bd5e-144">如果在 AG 的主要資料庫中使用資料庫鏡像，且若在連接至主要資料庫而非可用性群組接聽程式的連接字串中使用 `MultiSubnetFailover=True`，驅動程式會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-144">The driver will return an error if database mirroring is used on the primary database in the AG, and if `MultiSubnetFailover=True` is used in the connection string that connects to a primary database instead of to an availability group listener.</span></span>  
  
## <a name="specifying-application-intent"></a><span data-ttu-id="1bd5e-145">指定應用程式用途</span><span class="sxs-lookup"><span data-stu-id="1bd5e-145">Specifying Application Intent</span></span>  
 <span data-ttu-id="1bd5e-146">當 `ApplicationIntent=ReadOnly` 時，用戶端會在連接至啟用 AlwaysOn 的資料庫時要求讀取工作負載。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-146">When `ApplicationIntent=ReadOnly`, the client requests a read workload when connecting to an AlwaysOn enabled database.</span></span> <span data-ttu-id="1bd5e-147">伺服器將在連接及 USE 資料庫陳述式時強制該用途，但僅限於啟用 Always On 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-147">The server will enforce the intent at connection time and during a USE database statement but only to an Always On enabled database.</span></span>  
  
 <span data-ttu-id="1bd5e-148">`ApplicationIntent` 關鍵字不適用於舊式的唯讀資料庫。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-148">The `ApplicationIntent` keyword does not work with legacy, read-only databases.</span></span>  
  
 <span data-ttu-id="1bd5e-149">資料庫可以允許或不允許目標 AlwaysOn 資料庫上的讀取工作負載。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-149">A database can allow or disallow read workloads on the targeted AlwaysOn database.</span></span> <span data-ttu-id="1bd5e-150">(此作業會透過 `ALLOW_CONNECTIONS` 和 `PRIMARY_ROLE``SECONDARY_ROLE` 陳述式的 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 子句來完成)。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-150">(This is done with the `ALLOW_CONNECTIONS` clause of the `PRIMARY_ROLE` and `SECONDARY_ROLE`[!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements.)</span></span>  
  
 <span data-ttu-id="1bd5e-151">`ApplicationIntent` 關鍵字可用於啟用唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-151">The `ApplicationIntent` keyword is used to enable read-only routing.</span></span>  
  
## <a name="read-only-routing"></a><span data-ttu-id="1bd5e-152">唯讀路由</span><span class="sxs-lookup"><span data-stu-id="1bd5e-152">Read-Only Routing</span></span>  
 <span data-ttu-id="1bd5e-153">唯讀路由功能可確保唯讀資料庫複本的可用性。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-153">Read-only routing is a feature that can ensure the availability of a read only replica of a database.</span></span> <span data-ttu-id="1bd5e-154">若要啟用唯讀路由：</span><span class="sxs-lookup"><span data-stu-id="1bd5e-154">To enable read-only routing:</span></span>  
  
1. <span data-ttu-id="1bd5e-155">您必須連接到 AlwaysOn 可用性群組的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-155">You must connect to an Always On Availability Group availability group listener.</span></span>  
  
2. <span data-ttu-id="1bd5e-156">`ApplicationIntent` 連接字串關鍵字必須設為 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-156">The `ApplicationIntent` connection string keyword must be set to `ReadOnly`.</span></span>  
  
3. <span data-ttu-id="1bd5e-157">資料庫管理員必須設定可用性群組以啟用唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-157">The Availability Group must be configured by the database administrator to enable read-only routing.</span></span>  
  
 <span data-ttu-id="1bd5e-158">使用唯讀路由的多個連接可能不會全數連接至同一個唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-158">It is possible that multiple connections using read-only routing will not all connect to the same read-only replica.</span></span> <span data-ttu-id="1bd5e-159">資料庫同步作業或伺服器路由組態中的變更可能會導致用戶端連接至不同的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-159">Changes in database synchronization or changes in the server's routing configuration can result in client connections to different read-only replicas.</span></span> <span data-ttu-id="1bd5e-160">為確保所有唯讀要求能連接到同一個唯讀複本，請勿將可用性群組接聽程式傳送到 `Data Source` 連接字串關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-160">To ensure that all read-only requests connect to the same read-only replica, do not pass an availability group listener to the `Data Source` connection string keyword.</span></span> <span data-ttu-id="1bd5e-161">相反地，請指定唯讀執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-161">Instead, specify the name of the read-only instance.</span></span>  
  
 <span data-ttu-id="1bd5e-162">唯讀路由連接到主要複本的時間較長，因為唯讀路由會先連接到主要複本，再尋找最適合的可讀次要複本。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-162">Read-only routing may take longer than connecting to the primary because read only routing first connects to the primary and then looks for the best available readable secondary.</span></span> <span data-ttu-id="1bd5e-163">因此，您應延長登入逾時。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-163">Because of this, you should increase your login timeout.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd5e-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bd5e-164">See also</span></span>

- [<span data-ttu-id="1bd5e-165">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1bd5e-165">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [<span data-ttu-id="1bd5e-166">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1bd5e-166">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
