---
title: 啟用查詢通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 693e67b4d369eb69b8e0a9dded6decb2d3928459
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554875"
---
# <a name="enabling-query-notifications"></a>啟用查詢通知
取用查詢通知的應用程式有一組常見需求。 您必須正確設定資料來源才能支援 SQL 查詢通知，而且使用者必須具有正確的用戶端及伺服器端權限。  
  
 若要使用查詢通知，您必須：  
  
- 啟用資料庫的查詢通知。  
  
- 確定用來連線到資料庫的使用者識別碼具備必要權限。  
  
- 使用 <xref:System.Data.SqlClient.SqlCommand> 物件搭配關聯的通知物件 (<xref:System.Data.SqlClient.SqlDependency> 或 <xref:System.Data.Sql.SqlNotificationRequest>) 執行有效 SELECT 陳述式。  
  
- 提供程式碼來處理受監視的資料發生變更時要發出的通知。  
  
## <a name="query-notifications-requirements"></a>查詢通知需求  
 只有符合一組特定需求的 SELECT 陳述式才支援查詢通知。 下表提供 SQL Server 線上叢書中 Service Broker 與查詢通知文件的連結。  
  
 **SQL Server 文件**  
  
- [為通知建立查詢](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Service Broker 的安全性考量](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [安全性與保護 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Notification Services 的安全性考量](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [查詢通知權限](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Service Broker 的國際性考量](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [解決方案設計考量 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Service Broker 開發人員資訊中心](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [開發人員手冊 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>啟用查詢通知來執行範例程式碼  
 若要透過使用 SQL Server Management Studio，在 **AdventureWorks** 資料庫上啟用 Service Broker，請執行下列 Transact-SQL 陳述式：  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 為了讓查詢通知範例正確執行，必須在資料庫伺服器上執行下列 Transact-SQL 陳述式。  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>查詢通知使用權限  
 若使用者執行的命令會要求通知，則必須有伺服器上的訂閱查詢通知資料庫權限。  
  
 在部分信任狀況下執行的用戶端程式碼需要 <xref:System.Data.SqlClient.SqlClientPermission>。  
  
 下列程式碼會建立將 <xref:System.Security.Permissions.PermissionState> 設定為 <xref:System.Security.Permissions.PermissionState.Unrestricted> 的 <xref:System.Data.SqlClient.SqlClientPermission> 物件。 如果在呼叫堆疊中較高的所有呼叫者都尚未獲授與權限，<xref:System.Security.CodeAccessPermission.Demand%2A> 將會在執行階段強制執行 <xref:System.Security.SecurityException>。  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>選擇通知物件  
 查詢通知 API 提供兩個物件來處理通知：<xref:System.Data.SqlClient.SqlDependency> 和 <xref:System.Data.Sql.SqlNotificationRequest>。 一般而言，大多數非 ASP.NET 應用程式應使用 <xref:System.Data.SqlClient.SqlDependency> 物件。 ASP.NET 應用程式應使用較高層級的 <xref:System.Web.Caching.SqlCacheDependency>，其包裝了 <xref:System.Data.SqlClient.SqlDependency>，並提供用於管理通知及快取物件的架構。  
  
### <a name="using-sqldependency"></a>使用 SqlDependency  
 若要使用 <xref:System.Data.SqlClient.SqlDependency>，所使用的 SQL Server 資料庫必須啟用 Service Broker，且使用者必須具有接收通知的使用權限。 系統會預先定義 Service Broker 物件，例如通知佇列。  
  
 此外，<xref:System.Data.SqlClient.SqlDependency> 會自動啟動背景工作執行緒，以便在通知張貼到佇列時進行處理；它也會剖析 Service Broker 訊息，將資訊以事件引數資料形式公開。 <xref:System.Data.SqlClient.SqlDependency> 必須透過呼叫 `Start` 方法來初始化，以建立對資料庫的相依性。 這是靜態方法，而且只需要在應用程式初始化期間針對每個必要的資料庫連接呼叫一次。 對於每個進行的相依性連線，`Stop` 方法應該在應用程式終止時呼叫。  
  
### <a name="using-sqlnotificationrequest"></a>使用 SqlNotificationRequest  
 相反地，<xref:System.Data.Sql.SqlNotificationRequest> 需要您自行實作整個接聽基礎結構。 此外，必須定義所有支援的 Service Broker 物件，例如佇列、服務與佇列所支援的訊息類型。 如果您的應用程式需要特殊的通知訊息或通知行為，或如果您的應用程式是較大型 Service Broker 應用程式的一部分，此手動方法就很有用。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 中的查詢通知](query-notifications-in-sql-server.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
