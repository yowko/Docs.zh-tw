---
title: 啟用查詢通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 0c377e02d5be7cb4de41d62b1e3734f790115086
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651213"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="d8c58-102">啟用查詢通知</span><span class="sxs-lookup"><span data-stu-id="d8c58-102">Enabling Query Notifications</span></span>
<span data-ttu-id="d8c58-103">使用查詢通知的應用程式具有通用要求集。</span><span class="sxs-lookup"><span data-stu-id="d8c58-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="d8c58-104">您必須正確設定資料來源才能支援 SQL 查詢通知，而且使用者必須具有正確的用戶端及伺服器端權限。</span><span class="sxs-lookup"><span data-stu-id="d8c58-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="d8c58-105">若要使用查詢通知，您必須：</span><span class="sxs-lookup"><span data-stu-id="d8c58-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="d8c58-106">啟用資料庫的查詢通知。</span><span class="sxs-lookup"><span data-stu-id="d8c58-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="d8c58-107">確保用於連接至資料庫的使用者 ID 具有必要的使用權限。</span><span class="sxs-lookup"><span data-stu-id="d8c58-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="d8c58-108">將可執行有效 SELECT 陳述式的 <xref:System.Data.SqlClient.SqlCommand> 物件，與關聯的通知物件 (<xref:System.Data.SqlClient.SqlDependency> 或 <xref:System.Data.Sql.SqlNotificationRequest>) 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d8c58-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="d8c58-109">受監視的資料變更時，提供處理通知的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8c58-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="d8c58-110">查詢通知需求</span><span class="sxs-lookup"><span data-stu-id="d8c58-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="d8c58-111">查詢通知僅支援符合特定需求清單的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8c58-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="d8c58-112">下表將提供《SQL Server 線上叢書》中 Service Broker 和查詢通知文件的連結。</span><span class="sxs-lookup"><span data-stu-id="d8c58-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d8c58-113">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="d8c58-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="d8c58-114">[建立查詢通知](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d8c58-114">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="d8c58-115">[Service Broker 的安全性考量](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="d8c58-115">[Security Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="d8c58-116">[安全性與保護 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d8c58-116">[Security and Protection (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="d8c58-117">[Notification Services 的安全性考量](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="d8c58-117">[Security Considerations for Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="d8c58-118">[查詢通知權限](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d8c58-118">[Query Notification Permissions](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="d8c58-119">[Service Broker 的國際性考量](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="d8c58-119">[International Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="d8c58-120">[解決方案設計考量 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d8c58-120">[Solution Design Considerations (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="d8c58-121">[Service Broker 開發人員資訊中心](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d8c58-121">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="d8c58-122">[開發人員指南 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="d8c58-122">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="d8c58-123">啟用查詢通知來執行範例程式碼</span><span class="sxs-lookup"><span data-stu-id="d8c58-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="d8c58-124">若要在啟用 Service Broker **AdventureWorks**資料庫使用 SQL Server Management Studio，請執行下列 TRANSACT-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d8c58-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="d8c58-125">若要讓查詢通知範例正常執行，您必須在資料庫伺服器上執行下列 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8c58-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="d8c58-126">查詢通知使用權限</span><span class="sxs-lookup"><span data-stu-id="d8c58-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="d8c58-127">執行要求通知之命令的使用者，必須在伺服器上具有 SUBSCRIBE QUERY NOTIFICATIONS 資料庫的使用權限。</span><span class="sxs-lookup"><span data-stu-id="d8c58-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="d8c58-128">在部分信任狀況下執行的用戶端程式碼要求 <xref:System.Data.SqlClient.SqlClientPermission>。</span><span class="sxs-lookup"><span data-stu-id="d8c58-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="d8c58-129">下列程式碼會建立 <xref:System.Data.SqlClient.SqlClientPermission> 物件，並將 <xref:System.Security.Permissions.PermissionState> 設定為 <xref:System.Security.Permissions.PermissionState.Unrestricted>。</span><span class="sxs-lookup"><span data-stu-id="d8c58-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="d8c58-130">如果在呼叫堆疊中較高的所有呼叫端都尚未被授與此權限，<xref:System.Security.CodeAccessPermission.Demand%2A> 將在執行階段強制執行 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="d8c58-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="d8c58-131">選擇通知物件</span><span class="sxs-lookup"><span data-stu-id="d8c58-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="d8c58-132">查詢通知 API 提供兩個物件來處理通知：<xref:System.Data.SqlClient.SqlDependency> 與 <xref:System.Data.Sql.SqlNotificationRequest>。</span><span class="sxs-lookup"><span data-stu-id="d8c58-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="d8c58-133">一般而言，大多數非 ASP.NET 應用程式應使用 <xref:System.Data.SqlClient.SqlDependency> 物件。</span><span class="sxs-lookup"><span data-stu-id="d8c58-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="d8c58-134">ASP.NET 應用程式應使用較高層級的 <xref:System.Web.Caching.SqlCacheDependency>，其包裝了 <xref:System.Data.SqlClient.SqlDependency>，並提供用於管理通知及快取物件的架構。</span><span class="sxs-lookup"><span data-stu-id="d8c58-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="d8c58-135">使用 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="d8c58-135">Using SqlDependency</span></span>  
 <span data-ttu-id="d8c58-136">若要使用 <xref:System.Data.SqlClient.SqlDependency>，所使用的 SQL Server 資料庫必須啟用 Service Broker，而且使用者必須有接收通知的使用權限。</span><span class="sxs-lookup"><span data-stu-id="d8c58-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="d8c58-137">Service Broker 物件 (如通知佇列) 是預先定義的。</span><span class="sxs-lookup"><span data-stu-id="d8c58-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="d8c58-138">此外，<xref:System.Data.SqlClient.SqlDependency> 會自動啟動工作執行緒，以便在公佈到佇列時處理通知；它也會剖析 Service Broker 訊息，將資訊做為事件引數資料公開。</span><span class="sxs-lookup"><span data-stu-id="d8c58-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="d8c58-139"><xref:System.Data.SqlClient.SqlDependency> 必須藉由呼叫 `Start` 方法來初始化，以便建立對資料庫的相依性。</span><span class="sxs-lookup"><span data-stu-id="d8c58-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="d8c58-140">這是一種靜態方法，您僅需要在所要求之每個資料庫連接的應用程式初始化期間內，呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="d8c58-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="d8c58-141">對於每個進行的相依性連接，`Stop` 方法應該在應用程式終止時呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8c58-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="d8c58-142">使用 SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="d8c58-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="d8c58-143">相反，<xref:System.Data.Sql.SqlNotificationRequest> 要求您自己實作整個接聽基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d8c58-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="d8c58-144">此外，必須定義所有支援的 Service Broker 物件，如佇列、服務及佇列所支援的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d8c58-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="d8c58-145">如果應用程式要求特別通知訊息或通知行為，或者應用程式為較大 Service Broker 應用程式的一部分，則此手動方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="d8c58-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c58-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8c58-146">See also</span></span>

- [<span data-ttu-id="d8c58-147">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="d8c58-147">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [<span data-ttu-id="d8c58-148">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d8c58-148">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
