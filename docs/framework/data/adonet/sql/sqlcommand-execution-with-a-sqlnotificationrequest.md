---
title: 使用 SqlNotificationRequest 執行 SqlCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 1380d06b54980456080d9891013d0d8de6b4110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664092"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="da80a-102">使用 SqlNotificationRequest 執行 SqlCommand</span><span class="sxs-lookup"><span data-stu-id="da80a-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="da80a-103">您可以將 <xref:System.Data.SqlClient.SqlCommand> 設定為在從伺服器擷取的資料變更時產生通知，如果再次執行查詢，結果集就會不同。</span><span class="sxs-lookup"><span data-stu-id="da80a-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="da80a-104">這對於想要在伺服器上使用自訂通知佇列，或者不想維護使用中物件的情況都很有用。</span><span class="sxs-lookup"><span data-stu-id="da80a-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="da80a-105">建立通知要求</span><span class="sxs-lookup"><span data-stu-id="da80a-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="da80a-106">您可以將 <xref:System.Data.Sql.SqlNotificationRequest> 物件繫結至 `SqlCommand` 物件，藉此建立通知要求。</span><span class="sxs-lookup"><span data-stu-id="da80a-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="da80a-107">在要求建立之後，就不再需要 `SqlNotificationRequest` 物件。</span><span class="sxs-lookup"><span data-stu-id="da80a-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="da80a-108">您可以查詢佇列以尋找通知並進行適當的回應。</span><span class="sxs-lookup"><span data-stu-id="da80a-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="da80a-109">即使應用程式關閉後又重新啟動，也可能造成通知。</span><span class="sxs-lookup"><span data-stu-id="da80a-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="da80a-110">在執行具有相關聯通知的命令時，對原始結果集所做的任何變更，都會傳送訊息至在通知要求中設定的 SQL Server 佇列。</span><span class="sxs-lookup"><span data-stu-id="da80a-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="da80a-111">輪詢 SQL Server 佇列及解譯訊息的方式，視應用程式而定。</span><span class="sxs-lookup"><span data-stu-id="da80a-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="da80a-112">應用程式負責輪詢佇列並依據訊息的內容進行回應。</span><span class="sxs-lookup"><span data-stu-id="da80a-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da80a-113">搭配使用 <xref:System.Data.SqlClient.SqlDependency> 與 SQL Server 通知要求時，請建立自己的佇列名稱，而不要使用預設服務名稱。</span><span class="sxs-lookup"><span data-stu-id="da80a-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="da80a-114"><xref:System.Data.Sql.SqlNotificationRequest> 沒有新的用戶端安全性項目。</span><span class="sxs-lookup"><span data-stu-id="da80a-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="da80a-115">這通常是伺服器功能，並且伺服器已建立使用者要求通知時必須擁有的特殊權限。</span><span class="sxs-lookup"><span data-stu-id="da80a-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="da80a-116">範例</span><span class="sxs-lookup"><span data-stu-id="da80a-116">Example</span></span>  
 <span data-ttu-id="da80a-117">下列程式碼片段將示範如何建立 <xref:System.Data.Sql.SqlNotificationRequest> 並將它與 <xref:System.Data.SqlClient.SqlCommand> 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="da80a-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
```vb  
' Assume connection is an open SqlConnection.  
' Create a new SqlCommand object.  
Dim command As New SqlCommand( _  
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)  
  
' Create a SqlNotificationRequest object.  
Dim notficationRequest As New SqlNotificationRequest()  
notficationRequest.id = "NotificationID"  
notficationRequest.Service = "mySSBQueue"  
  
' Associate the notification request with the command.  
command.Notification = notficationRequest  
' Execute the command.  
command.ExecuteReader()  
' Process the DataReader.  
' You can use Transact-SQL syntax to periodically poll the   
' SQL Server queue to see if you have a new message.  
```  
  
```csharp  
// Assume connection is an open SqlConnection.  
// Create a new SqlCommand object.  
SqlCommand command=new SqlCommand(  
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);  
  
// Create a SqlNotificationRequest object.  
SqlNotificationRequest notficationRequest=new SqlNotificationRequest();  
notficationRequest.id="NotificationID";  
notficationRequest.Service="mySSBQueue";  
  
// Associate the notification request with the command.  
command.Notification=notficationRequest;  
// Execute the command.  
command.ExecuteReader();  
// Process the DataReader.  
// You can use Transact-SQL syntax to periodically poll the   
// SQL Server queue to see if you have a new message.  
```  
  
## <a name="see-also"></a><span data-ttu-id="da80a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da80a-118">See also</span></span>
- [<span data-ttu-id="da80a-119">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="da80a-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [<span data-ttu-id="da80a-120">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="da80a-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
