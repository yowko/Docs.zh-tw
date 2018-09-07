---
title: Connection 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805857"
---
# <a name="connection-events"></a><span data-ttu-id="4c662-102">Connection 的事件</span><span class="sxs-lookup"><span data-stu-id="4c662-102">Connection Events</span></span>
<span data-ttu-id="4c662-103">所有.NET Framework 資料提供者都有**連接**具有兩個事件，您可以使用擷取的資料來源的參考用訊息，或判斷物件的狀態**連線**具有變更。</span><span class="sxs-lookup"><span data-stu-id="4c662-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="4c662-104">下表描述的事件**連線**物件。</span><span class="sxs-lookup"><span data-stu-id="4c662-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="4c662-105">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="4c662-105">Event</span></span>|<span data-ttu-id="4c662-106">描述</span><span class="sxs-lookup"><span data-stu-id="4c662-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c662-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="4c662-107">**InfoMessage**</span></span>|<span data-ttu-id="4c662-108">會在資訊訊息從資料來源傳回時發生。</span><span class="sxs-lookup"><span data-stu-id="4c662-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="4c662-109">資訊訊息是從資料來源傳回，且不會造成擲回例外狀況息。</span><span class="sxs-lookup"><span data-stu-id="4c662-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="4c662-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="4c662-110">**StateChange**</span></span>|<span data-ttu-id="4c662-111">發生時的狀態**連線**變更。</span><span class="sxs-lookup"><span data-stu-id="4c662-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="4c662-112">使用 InfoMessage 事件</span><span class="sxs-lookup"><span data-stu-id="4c662-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="4c662-113">您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 物件的 <xref:System.Data.SqlClient.SqlConnection> 事件，從 SQL Server 資料來源擷取警告和資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="4c662-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="4c662-114">如果資料來源傳回嚴重性層級 11 到 16 的錯誤，則可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c662-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="4c662-115">不過，您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，從與錯誤無關的資料來源取得訊息。</span><span class="sxs-lookup"><span data-stu-id="4c662-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="4c662-116">以 Microsoft SQL Server 為例，任何嚴重性為 10 或以下的錯誤都視為資訊訊息，而且可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件進行擷取。</span><span class="sxs-lookup"><span data-stu-id="4c662-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="4c662-117">如需詳細資訊，請參閱 < [Database Engine 錯誤嚴重性](/sql/relational-databases/errors-events/database-engine-error-severities)文章。</span><span class="sxs-lookup"><span data-stu-id="4c662-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="4c662-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage>事件會接收<xref:System.Data.SqlClient.SqlInfoMessageEventArgs>物件，其中包含，在其**錯誤**屬性、 資料來源的訊息的集合。</span><span class="sxs-lookup"><span data-stu-id="4c662-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="4c662-119">您可以查詢**錯誤**此集合中的錯誤號碼和訊息文字，以及錯誤的來源中的物件。</span><span class="sxs-lookup"><span data-stu-id="4c662-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="4c662-120">SQL Server 的 .NET Framework 資料提供者也包含訊息來源處的資料庫、預存程序和行號等詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4c662-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="4c662-121">範例</span><span class="sxs-lookup"><span data-stu-id="4c662-121">Example</span></span>  
 <span data-ttu-id="4c662-122">下列程式碼範例會顯示如何加入 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4c662-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="4c662-123">將錯誤視為 InfoMessage 處理</span><span class="sxs-lookup"><span data-stu-id="4c662-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="4c662-124">只有在資訊訊息及警告訊息是從伺服器傳回時，才會正常地引發 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件。</span><span class="sxs-lookup"><span data-stu-id="4c662-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="4c662-125">不過，在實際錯誤發生時，執行**ExecuteNonQuery**或是**ExecuteReader**啟始伺服器作業的方法，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c662-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="4c662-126">若要繼續處理命令中的其餘陳述式，而不理會伺服器產生的任何錯誤，請將 <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> 的 <xref:System.Data.SqlClient.SqlConnection> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4c662-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="4c662-127">這麼做會使得連接引發錯誤的 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，而非擲回例外狀況並中斷處理。</span><span class="sxs-lookup"><span data-stu-id="4c662-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="4c662-128">用戶端應用程式接下來處理這個事件並回應錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="4c662-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c662-129">必須將嚴重性層級 17 或以上的錯誤 (造成伺服器停止處理命令) 當做例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="4c662-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="4c662-130">在此情況下會擲回例外狀況，而不理會<xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件中如何處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c662-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="4c662-131">使用 StateChange 事件</span><span class="sxs-lookup"><span data-stu-id="4c662-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="4c662-132">**StateChange**就會發生事件時的狀態**連線**變更。</span><span class="sxs-lookup"><span data-stu-id="4c662-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="4c662-133">**StateChange**事件會接收<xref:System.Data.StateChangeEventArgs>可讓您判斷狀態變更**連線**使用**OriginalState**並**CurrentState**屬性。</span><span class="sxs-lookup"><span data-stu-id="4c662-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="4c662-134">**OriginalState**屬性是<xref:System.Data.ConnectionState>列舉，指出狀態**連接**之前變更它。</span><span class="sxs-lookup"><span data-stu-id="4c662-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="4c662-135">**CurrentState**已<xref:System.Data.ConnectionState>列舉，指出狀態**連線**變更後。</span><span class="sxs-lookup"><span data-stu-id="4c662-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="4c662-136">下列程式碼範例會使用**StateChange**將訊息寫入至主控台的事件時的狀態**連線**變更。</span><span class="sxs-lookup"><span data-stu-id="4c662-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c662-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c662-137">See Also</span></span>  
 [<span data-ttu-id="4c662-138">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="4c662-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="4c662-139">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="4c662-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
