---
title: 在 SQL Server 中建立資料庫鏡像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 81e8bd5ba9274c84ffe18f617978b61238ebeff2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782438"
---
# <a name="database-mirroring-in-sql-server"></a><span data-ttu-id="71592-102">在 SQL Server 中建立資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="71592-102">Database Mirroring in SQL Server</span></span>
<span data-ttu-id="71592-103">SQL Server 中的資料庫鏡像可讓您將 SQL Server 資料庫的複本或鏡像保存在待命伺服器上。</span><span class="sxs-lookup"><span data-stu-id="71592-103">Database mirroring in SQL Server allows you to keep a copy, or mirror, of a SQL Server database on a standby server.</span></span> <span data-ttu-id="71592-104">鏡像可確保永遠存在兩份分開的資料複本，這會提供高可用性及完整的資料重複性。</span><span class="sxs-lookup"><span data-stu-id="71592-104">Mirroring ensures that two separate copies of the data exist at all times, providing high availability and complete data redundancy.</span></span> <span data-ttu-id="71592-105">.NET Data Provider for SQL Server 提供對資料庫鏡像的隱含支援，這樣將其設定給 SQL Server 資料庫後，開發人員即無需採取任何動作或撰寫任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="71592-105">The .NET Data Provider for SQL Server provides implicit support for database mirroring, so that the developer does not need to take any action or write any code once it has been configured for a SQL Server database.</span></span> <span data-ttu-id="71592-106">此外，<xref:System.Data.SqlClient.SqlConnection> 物件支援明確連接模式，可在 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 中提供容錯移轉夥伴伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="71592-106">In addition, the <xref:System.Data.SqlClient.SqlConnection> object supports an explicit connection mode that allows supplying the name of a failover partner server in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="71592-107">下列簡化的事件序列會針對目標鎖定設定為鏡像之資料庫的 <xref:System.Data.SqlClient.SqlConnection> 物件發生：</span><span class="sxs-lookup"><span data-stu-id="71592-107">The following simplified sequence of events occurs for a <xref:System.Data.SqlClient.SqlConnection> object that targets a database configured for mirroring:</span></span>  
  
1. <span data-ttu-id="71592-108">用戶端應用程式成功連接至主體資料庫，伺服器再傳送回夥伴伺服器的名稱，稍後會在用戶端上快取該名稱。</span><span class="sxs-lookup"><span data-stu-id="71592-108">The client application successfully connects to the principal database, and the server sends back the name of the partner server, which is then cached on the client.</span></span>  
  
2. <span data-ttu-id="71592-109">如果包含主體資料庫的伺服器失敗或連接中斷，則會遺失連接及異動狀態。</span><span class="sxs-lookup"><span data-stu-id="71592-109">If the server containing the principal database fails or connectivity is interrupted, connection and transaction state is lost.</span></span> <span data-ttu-id="71592-110">用戶端應用程式會嘗試重新建立與主體資料庫的連接，但失敗。</span><span class="sxs-lookup"><span data-stu-id="71592-110">The client application attempts to re-establish a connection to the principal database and fails.</span></span>  
  
3. <span data-ttu-id="71592-111">然後，用戶端應用程式會透明地嘗試建立與夥伴伺服器上鏡像資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="71592-111">The client application then transparently attempts to establish a connection to the mirror database on the partner server.</span></span> <span data-ttu-id="71592-112">如果成功，則連接會重新導向至稍後會變成新主體資料庫的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="71592-112">If it succeeds, the connection is redirected to the mirror database, which then becomes the new principal database.</span></span>  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a><span data-ttu-id="71592-113">在連接字串中指定容錯移轉夥伴</span><span class="sxs-lookup"><span data-stu-id="71592-113">Specifying the Failover Partner in the Connection String</span></span>  
 <span data-ttu-id="71592-114">如果您在連接字串 (Connection String) 中提供了容錯移轉夥伴伺服器的名稱，只要用戶端應用程式第一次連接時主體資料庫無法使用，用戶端就會透明地嘗試與容錯移轉夥伴連接。</span><span class="sxs-lookup"><span data-stu-id="71592-114">If you supply the name of a failover partner server in the connection string, the client will transparently attempt a connection with the failover partner if the principal database is unavailable when the client application first connects.</span></span>  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 <span data-ttu-id="71592-115">如果您省略了容錯移轉夥伴伺服器的名稱，而且用戶端應用程式第一次連接時主體資料庫無法使用，就會引發 <xref:System.Data.SqlClient.SqlException>。</span><span class="sxs-lookup"><span data-stu-id="71592-115">If you omit the name of the failover partner server and the principal database is unavailable when the client application first connects then a <xref:System.Data.SqlClient.SqlException> is raised.</span></span>  
  
 <span data-ttu-id="71592-116">成功開啟 <xref:System.Data.SqlClient.SqlConnection> 時，伺服器就會傳回容錯移轉夥伴名稱，並且取代連接字串中提供的任何值。</span><span class="sxs-lookup"><span data-stu-id="71592-116">When a <xref:System.Data.SqlClient.SqlConnection> is successfully opened, the failover partner name is returned by the server and supersedes any values supplied in the connection string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71592-117">在資料庫鏡像案例中，您必須在連接字串中明確指定初始資料庫目錄和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="71592-117">You must explicitly specify the initial catalog or database name in the connection string for database mirroring scenarios.</span></span> <span data-ttu-id="71592-118">如果用戶端在沒有明確指定初始資料庫目錄或資料庫的連接上收到容錯移轉資訊，則不會快取該容錯移轉資訊，而且應用程式在主體伺服器失敗時不會嘗試容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="71592-118">If the client receives failover information on a connection that doesn't have an explicitly specified initial catalog or database, the failover information is not cached and the application does not attempt to fail over if the principal server fails.</span></span> <span data-ttu-id="71592-119">如果連接字串具有容錯移轉夥伴的值，但是沒有初始資料庫目錄或資料庫的值，就會引發 `InvalidArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="71592-119">If a connection string has a value for the failover partner, but no value for the initial catalog or database, an `InvalidArgumentException` is raised.</span></span>  
  
## <a name="retrieving-the-current-server-name"></a><span data-ttu-id="71592-120">擷取目前的伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="71592-120">Retrieving the Current Server Name</span></span>  
 <span data-ttu-id="71592-121">在容錯移轉時，您可藉由使用 <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性，擷取目前連接實際連接的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="71592-121">In the event of a failover, you can retrieve the name of the server to which the current connection is actually connected by using the <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="71592-122">下列程式碼片段會擷取作用中伺服器的名稱，並假設連接變數參考開啟的 <xref:System.Data.SqlClient.SqlConnection>。</span><span class="sxs-lookup"><span data-stu-id="71592-122">The following code fragment retrieves the name of the active server, assuming that the connection variable references an open <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
 <span data-ttu-id="71592-123">當發生容錯移轉事件且連接切換到鏡像伺服器時，會更新**DataSource**屬性以反映鏡像名稱。</span><span class="sxs-lookup"><span data-stu-id="71592-123">When a failover event occurs and the connection is switched to the mirror server, the **DataSource** property is updated to reflect the mirror name.</span></span>  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a><span data-ttu-id="71592-124">SqlClient 鏡像行為</span><span class="sxs-lookup"><span data-stu-id="71592-124">SqlClient Mirroring Behavior</span></span>  
 <span data-ttu-id="71592-125">用戶端會永遠嘗試連接至目前的主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="71592-125">The client always tries to connect to the current principal server.</span></span> <span data-ttu-id="71592-126">如果連接失敗，則會嘗試容錯移轉夥伴。</span><span class="sxs-lookup"><span data-stu-id="71592-126">If it fails, it tries the failover partner.</span></span> <span data-ttu-id="71592-127">如果鏡像資料庫已切換至夥伴伺服器上的主體角色，則連接成功，並在呼叫 <xref:System.AppDomain> 的存留期內，將新主體鏡像對應傳送至用戶端並快取它。</span><span class="sxs-lookup"><span data-stu-id="71592-127">If the mirror database has already been switched to the principal role on the partner server, the connection succeeds and the new principal-mirror mapping is sent to the client and cached for the lifetime of the calling <xref:System.AppDomain>.</span></span> <span data-ttu-id="71592-128">它不會儲存在持續性儲存體中，而且無法在不同**AppDomain**或進程中的後續連接使用。</span><span class="sxs-lookup"><span data-stu-id="71592-128">It is not stored in persistent storage and is not available for subsequent connections in a different **AppDomain** or process.</span></span> <span data-ttu-id="71592-129">不過，它可以用於相同**AppDomain**內的後續連接。</span><span class="sxs-lookup"><span data-stu-id="71592-129">However, it is available for subsequent connections within the same **AppDomain**.</span></span> <span data-ttu-id="71592-130">請注意，在相同或不同電腦上執行的另一個**AppDomain**或進程，一律會有其連線集區，而且不會重設這些連接。</span><span class="sxs-lookup"><span data-stu-id="71592-130">Note that another **AppDomain** or process running on the same or a different computer always has its pool of connections, and those connections are not reset.</span></span> <span data-ttu-id="71592-131">在此情況下，如果主資料庫停止運作，則每個進程或**AppDomain**都會失敗一次，而且會自動清除集區。</span><span class="sxs-lookup"><span data-stu-id="71592-131">In that case, if the primary database goes down, each process or **AppDomain** fails once, and the pool is automatically cleared.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71592-132">會在每個資料庫上設定伺服器上的鏡像支援。</span><span class="sxs-lookup"><span data-stu-id="71592-132">Mirroring support on the server is configured on a per-database basis.</span></span> <span data-ttu-id="71592-133">如果藉由使用多個名稱或變更目前的資料庫，針對主體/鏡像組中不包括的其他資料庫執行資料管理作業，則在失敗時，不會傳播對這些資料庫所做的變更。</span><span class="sxs-lookup"><span data-stu-id="71592-133">If data manipulation operations are executed against other databases not included in the principal/mirror set, either by using multipart names or by changing the current database, the changes to these other databases do not propagate in the event of failure.</span></span> <span data-ttu-id="71592-134">當在未鏡像的資料庫中修改資料時，不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="71592-134">No error is generated when data is modified in a database that is not mirrored.</span></span> <span data-ttu-id="71592-135">開發人員必須評估此類作業可能會產生的影響。</span><span class="sxs-lookup"><span data-stu-id="71592-135">The developer must evaluate the possible impact of such operations.</span></span>  
  
## <a name="database-mirroring-resources"></a><span data-ttu-id="71592-136">資料庫鏡像資源</span><span class="sxs-lookup"><span data-stu-id="71592-136">Database Mirroring Resources</span></span>  
 <span data-ttu-id="71592-137">如需有關設定、部署和管理鏡像的概念檔和資訊，請參閱 SQL Server 檔中的下列資源。</span><span class="sxs-lookup"><span data-stu-id="71592-137">For conceptual documentation and information on configuring, deploying and administering mirroring, see the following resources in SQL Server documentation.</span></span>  
  
|<span data-ttu-id="71592-138">Resource</span><span class="sxs-lookup"><span data-stu-id="71592-138">Resource</span></span>|<span data-ttu-id="71592-139">描述</span><span class="sxs-lookup"><span data-stu-id="71592-139">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="71592-140">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="71592-140">Database Mirroring</span></span>](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|<span data-ttu-id="71592-141">說明如何在 SQL Server 中設定鏡像。</span><span class="sxs-lookup"><span data-stu-id="71592-141">Describes how to set up and configure mirroring in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71592-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71592-142">See also</span></span>

- [<span data-ttu-id="71592-143">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="71592-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
