---
title: "SQL Server 中的查詢通知"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 376f2cfefcaf53affe5a20a5812a02839dd5d4a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="401c6-102">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="401c6-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="401c6-103">依據 Service Broker 基礎結構所建置的查詢通知可讓應用程式在資料變更時收到通知。</span><span class="sxs-lookup"><span data-stu-id="401c6-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="401c6-104">此功能對於從資料庫中提供資訊快取的應用程式 (如 Web 應用程式)，及需要在來源資料變更時收到通知的應用程式來說非常有用。</span><span class="sxs-lookup"><span data-stu-id="401c6-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="401c6-105">您可以使用 ADO.NET，以三種方式實作查詢通知：</span><span class="sxs-lookup"><span data-stu-id="401c6-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1.  <span data-ttu-id="401c6-106">由公開伺服器端功能的 `SqlNotificationRequest` 類別所提供的低層級實作，它可讓您使用通知要求執行命令。</span><span class="sxs-lookup"><span data-stu-id="401c6-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2.  <span data-ttu-id="401c6-107">由在來源應用程式與 SQL Server 之間提供高層級抽象通知功能之 `SqlDependency` 類別所提供的高層級實作，可讓您使用相依性偵測伺服器中的變更。</span><span class="sxs-lookup"><span data-stu-id="401c6-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="401c6-108">在多數情況下，對於使用 .NET Framework Data Provider for SQL Server 的 Managed 用戶端應用程式而言，這是利用 SQL Server 通知功能最簡單且最有效的方式。</span><span class="sxs-lookup"><span data-stu-id="401c6-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3.  <span data-ttu-id="401c6-109">此外，使用 ASP.NET 2.0 或更新版本建置的 Web 應用程式可以使用 `SqlCacheDependency` Helper 類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="401c6-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="401c6-110">查詢通知可用於需要重新整理顯示或快取，以回應基礎資料變更的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="401c6-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="401c6-111">Microsoft SQL Server 可讓 .NET Framework 應用程式傳送命令至 SQL Server，並要求當執行相同命令而產生與最初擷取的不同結果集時，就產生通知。</span><span class="sxs-lookup"><span data-stu-id="401c6-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="401c6-112">伺服器中產生的通知會透過這些要稍後處理的佇列進行傳送。</span><span class="sxs-lookup"><span data-stu-id="401c6-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="401c6-113">您可以針對 SELECT 和 EXECUTE 陳述式設定通知。</span><span class="sxs-lookup"><span data-stu-id="401c6-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="401c6-114">使用 EXECUTE 陳述式時，SQL Server 會針對執行的命令而非 EXECUTE 陳述式本身註冊通知。</span><span class="sxs-lookup"><span data-stu-id="401c6-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="401c6-115">此命令必須符合 SELECT 陳述式的需求和限制。</span><span class="sxs-lookup"><span data-stu-id="401c6-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="401c6-116">當註冊通知的命令包含一個以上的陳述式時，Database Engine 就會針對批次中的每個陳述式建立通知。</span><span class="sxs-lookup"><span data-stu-id="401c6-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="401c6-117">如果您正在開發應用程式的資料變更時，需要可靠的次秒通知，請檢閱各節**規劃有效率的查詢通知策略**和**替代項目查詢通知**中[通知計畫](http://go.microsoft.com/fwlink/?LinkId=211984)SQL Server 線上叢書 》 中的主題。</span><span class="sxs-lookup"><span data-stu-id="401c6-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](http://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="401c6-118">如需查詢通知和 SQL Server Service Broker 的詳細資訊，請參閱下列《SQL Server 線上叢書》主題的連結。</span><span class="sxs-lookup"><span data-stu-id="401c6-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="401c6-119">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="401c6-119">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="401c6-120">使用查詢通知</span><span class="sxs-lookup"><span data-stu-id="401c6-120">Using Query Notifications</span></span>](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [<span data-ttu-id="401c6-121">為通知建立查詢</span><span class="sxs-lookup"><span data-stu-id="401c6-121">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="401c6-122">Service Broker</span><span class="sxs-lookup"><span data-stu-id="401c6-122">Service Broker</span></span>](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [<span data-ttu-id="401c6-123">Service Broker 開發人員資訊中心</span><span class="sxs-lookup"><span data-stu-id="401c6-123">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="401c6-124">開發 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="401c6-124">Development (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a><span data-ttu-id="401c6-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="401c6-125">In This Section</span></span>  
 [<span data-ttu-id="401c6-126">啟用查詢通知</span><span class="sxs-lookup"><span data-stu-id="401c6-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="401c6-127">討論如何使用查詢通知，包括其啟用及使用需求。</span><span class="sxs-lookup"><span data-stu-id="401c6-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="401c6-128">ASP.NET 應用程式中的 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="401c6-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="401c6-129">示範如何使用 ASP.NET 應用程式的查詢通知。</span><span class="sxs-lookup"><span data-stu-id="401c6-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="401c6-130">使用 SqlDependency 偵測變更</span><span class="sxs-lookup"><span data-stu-id="401c6-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="401c6-131">示範如何偵測查詢結果何時會與原來接收的結果不同。</span><span class="sxs-lookup"><span data-stu-id="401c6-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="401c6-132">使用 SqlNotificationRequest 執行 SqlCommand</span><span class="sxs-lookup"><span data-stu-id="401c6-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="401c6-133">示範如何將 <xref:System.Data.SqlClient.SqlCommand> 物件設定為搭配查詢通知使用。</span><span class="sxs-lookup"><span data-stu-id="401c6-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="401c6-134">參考資料</span><span class="sxs-lookup"><span data-stu-id="401c6-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="401c6-135">說明 <xref:System.Data.Sql.SqlNotificationRequest> 類別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="401c6-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="401c6-136">說明 <xref:System.Data.SqlClient.SqlDependency> 類別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="401c6-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="401c6-137">說明 <xref:System.Web.Caching.SqlCacheDependency> 類別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="401c6-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401c6-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="401c6-138">See Also</span></span>  
 [<span data-ttu-id="401c6-139">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="401c6-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="401c6-140">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="401c6-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
