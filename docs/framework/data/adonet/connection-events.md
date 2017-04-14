---
title: "連接事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 連接事件
所有 .NET Framework 資料提供者都有 **Connection** 物件，該物件則有兩個事件，可讓您從資料來源擷取參考訊息，或判斷 **Connection** 的狀態是否已變更。  下表說明 **Connection** 物件的事件。  
  
|事件|描述|  
|--------|--------|  
|**InfoMessage**|會在資訊訊息從資料來源傳回時發生。  資訊訊息是從資料來源傳回，且不會造成擲回例外狀況息。|  
|**StateChange**|於 **Connection** 狀態變更時發生。|  
  
## 使用 InfoMessage 事件  
 您可以使用 <xref:System.Data.SqlClient.SqlConnection> 物件的 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，從 SQL Server 資料來源擷取警告和資訊訊息。  如果資料來源傳回嚴重性層級 11 到 16 的錯誤，則可能會擲回例外狀況。  不過，您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，從與錯誤無關的資料來源取得訊息。  以 Microsoft SQL Server 為例，任何嚴重性為 10 或以下的錯誤都視為資訊訊息，而且可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件進行擷取。  如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜錯誤訊息嚴重性層級＞主題 \(英文\)。  
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件會接收 <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> 物件，該物件在其 **Errors** 屬性中包含資料來源的訊息集合。  您可以向這個集合中的 **Error** 物件查詢錯誤代碼、訊息文字和錯誤來源。  SQL Server 的 .NET Framework 資料提供者也包含訊息來源處的資料庫、預存程序和行號等詳細資訊。  
  
### 範例  
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
  
## 將錯誤視為 InfoMessage 處理  
 只有在資訊訊息及警告訊息是從伺服器傳回時，才會正常地引發 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件。  不過在確實發生錯誤時，將無法執行 **ExecuteNonQuery** 或 **ExecuteReader** 方法 \(此方法可啟始伺服器作業\)，並擲回例外狀況。  
  
 若要繼續處理命令中的其餘陳述式，而不理會伺服器產生的任何錯誤，請將 <xref:System.Data.SqlClient.SqlConnection> 的 <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> 屬性設定為 `true`。  這麼做會使得連接引發錯誤的 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，而非擲回例外狀況並中斷處理。  用戶端應用程式接下來處理這個事件並回應錯誤狀況。  
  
> [!NOTE]
>  必須將嚴重性層級 17 或以上的錯誤 \(造成伺服器停止處理命令\) 當做例外狀況處理。  在此情況下會擲回例外狀況，而不理會<xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件中如何處理錯誤。  
  
## 使用 StateChange 事件  
 **Connection** 狀態變更時會發生 **StateChange** 事件。  **StateChange** 事件會接收 <xref:System.Data.StateChangeEventArgs>，可讓您使用 **OriginalState** 和 **CurrentState** 屬性，判斷 **Connection** 的狀態變更。  **OriginalState** 屬性是 <xref:System.Data.ConnectionState> 列舉型別，表示 **Connection** 變更前的狀態。  **CurrentState** 是 <xref:System.Data.ConnectionState> 列舉型別，表示 **Connection** 變更後的狀態。  
  
 下列程式碼範例在 **Connection** 狀態變更時，使用 **StateChange** 事件撰寫訊息給主控台。  
  
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
  
## 請參閱  
 [連接資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)