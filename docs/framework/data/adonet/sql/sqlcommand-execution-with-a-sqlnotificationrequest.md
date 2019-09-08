---
title: 使用 SqlNotificationRequest 執行 SqlCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791541"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>使用 SqlNotificationRequest 執行 SqlCommand

您可以將 <xref:System.Data.SqlClient.SqlCommand> 設定為在從伺服器擷取的資料變更時產生通知，如果再次執行查詢，結果集就會不同。 這對於想要在伺服器上使用自訂通知佇列，或者不想維護使用中物件的情況都很有用。

## <a name="creating-the-notification-request"></a>建立通知要求

您可以將 <xref:System.Data.Sql.SqlNotificationRequest> 物件繫結至 `SqlCommand` 物件，藉此建立通知要求。 在要求建立之後，就不再需要 `SqlNotificationRequest` 物件。 您可以查詢佇列以尋找通知並進行適當的回應。 即使應用程式關閉後又重新啟動，也可能造成通知。

在執行具有相關聯通知的命令時，對原始結果集所做的任何變更，都會傳送訊息至在通知要求中設定的 SQL Server 佇列。

輪詢 SQL Server 佇列及解譯訊息的方式，視應用程式而定。 應用程式負責輪詢佇列並依據訊息的內容進行回應。

> [!NOTE]
> 搭配使用 <xref:System.Data.SqlClient.SqlDependency> 與 SQL Server 通知要求時，請建立自己的佇列名稱，而不要使用預設服務名稱。

<xref:System.Data.Sql.SqlNotificationRequest> 沒有新的用戶端安全性項目。 這通常是伺服器功能，並且伺服器已建立使用者要求通知時必須擁有的特殊權限。

### <a name="example"></a>範例

下列程式碼片段將示範如何建立 <xref:System.Data.Sql.SqlNotificationRequest> 並將它與 <xref:System.Data.SqlClient.SqlCommand> 產生關聯。

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
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
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a>另請參閱

- [SQL Server 中的查詢通知](query-notifications-in-sql-server.md)
- [ADO.NET 概觀](../ado-net-overview.md)
