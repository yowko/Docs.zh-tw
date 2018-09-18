---
title: Connection 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003798"
---
# <a name="connection-events"></a>Connection 的事件
所有.NET Framework 資料提供者都有**連接**具有兩個事件，您可以使用擷取的資料來源的參考用訊息，或判斷物件的狀態**連線**具有變更。 下表描述的事件**連線**物件。  
  
|Event - 事件|描述|  
|-----------|-----------------|  
|**InfoMessage**|會在資訊訊息從資料來源傳回時發生。 資訊訊息是從資料來源傳回，且不會造成擲回例外狀況息。|  
|**StateChange**|發生時的狀態**連線**變更。|  
  
## <a name="working-with-the-infomessage-event"></a>使用 InfoMessage 事件  
 您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 物件的 <xref:System.Data.SqlClient.SqlConnection> 事件，從 SQL Server 資料來源擷取警告和資訊訊息。 如果資料來源傳回嚴重性層級 11 到 16 的錯誤，則可能會擲回例外狀況。 不過，您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，從與錯誤無關的資料來源取得訊息。 以 Microsoft SQL Server 為例，任何嚴重性為 10 或以下的錯誤都視為資訊訊息，而且可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件進行擷取。 如需詳細資訊，請參閱 < [Database Engine 錯誤嚴重性](/sql/relational-databases/errors-events/database-engine-error-severities)文章。
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage>事件會接收<xref:System.Data.SqlClient.SqlInfoMessageEventArgs>物件，其中包含，在其**錯誤**屬性、 資料來源的訊息的集合。 您可以查詢**錯誤**此集合中的錯誤號碼和訊息文字，以及錯誤的來源中的物件。 SQL Server 的 .NET Framework 資料提供者也包含訊息來源處的資料庫、預存程序和行號等詳細資訊。  
  
### <a name="example"></a>範例  
 下列程式碼範例會顯示如何加入 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件的事件處理常式。  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>將錯誤視為 InfoMessage 處理  
 只有在資訊訊息及警告訊息是從伺服器傳回時，才會正常地引發 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件。 不過，在實際錯誤發生時，執行**ExecuteNonQuery**或是**ExecuteReader**啟始伺服器作業的方法，並擲回例外狀況。  
  
 若要繼續處理命令中的其餘陳述式，而不理會伺服器產生的任何錯誤，請將 <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> 的 <xref:System.Data.SqlClient.SqlConnection> 屬性設定為 `true`。 這麼做會使得連接引發錯誤的 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，而非擲回例外狀況並中斷處理。 用戶端應用程式接下來處理這個事件並回應錯誤狀況。  
  
> [!NOTE]
>  必須將嚴重性層級 17 或以上的錯誤 (造成伺服器停止處理命令) 當做例外狀況處理。 在此情況下會擲回例外狀況，而不理會<xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件中如何處理錯誤。  
  
## <a name="working-with-the-statechange-event"></a>使用 StateChange 事件  
 **StateChange**就會發生事件時的狀態**連線**變更。 **StateChange**事件會接收<xref:System.Data.StateChangeEventArgs>可讓您判斷狀態變更**連線**使用**OriginalState**並**CurrentState**屬性。 **OriginalState**屬性是<xref:System.Data.ConnectionState>列舉，指出狀態**連接**之前變更它。 **CurrentState**已<xref:System.Data.ConnectionState>列舉，指出狀態**連線**變更後。  
  
 下列程式碼範例會使用**StateChange**將訊息寫入至主控台的事件時的狀態**連線**變更。  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [連接至資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
