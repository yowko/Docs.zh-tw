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
# <a name="connection-events"></a><span data-ttu-id="2729c-102">Connection 的事件</span><span class="sxs-lookup"><span data-stu-id="2729c-102">Connection Events</span></span>
<span data-ttu-id="2729c-103">所有 .NET Framework 資料提供程式都有**連接**物件，具有兩個事件，可用於從資料來源檢索資訊消息或確定**連接**的狀態是否已更改。</span><span class="sxs-lookup"><span data-stu-id="2729c-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="2729c-104">下表描述了**連接**物件的事件。</span><span class="sxs-lookup"><span data-stu-id="2729c-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="2729c-105">事件</span><span class="sxs-lookup"><span data-stu-id="2729c-105">Event</span></span>|<span data-ttu-id="2729c-106">描述</span><span class="sxs-lookup"><span data-stu-id="2729c-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2729c-107">**資訊留言**</span><span class="sxs-lookup"><span data-stu-id="2729c-107">**InfoMessage**</span></span>|<span data-ttu-id="2729c-108">會在資訊訊息從資料來源傳回時發生。</span><span class="sxs-lookup"><span data-stu-id="2729c-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="2729c-109">資訊訊息是從資料來源傳回，且不會造成擲回例外狀況息。</span><span class="sxs-lookup"><span data-stu-id="2729c-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="2729c-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="2729c-110">**StateChange**</span></span>|<span data-ttu-id="2729c-111">當**連接**狀態更改時發生。</span><span class="sxs-lookup"><span data-stu-id="2729c-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="2729c-112">使用 InfoMessage 事件</span><span class="sxs-lookup"><span data-stu-id="2729c-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="2729c-113">您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 物件的 <xref:System.Data.SqlClient.SqlConnection> 事件，從 SQL Server 資料來源擷取警告和資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="2729c-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="2729c-114">如果資料來源傳回嚴重性層級 11 到 16 的錯誤，則可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2729c-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="2729c-115">不過，您可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，從與錯誤無關的資料來源取得訊息。</span><span class="sxs-lookup"><span data-stu-id="2729c-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="2729c-116">以 Microsoft SQL Server 為例，任何嚴重性為 10 或以下的錯誤都視為資訊訊息，而且可以使用 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件進行擷取。</span><span class="sxs-lookup"><span data-stu-id="2729c-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="2729c-117">有關詳細資訊，請參閱[資料庫引擎錯誤許可權](/sql/relational-databases/errors-events/database-engine-error-severities)一文。</span><span class="sxs-lookup"><span data-stu-id="2729c-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="2729c-118">該<xref:System.Data.SqlClient.SqlConnection.InfoMessage>事件接收的物件<xref:System.Data.SqlClient.SqlInfoMessageEventArgs>在其**Errors**屬性中包含來自資料來源的消息的集合。</span><span class="sxs-lookup"><span data-stu-id="2729c-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="2729c-119">您可以查詢此集合中的**Error**物件以查找錯誤編號和消息文本以及錯誤源。</span><span class="sxs-lookup"><span data-stu-id="2729c-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="2729c-120">SQL Server 的 .NET Framework 資料提供者也包含訊息來源處的資料庫、預存程序和行號等詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2729c-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2729c-121">範例</span><span class="sxs-lookup"><span data-stu-id="2729c-121">Example</span></span>  
 <span data-ttu-id="2729c-122">下列程式碼範例會顯示如何加入 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2729c-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="2729c-123">將錯誤視為 InfoMessage 處理</span><span class="sxs-lookup"><span data-stu-id="2729c-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="2729c-124">只有在資訊訊息及警告訊息是從伺服器傳回時，才會正常地引發 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件。</span><span class="sxs-lookup"><span data-stu-id="2729c-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="2729c-125">但是，當發生實際錯誤時，啟動伺服器操作的執行**NonQuery**或**ExecuteReader**方法將停止，並引發異常。</span><span class="sxs-lookup"><span data-stu-id="2729c-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="2729c-126">若要繼續處理命令中的其餘陳述式，而不理會伺服器產生的任何錯誤，請將 <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> 的 <xref:System.Data.SqlClient.SqlConnection> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="2729c-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="2729c-127">這麼做會使得連接引發錯誤的 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件，而非擲回例外狀況並中斷處理。</span><span class="sxs-lookup"><span data-stu-id="2729c-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="2729c-128">用戶端應用程式接下來處理這個事件並回應錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="2729c-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2729c-129">必須將嚴重性層級 17 或以上的錯誤 (造成伺服器停止處理命令) 當做例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="2729c-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="2729c-130">在此情況下會擲回例外狀況，而不理會<xref:System.Data.SqlClient.SqlConnection.InfoMessage> 事件中如何處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="2729c-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="2729c-131">使用 StateChange 事件</span><span class="sxs-lookup"><span data-stu-id="2729c-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="2729c-132">當**連接**狀態更改時，將發生**狀態更改**事件。</span><span class="sxs-lookup"><span data-stu-id="2729c-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="2729c-133">**狀態更改**事件接收<xref:System.Data.StateChangeEventArgs>，使您能夠通過使用**原始狀態**和**目前狀態**屬性確定**連接**狀態的更改。</span><span class="sxs-lookup"><span data-stu-id="2729c-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="2729c-134">**原始狀態**屬性是一個<xref:System.Data.ConnectionState>枚舉，用於指示**連接**在更改之前的狀態。</span><span class="sxs-lookup"><span data-stu-id="2729c-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="2729c-135">**目前狀態**是一<xref:System.Data.ConnectionState>個枚舉，指示**連接**更改後的狀態。</span><span class="sxs-lookup"><span data-stu-id="2729c-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="2729c-136">以下代碼示例使用**StateChange**事件在**連接**狀態更改時向主控台寫入消息。</span><span class="sxs-lookup"><span data-stu-id="2729c-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2729c-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2729c-137">See also</span></span>

- [<span data-ttu-id="2729c-138">連接到資料來源</span><span class="sxs-lookup"><span data-stu-id="2729c-138">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- <span data-ttu-id="2729c-139">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="2729c-139">[ADO.NET Overview](ado-net-overview.md)</span></span>
