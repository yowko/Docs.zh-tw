---
title: 在 SQL Server 中建立資料庫鏡像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 7e2c1c8ea1cbc1bb22452b9ef9d1f250c96118ea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173532"
---
# <a name="database-mirroring-in-sql-server"></a><span data-ttu-id="d9aba-102">在 SQL Server 中建立資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="d9aba-102">Database Mirroring in SQL Server</span></span>

<span data-ttu-id="d9aba-103">SQL Server 中的資料庫鏡像可讓您將 SQL Server 資料庫的複本或鏡像保存在待命伺服器上。</span><span class="sxs-lookup"><span data-stu-id="d9aba-103">Database mirroring in SQL Server allows you to keep a copy, or mirror, of a SQL Server database on a standby server.</span></span> <span data-ttu-id="d9aba-104">鏡像可確保隨時都有兩個個別的資料複本，進而提供高可用性與完整的資料備援能力。</span><span class="sxs-lookup"><span data-stu-id="d9aba-104">Mirroring ensures that two separate copies of the data exist at all times, providing high availability and complete data redundancy.</span></span> <span data-ttu-id="d9aba-105">.NET Data Provider for SQL Server 提供對資料庫鏡像的隱含支援，這樣將其設定給 SQL Server 資料庫後，開發人員即無需採取任何動作或撰寫任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="d9aba-105">The .NET Data Provider for SQL Server provides implicit support for database mirroring, so that the developer does not need to take any action or write any code once it has been configured for a SQL Server database.</span></span> <span data-ttu-id="d9aba-106">此外，<xref:System.Data.SqlClient.SqlConnection> 物件支援可在 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 中提供容錯移轉夥伴伺服器名稱的明確連線模式。</span><span class="sxs-lookup"><span data-stu-id="d9aba-106">In addition, the <xref:System.Data.SqlClient.SqlConnection> object supports an explicit connection mode that allows supplying the name of a failover partner server in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="d9aba-107">下列簡化的事件順序會針對 <xref:System.Data.SqlClient.SqlConnection> 物件發生，此物件會以設定為用於鏡像的資料庫作為目標：</span><span class="sxs-lookup"><span data-stu-id="d9aba-107">The following simplified sequence of events occurs for a <xref:System.Data.SqlClient.SqlConnection> object that targets a database configured for mirroring:</span></span>  
  
1. <span data-ttu-id="d9aba-108">用戶端應用程式成功連線到主體資料庫，而伺服器會傳回夥伴伺服器的名稱，接著夥伴伺服器名稱會在用戶端上快取。</span><span class="sxs-lookup"><span data-stu-id="d9aba-108">The client application successfully connects to the principal database, and the server sends back the name of the partner server, which is then cached on the client.</span></span>  
  
2. <span data-ttu-id="d9aba-109">如果包含主體資料庫的伺服器失敗或連線中斷，連線和交易狀態就會遺失。</span><span class="sxs-lookup"><span data-stu-id="d9aba-109">If the server containing the principal database fails or connectivity is interrupted, connection and transaction state is lost.</span></span> <span data-ttu-id="d9aba-110">用戶端應用程式嘗試重新建立與主體資料庫的連線，但失敗。</span><span class="sxs-lookup"><span data-stu-id="d9aba-110">The client application attempts to re-establish a connection to the principal database and fails.</span></span>  
  
3. <span data-ttu-id="d9aba-111">然後，用戶端應用程式會以透明方式，嘗試建立與夥伴伺服器上鏡像資料庫的連線。</span><span class="sxs-lookup"><span data-stu-id="d9aba-111">The client application then transparently attempts to establish a connection to the mirror database on the partner server.</span></span> <span data-ttu-id="d9aba-112">如果成功，會將連線重新導向至鏡像資料庫，接著鏡像資料庫會成為新的主體資料庫。</span><span class="sxs-lookup"><span data-stu-id="d9aba-112">If it succeeds, the connection is redirected to the mirror database, which then becomes the new principal database.</span></span>  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a><span data-ttu-id="d9aba-113">在連接字串中指定容錯移轉夥伴</span><span class="sxs-lookup"><span data-stu-id="d9aba-113">Specifying the Failover Partner in the Connection String</span></span>  

 <span data-ttu-id="d9aba-114">如果您在連接字串中提供容錯移轉夥伴伺服器的名稱，當用戶端應用程式第一次連接時，如果主體資料庫無法使用，用戶端將會以透明方式嘗試與容錯移轉夥伴連線。</span><span class="sxs-lookup"><span data-stu-id="d9aba-114">If you supply the name of a failover partner server in the connection string, the client will transparently attempt a connection with the failover partner if the principal database is unavailable when the client application first connects.</span></span>  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 <span data-ttu-id="d9aba-115">如果您省略容錯移轉夥伴伺服器的名稱，而且當用戶端應用程式第一次連線時主體資料庫無法使用，則會引發 <xref:System.Data.SqlClient.SqlException>。</span><span class="sxs-lookup"><span data-stu-id="d9aba-115">If you omit the name of the failover partner server and the principal database is unavailable when the client application first connects then a <xref:System.Data.SqlClient.SqlException> is raised.</span></span>  
  
 <span data-ttu-id="d9aba-116">成功開啟 <xref:System.Data.SqlClient.SqlConnection> 之後，伺服器就會傳回容錯移轉夥伴名稱，並取代連接字串中提供的任何值。</span><span class="sxs-lookup"><span data-stu-id="d9aba-116">When a <xref:System.Data.SqlClient.SqlConnection> is successfully opened, the failover partner name is returned by the server and supersedes any values supplied in the connection string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9aba-117">您必須在資料庫鏡像案例的連接字串中，明確指定初始目錄或資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d9aba-117">You must explicitly specify the initial catalog or database name in the connection string for database mirroring scenarios.</span></span> <span data-ttu-id="d9aba-118">如果用戶端在沒有明確指定初始目錄或資料庫的連線上收到容錯移轉資訊，則不會快取該容錯移轉資訊，且應用程式在主體伺服器失敗時不會嘗試容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="d9aba-118">If the client receives failover information on a connection that doesn't have an explicitly specified initial catalog or database, the failover information is not cached and the application does not attempt to fail over if the principal server fails.</span></span> <span data-ttu-id="d9aba-119">如果連接字串內含容錯移轉夥伴的值，但是沒有初始目錄或資料庫的值，就會引發 `InvalidArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="d9aba-119">If a connection string has a value for the failover partner, but no value for the initial catalog or database, an `InvalidArgumentException` is raised.</span></span>  
  
## <a name="retrieving-the-current-server-name"></a><span data-ttu-id="d9aba-120">擷取目前的伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="d9aba-120">Retrieving the Current Server Name</span></span>  

 <span data-ttu-id="d9aba-121">萬一發生容錯移轉，您可以使用 <xref:System.Data.SqlClient.SqlConnection> 物件的 <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 屬性，擷取目前連線實際連接的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="d9aba-121">In the event of a failover, you can retrieve the name of the server to which the current connection is actually connected by using the <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="d9aba-122">假設連接變數參考已開啟的 <xref:System.Data.SqlClient.SqlConnection>，下列程式碼片段就會擷取使用中伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="d9aba-122">The following code fragment retrieves the name of the active server, assuming that the connection variable references an open <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
 <span data-ttu-id="d9aba-123">當發生容錯移轉事件且連線切換到鏡像伺服器時，**DataSource** 屬性會更新以反映鏡像名稱。</span><span class="sxs-lookup"><span data-stu-id="d9aba-123">When a failover event occurs and the connection is switched to the mirror server, the **DataSource** property is updated to reflect the mirror name.</span></span>  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a><span data-ttu-id="d9aba-124">SqlClient 鏡像行為</span><span class="sxs-lookup"><span data-stu-id="d9aba-124">SqlClient Mirroring Behavior</span></span>  

 <span data-ttu-id="d9aba-125">用戶端一律會嘗試連線到目前的主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="d9aba-125">The client always tries to connect to the current principal server.</span></span> <span data-ttu-id="d9aba-126">如果失敗，會嘗試容錯移轉夥伴。</span><span class="sxs-lookup"><span data-stu-id="d9aba-126">If it fails, it tries the failover partner.</span></span> <span data-ttu-id="d9aba-127">如果鏡像資料庫已經切換到夥伴伺服器上的主體角色，連線就會成功，而且新的主體-鏡像對應會傳送至用戶端，並在呼叫 <xref:System.AppDomain> 的存留期間進行快取。</span><span class="sxs-lookup"><span data-stu-id="d9aba-127">If the mirror database has already been switched to the principal role on the partner server, the connection succeeds and the new principal-mirror mapping is sent to the client and cached for the lifetime of the calling <xref:System.AppDomain>.</span></span> <span data-ttu-id="d9aba-128">該項目並非儲存於永續性儲存區中，而且無法在不同 **AppDomain** 或處理序中的後續連線上使用。</span><span class="sxs-lookup"><span data-stu-id="d9aba-128">It is not stored in persistent storage and is not available for subsequent connections in a different **AppDomain** or process.</span></span> <span data-ttu-id="d9aba-129">不過，其可在相同 **AppDomain** 內的後續連線上使用。</span><span class="sxs-lookup"><span data-stu-id="d9aba-129">However, it is available for subsequent connections within the same **AppDomain**.</span></span> <span data-ttu-id="d9aba-130">請注意，在相同或不同電腦上執行的其他 **AppDomain** 或處理序永遠擁有自己的連線集區，並且不會重設那些連線。</span><span class="sxs-lookup"><span data-stu-id="d9aba-130">Note that another **AppDomain** or process running on the same or a different computer always has its pool of connections, and those connections are not reset.</span></span> <span data-ttu-id="d9aba-131">在此情況下，如果主要資料庫關閉，則每個處理序或 **AppDomain** 會失敗一次，且會自動清除集區。</span><span class="sxs-lookup"><span data-stu-id="d9aba-131">In that case, if the primary database goes down, each process or **AppDomain** fails once, and the pool is automatically cleared.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9aba-132">伺服器上的鏡像支援是以個別資料庫為基礎所設定的。</span><span class="sxs-lookup"><span data-stu-id="d9aba-132">Mirroring support on the server is configured on a per-database basis.</span></span> <span data-ttu-id="d9aba-133">如果是針對不包含在主體/鏡像集內的其他資料庫執行資料操作作業，不論是使用多部分名稱或透過變更目前的資料庫，這些對其他資料庫所做的變更都不會在發生失敗時傳播。</span><span class="sxs-lookup"><span data-stu-id="d9aba-133">If data manipulation operations are executed against other databases not included in the principal/mirror set, either by using multipart names or by changing the current database, the changes to these other databases do not propagate in the event of failure.</span></span> <span data-ttu-id="d9aba-134">在未鏡像的資料庫中修改資料時，並不會產生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="d9aba-134">No error is generated when data is modified in a database that is not mirrored.</span></span> <span data-ttu-id="d9aba-135">開發人員必須評估此類作業可能產生的影響。</span><span class="sxs-lookup"><span data-stu-id="d9aba-135">The developer must evaluate the possible impact of such operations.</span></span>  
  
## <a name="database-mirroring-resources"></a><span data-ttu-id="d9aba-136">資料庫鏡像資源</span><span class="sxs-lookup"><span data-stu-id="d9aba-136">Database Mirroring Resources</span></span>  

 <span data-ttu-id="d9aba-137">如需設定、部署和管理鏡像的概念文件和詳細資訊，請參閱 SQL Server 文件中的下列資源。</span><span class="sxs-lookup"><span data-stu-id="d9aba-137">For conceptual documentation and information on configuring, deploying and administering mirroring, see the following resources in SQL Server documentation.</span></span>  
  
|<span data-ttu-id="d9aba-138">資源</span><span class="sxs-lookup"><span data-stu-id="d9aba-138">Resource</span></span>|<span data-ttu-id="d9aba-139">描述</span><span class="sxs-lookup"><span data-stu-id="d9aba-139">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="d9aba-140">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="d9aba-140">Database Mirroring</span></span>](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|<span data-ttu-id="d9aba-141">描述如何在 SQL Server 中設定鏡像。</span><span class="sxs-lookup"><span data-stu-id="d9aba-141">Describes how to set up and configure mirroring in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9aba-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9aba-142">See also</span></span>

- <span data-ttu-id="d9aba-143">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="d9aba-143">[ADO.NET Overview](../ado-net-overview.md)</span></span>
