---
title: SQL Server 中的查詢通知
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 166471658ccd1ef48db2ac1647f74ea696f3263d
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092289"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="d3d96-102">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="d3d96-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="d3d96-103">依據 Service Broker 基礎結構所建置的查詢通知可讓應用程式在資料變更時收到通知。</span><span class="sxs-lookup"><span data-stu-id="d3d96-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="d3d96-104">此功能對於從資料庫中提供資訊快取的應用程式 (如 Web 應用程式)，及需要在來源資料變更時收到通知的應用程式來說非常有用。</span><span class="sxs-lookup"><span data-stu-id="d3d96-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="d3d96-105">您可以使用 ADO.NET，以三種方式實作查詢通知：</span><span class="sxs-lookup"><span data-stu-id="d3d96-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1.  <span data-ttu-id="d3d96-106">由公開伺服器端功能的 `SqlNotificationRequest` 類別所提供的低層級實作，它可讓您使用通知要求執行命令。</span><span class="sxs-lookup"><span data-stu-id="d3d96-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2.  <span data-ttu-id="d3d96-107">由在來源應用程式與 SQL Server 之間提供高層級抽象通知功能之 `SqlDependency` 類別所提供的高層級實作，可讓您使用相依性偵測伺服器中的變更。</span><span class="sxs-lookup"><span data-stu-id="d3d96-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="d3d96-108">在多數情況下，對於使用 .NET Framework Data Provider for SQL Server 的 Managed 用戶端應用程式而言，這是利用 SQL Server 通知功能最簡單且最有效的方式。</span><span class="sxs-lookup"><span data-stu-id="d3d96-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3.  <span data-ttu-id="d3d96-109">此外，使用 ASP.NET 2.0 或更新版本建置的 Web 應用程式可以使用 `SqlCacheDependency` Helper 類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="d3d96-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="d3d96-110">查詢通知可用於需要重新整理顯示或快取，以回應基礎資料變更的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="d3d96-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="d3d96-111">Microsoft SQL Server 可讓 .NET Framework 應用程式傳送命令至 SQL Server，並要求當執行相同命令而產生與最初擷取的不同結果集時，就產生通知。</span><span class="sxs-lookup"><span data-stu-id="d3d96-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="d3d96-112">伺服器中產生的通知會透過這些要稍後處理的佇列進行傳送。</span><span class="sxs-lookup"><span data-stu-id="d3d96-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="d3d96-113">您可以針對 SELECT 和 EXECUTE 陳述式設定通知。</span><span class="sxs-lookup"><span data-stu-id="d3d96-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="d3d96-114">使用 EXECUTE 陳述式時，SQL Server 會針對執行的命令而非 EXECUTE 陳述式本身註冊通知。</span><span class="sxs-lookup"><span data-stu-id="d3d96-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="d3d96-115">此命令必須符合 SELECT 陳述式的需求和限制。</span><span class="sxs-lookup"><span data-stu-id="d3d96-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="d3d96-116">當註冊通知的命令包含一個以上的陳述式時，Database Engine 就會針對批次中的每個陳述式建立通知。</span><span class="sxs-lookup"><span data-stu-id="d3d96-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="d3d96-117">如果您正在開發應用程式的資料變更時，會需要可靠的次秒通知，請檢閱章節**規劃有效率的查詢通知策略**和**替代項目查詢通知**中[通知計畫](https://go.microsoft.com/fwlink/?LinkId=211984)SQL Server 線上叢書 》 中的主題。</span><span class="sxs-lookup"><span data-stu-id="d3d96-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](https://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="d3d96-118">如需查詢通知和 SQL Server Service Broker 的詳細資訊，請參閱下列《SQL Server 線上叢書》主題的連結。</span><span class="sxs-lookup"><span data-stu-id="d3d96-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d3d96-119">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="d3d96-119">**SQL Server documentation**</span></span>  
  
-   <span data-ttu-id="d3d96-120">[使用查詢通知](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d3d96-120">[Using Query Notifications](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
-   <span data-ttu-id="d3d96-121">[建立查詢通知](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d3d96-121">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
-   <span data-ttu-id="d3d96-122">[開發 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d3d96-122">[Development (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
-   <span data-ttu-id="d3d96-123">[Service Broker 開發人員資訊中心](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d3d96-123">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
-   <span data-ttu-id="d3d96-124">[開發人員指南 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d3d96-124">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3d96-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3d96-125">In This Section</span></span>  
 [<span data-ttu-id="d3d96-126">啟用查詢通知</span><span class="sxs-lookup"><span data-stu-id="d3d96-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="d3d96-127">討論如何使用查詢通知，包括其啟用及使用需求。</span><span class="sxs-lookup"><span data-stu-id="d3d96-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="d3d96-128">ASP.NET 應用程式中的 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="d3d96-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="d3d96-129">示範如何使用 ASP.NET 應用程式的查詢通知。</span><span class="sxs-lookup"><span data-stu-id="d3d96-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="d3d96-130">使用 SqlDependency 偵測變更</span><span class="sxs-lookup"><span data-stu-id="d3d96-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="d3d96-131">示範如何偵測查詢結果何時會與原來接收的結果不同。</span><span class="sxs-lookup"><span data-stu-id="d3d96-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="d3d96-132">使用 SqlNotificationRequest 執行 SqlCommand</span><span class="sxs-lookup"><span data-stu-id="d3d96-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="d3d96-133">示範如何將 <xref:System.Data.SqlClient.SqlCommand> 物件設定為搭配查詢通知使用。</span><span class="sxs-lookup"><span data-stu-id="d3d96-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d3d96-134">參考資料</span><span class="sxs-lookup"><span data-stu-id="d3d96-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="d3d96-135">說明 <xref:System.Data.Sql.SqlNotificationRequest> 類別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="d3d96-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="d3d96-136">說明 <xref:System.Data.SqlClient.SqlDependency> 類別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="d3d96-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="d3d96-137">說明 <xref:System.Web.Caching.SqlCacheDependency> 類別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="d3d96-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d96-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3d96-138">See also</span></span>
- [<span data-ttu-id="d3d96-139">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3d96-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="d3d96-140">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d3d96-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
