---
title: SQL Server 中的查詢通知
description: 瞭解如何使用查詢通知，在 SQL Server 資料庫中的資料變更時通知應用程式，例如重新整理應用程式顯示。
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 8001f75d7e278a965b6e8e00e4b9af7b770a8bb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183087"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="b3249-103">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="b3249-103">Query Notifications in SQL Server</span></span>

<span data-ttu-id="b3249-104">查詢通知是根據 Service Broker 基礎結構而建置，可讓應用程式在資料變更時收到通知。</span><span class="sxs-lookup"><span data-stu-id="b3249-104">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="b3249-105">此功能對於從資料庫中提供資訊快取的應用程式 (如 Web 應用程式)，及需要在來源資料變更時收到通知的應用程式來說非常有用。</span><span class="sxs-lookup"><span data-stu-id="b3249-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="b3249-106">有三種方式可以使用 ADO.NET 來實作查詢通知：</span><span class="sxs-lookup"><span data-stu-id="b3249-106">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="b3249-107">低階實作會由公開伺服器端功能的 `SqlNotificationRequest` 類別所提供，可讓您利用通知要求來執行命令。</span><span class="sxs-lookup"><span data-stu-id="b3249-107">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="b3249-108">高階實作會由 `SqlDependency` 類別所提供，此類別可提供在來源應用程式與 SQL Server 之間通知功能的高階抽象概念，讓您可以使用相依性來偵測伺服器中的變更。</span><span class="sxs-lookup"><span data-stu-id="b3249-108">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="b3249-109">在多數情況下，對於使用 .NET Framework Data Provider for SQL Server 的 Managed 用戶端應用程式而言，這是利用 SQL Server 通知功能最簡單且最有效的方式。</span><span class="sxs-lookup"><span data-stu-id="b3249-109">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="b3249-110">此外，使用 ASP.NET 2.0 或更新版本建置的 Web 應用程式可以使用 `SqlCacheDependency` Helper 類別。</span><span class="sxs-lookup"><span data-stu-id="b3249-110">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="b3249-111">查詢通知對於需要重新整理顯示或快取，以回應底層資料變更的應用程式很有用。</span><span class="sxs-lookup"><span data-stu-id="b3249-111">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="b3249-112">Microsoft SQL Server 可讓 .NET Framework 應用程式傳送命令至 SQL Server，並要求當執行相同命令而產生與最初擷取的不同結果集時，就產生通知。</span><span class="sxs-lookup"><span data-stu-id="b3249-112">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="b3249-113">在伺服器所產生的通知會透過佇列傳送，以供稍後處理。</span><span class="sxs-lookup"><span data-stu-id="b3249-113">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="b3249-114">您可以為 SELECT 和 EXECUTE 陳述式設定通知。</span><span class="sxs-lookup"><span data-stu-id="b3249-114">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="b3249-115">使用 EXECUTE 陳述式時，SQL Server 會為執行的命令註冊通知，而非為 EXECUTE 陳述式本身。</span><span class="sxs-lookup"><span data-stu-id="b3249-115">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="b3249-116">此命令必須符合 SELECT 陳述式的需求和限制。</span><span class="sxs-lookup"><span data-stu-id="b3249-116">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="b3249-117">當註冊通知的命令包含多個陳述式時，資料庫引擎會為批次中的每個陳述式建立一個通知。</span><span class="sxs-lookup"><span data-stu-id="b3249-117">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="b3249-118">如果您要開發的應用程式在資料變更時需要可靠的次秒通知，請參閱**規劃有效率的查詢通知策略**，以及[規劃通知](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105))文章中**查詢通知的替代**專案。</span><span class="sxs-lookup"><span data-stu-id="b3249-118">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) article.</span></span> <span data-ttu-id="b3249-119">如需查詢通知和 SQL Server Service Broker 的詳細資訊，請參閱 SQL Server 檔中的下列文章連結。</span><span class="sxs-lookup"><span data-stu-id="b3249-119">For more information about Query Notifications and SQL Server Service Broker, see the following links to articles in the SQL Server documentation.</span></span>  
  
 <span data-ttu-id="b3249-120">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="b3249-120">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="b3249-121">[使用查詢通知](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="b3249-121">[Using Query Notifications](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="b3249-122">[為通知建立查詢](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="b3249-122">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="b3249-123">[開發 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="b3249-123">[Development (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="b3249-124">[Service Broker 開發人員資訊中心](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="b3249-124">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="b3249-125">[開發人員手冊 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="b3249-125">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3249-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="b3249-126">In This Section</span></span>  

 [<span data-ttu-id="b3249-127">啟用查詢通知</span><span class="sxs-lookup"><span data-stu-id="b3249-127">Enabling Query Notifications</span></span>](enabling-query-notifications.md)  
 <span data-ttu-id="b3249-128">討論如何使用查詢通知，包括其啟用及使用需求。</span><span class="sxs-lookup"><span data-stu-id="b3249-128">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="b3249-129">ASP.NET 應用程式中的 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="b3249-129">SqlDependency in an ASP.NET Application</span></span>](sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="b3249-130">示範如何使用 ASP.NET 應用程式的查詢通知。</span><span class="sxs-lookup"><span data-stu-id="b3249-130">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="b3249-131">使用 SqlDependency 偵測變更</span><span class="sxs-lookup"><span data-stu-id="b3249-131">Detecting Changes with SqlDependency</span></span>](detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="b3249-132">示範如何偵測查詢結果何時將會與原始接收的結果不同。</span><span class="sxs-lookup"><span data-stu-id="b3249-132">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="b3249-133">使用 SqlNotificationRequest 的 SqlCommand 執行</span><span class="sxs-lookup"><span data-stu-id="b3249-133">SqlCommand Execution with a SqlNotificationRequest</span></span>](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="b3249-134">示範如何設定 <xref:System.Data.SqlClient.SqlCommand> 物件來處理查詢通知。</span><span class="sxs-lookup"><span data-stu-id="b3249-134">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b3249-135">參考</span><span class="sxs-lookup"><span data-stu-id="b3249-135">Reference</span></span>  

 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="b3249-136">描述 <xref:System.Data.Sql.SqlNotificationRequest> 類別與其所有成員。</span><span class="sxs-lookup"><span data-stu-id="b3249-136">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="b3249-137">描述 <xref:System.Data.SqlClient.SqlDependency> 類別與其所有成員。</span><span class="sxs-lookup"><span data-stu-id="b3249-137">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="b3249-138">描述 <xref:System.Web.Caching.SqlCacheDependency> 類別與其所有成員。</span><span class="sxs-lookup"><span data-stu-id="b3249-138">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3249-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3249-139">See also</span></span>

- <span data-ttu-id="b3249-140">[SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b3249-140">[SQL Server and ADO.NET](index.md)</span></span>
- <span data-ttu-id="b3249-141">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="b3249-141">[ADO.NET Overview](../ado-net-overview.md)</span></span>
