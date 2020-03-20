---
title: Connection 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: a7ad0d4d950da71db0aebca872949fa82669c5c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151693"
---
# <a name="connection-events"></a>Connection 的事件
所有 .NET Framework 資料提供程式都有**連接**物件，具有兩個事件，可用於從資料來源檢索資訊消息或確定**連接**的狀態是否已更改。 下表描述了**連接**物件的事件。  
  
|事件|描述|  
|-----------|-----------------|  
|**資訊留言**|會在資訊訊息從資料來源傳回時發生。 資訊訊息是從資料來源傳回，且不會造成擲回例外狀況息。|  
|**StateChange**|當**連接**狀態更改時發生。|  
  
## <a name="working-with-the-infomessage-event"></a>使用 InfoMessage 事件  
 您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 物件的 <xref:System.Data.SqlClient.SqlConnection> 事件，從 SQL Server 資料來源擷取警告和資訊訊息。 如果資料來源傳回嚴重性層級 11 到 16 的錯誤，則可能會擲回例外狀況。 不過，您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，從與錯誤無關的資料來源取得訊息。 以 Microsoft SQL Server 為例，任何嚴重性為 10 或以下的錯誤都視為資訊訊息，而且可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件進行擷取。 有關詳細資訊，請參閱[資料庫引擎錯誤許可權](/sql/relational-databases/errors-events/database-engine-error-severities)一文。
  
 該<xref:System.Data.SqlClient.SqlConnection.InfoMessage>事件接收的物件<xref:System.Data.SqlClient.SqlInfoMessageEventArgs>在其**Errors**屬性中包含來自資料來源的消息的集合。 您可以查詢此集合中的**Error**物件以查找錯誤編號和消息文本以及錯誤源。 SQL Server 的 .NET Framework 資料提供者也包含訊息來源處的資料庫、預存程序和行號等詳細資訊。  
  
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
 只有在資訊訊息及警告訊息是從伺服器傳回時，才會正常地引發 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件。 但是，當發生實際錯誤時，啟動伺服器操作的執行**NonQuery**或**ExecuteReader**方法將停止，並引發異常。  
  
 若要繼續處理命令中的其餘陳述式，而不理會伺服器產生的任何錯誤，請將 <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> 的 <xref:System.Data.SqlClient.SqlConnection> 屬性設定為 `true`。 這麼做會使得連接引發錯誤的 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，而非擲回例外狀況並中斷處理。 用戶端應用程式接下來處理這個事件並回應錯誤狀況。  
  
> [!NOTE]
> 必須將嚴重性層級 17 或以上的錯誤 (造成伺服器停止處理命令) 當做例外狀況處理。 在此情況下會擲回例外狀況，而不理會<xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件中如何處理錯誤。  
  
## <a name="working-with-the-statechange-event"></a>使用 StateChange 事件  
 當**連接**狀態更改時，將發生**狀態更改**事件。 **狀態更改**事件接收<xref:System.Data.StateChangeEventArgs>，使您能夠通過使用**原始狀態**和**目前狀態**屬性確定**連接**狀態的更改。 **原始狀態**屬性是一個<xref:System.Data.ConnectionState>枚舉，用於指示**連接**在更改之前的狀態。 **目前狀態**是一<xref:System.Data.ConnectionState>個枚舉，指示**連接**更改後的狀態。  
  
 以下代碼示例使用**StateChange**事件在**連接**狀態更改時向主控台寫入消息。  
  
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

- [連接到資料來源](connecting-to-a-data-source.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
