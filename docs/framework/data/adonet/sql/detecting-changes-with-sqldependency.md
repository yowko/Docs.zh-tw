---
title: 使用 SqlDependency 偵測變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 63d6a17e5aaf3e5d39ed0eda288e75c071be4d73
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183768"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="ba18f-102">使用 SqlDependency 偵測變更</span><span class="sxs-lookup"><span data-stu-id="ba18f-102">Detecting Changes with SqlDependency</span></span>
<span data-ttu-id="ba18f-103">您可以將 <xref:System.Data.SqlClient.SqlDependency> 物件與 <xref:System.Data.SqlClient.SqlCommand> 產生關聯，以便偵測查詢結果與原始擷取結果不同的時間。</span><span class="sxs-lookup"><span data-stu-id="ba18f-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="ba18f-104">此外，您也可以指派委派 (Delegate) 給 `OnChange` 事件，而此事件將在相關聯命令的結果變更時引發。</span><span class="sxs-lookup"><span data-stu-id="ba18f-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="ba18f-105">您必須先將 <xref:System.Data.SqlClient.SqlDependency> 與此命令產生關聯，然後再執行此命令。</span><span class="sxs-lookup"><span data-stu-id="ba18f-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="ba18f-106">`HasChanges` 的 <xref:System.Data.SqlClient.SqlDependency> 屬性也可用來判斷自從上次擷取資料以來，查詢結果是否已經變更。</span><span class="sxs-lookup"><span data-stu-id="ba18f-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="ba18f-107">安全性考量</span><span class="sxs-lookup"><span data-stu-id="ba18f-107">Security Considerations</span></span>  
 <span data-ttu-id="ba18f-108">相依性基礎結構會仰賴呼叫 <xref:System.Data.SqlClient.SqlConnection> 時所開啟的 <xref:System.Data.SqlClient.SqlDependency.Start%2A>，以便接收指定命令之基礎資料已經變更的通知。</span><span class="sxs-lookup"><span data-stu-id="ba18f-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="ba18f-109">讓用戶端啟始呼叫 `SqlDependency.Start` 的功能是透過使用 <xref:System.Data.SqlClient.SqlClientPermission> 和程式碼存取安全性屬性來控制的。</span><span class="sxs-lookup"><span data-stu-id="ba18f-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="ba18f-110">如需詳細資訊，請參閱 <<c0> [ 啟用查詢通知](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)並[程式碼存取安全性和 ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ba18f-110">For more information, see [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) and [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="ba18f-111">範例</span><span class="sxs-lookup"><span data-stu-id="ba18f-111">Example</span></span>  
 <span data-ttu-id="ba18f-112">下列步驟將說明如何宣告相依性、執行命令，並在結果集變更時接收通知：</span><span class="sxs-lookup"><span data-stu-id="ba18f-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>  
  
1.  <span data-ttu-id="ba18f-113">啟始伺服器的 `SqlDependency` 連接。</span><span class="sxs-lookup"><span data-stu-id="ba18f-113">Initiate a `SqlDependency` connection to the server.</span></span>  
  
2.  <span data-ttu-id="ba18f-114">建立要連接至伺服器的 <xref:System.Data.SqlClient.SqlConnection> 和 <xref:System.Data.SqlClient.SqlCommand> 物件，並定義 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ba18f-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="ba18f-115">建立新的 `SqlDependency` 物件，或使用現有的物件，並將它繫結至 `SqlCommand` 物件。</span><span class="sxs-lookup"><span data-stu-id="ba18f-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="ba18f-116">如此便可在內部建立 <xref:System.Data.Sql.SqlNotificationRequest> 物件，並視需要將其繫結至命令物件。</span><span class="sxs-lookup"><span data-stu-id="ba18f-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="ba18f-117">此通知要求包含可唯一識別此 `SqlDependency` 物件的內部識別項。</span><span class="sxs-lookup"><span data-stu-id="ba18f-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="ba18f-118">此外，它也會啟動用戶端接聽程式 (Listener) (如果尚未作用中的話)。</span><span class="sxs-lookup"><span data-stu-id="ba18f-118">It also starts the client listener if it is not already active.</span></span>  
  
4.  <span data-ttu-id="ba18f-119">訂閱 `OnChange` 物件之 `SqlDependency` 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ba18f-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>  
  
5.  <span data-ttu-id="ba18f-120">使用 `Execute` 物件的任何 `SqlCommand` 方法來執行命令。</span><span class="sxs-lookup"><span data-stu-id="ba18f-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="ba18f-121">因為命令已繫結至通知物件，所以伺服器知道它必須產生通知，並且佇列資訊將指向相依性佇列。</span><span class="sxs-lookup"><span data-stu-id="ba18f-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>  
  
6.  <span data-ttu-id="ba18f-122">停止伺服器的 `SqlDependency` 連接。</span><span class="sxs-lookup"><span data-stu-id="ba18f-122">Stop the `SqlDependency` connection to the server.</span></span>  
  
 <span data-ttu-id="ba18f-123">如果任何使用者隨後變更基礎資料，Microsoft SQL Server 就會偵測到針對此類變更暫止的通知存在，並發佈通知，而該通知可透過呼叫 `SqlConnection` 所建立的基礎 `SqlDependency.Start` 來進行處理並轉送給用戶端。</span><span class="sxs-lookup"><span data-stu-id="ba18f-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="ba18f-124">用戶端接聽程式會接收到無效訊息。</span><span class="sxs-lookup"><span data-stu-id="ba18f-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="ba18f-125">然後，用戶端接聽程式會找出相關聯的 `SqlDependency` 物件並引發 `OnChange` 事件。</span><span class="sxs-lookup"><span data-stu-id="ba18f-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>  
  
 <span data-ttu-id="ba18f-126">下列程式碼片段會顯示您應該用來建立範例應用程式的設計模式。</span><span class="sxs-lookup"><span data-stu-id="ba18f-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>  
  
```vb  
Sub Initialization()  
    ' Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName)  
End Sub  
  
Sub SomeMethod()   
    ' Assume connection is an open SqlConnection.  
    ' Create a new SqlCommand object.  
    Using command As New SqlCommand( _  
      "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", _  
      connection)  
  
        ' Create a dependency and associate it with the SqlCommand.  
        Dim dependency As New SqlDependency(command)  
        ' Maintain the refence in a class member.  
        ' Subscribe to the SqlDependency event.  
        AddHandler dependency.OnChange, AddressOf OnDependencyChange  
  
        ' Execute the command.  
        Using reader = command.ExecuteReader()  
            ' Process the DataReader.  
        End Using  
    End Using  
End Sub   
  
' Handler method  
Sub OnDependencyChange(ByVal sender As Object, _  
    ByVal e As SqlNotificationEventArgs)   
    ' Handle the event (for example, invalidate this cache entry).  
End Sub  
  
Sub Termination()  
    ' Release the dependency  
    SqlDependency.Stop(connectionString, queueName)  
End Sub  
```  
  
```csharp  
void Initialization()  
{  
    // Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName);  
}  
  
void SomeMethod()  
{  
    // Assume connection is an open SqlConnection.  
  
    // Create a new SqlCommand object.  
    using (SqlCommand command=new SqlCommand(  
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",   
        connection))  
    {  
  
        // Create a dependency and associate it with the SqlCommand.  
        SqlDependency dependency=new SqlDependency(command);  
        // Maintain the reference in a class member.  
  
        // Subscribe to the SqlDependency event.  
        dependency.OnChange+=new  
           OnChangeEventHandler(OnDependencyChange);  
  
        // Execute the command.  
        using (SqlDataReader reader = command.ExecuteReader())  
        {  
            // Process the DataReader.  
        }  
    }  
}  
  
// Handler method  
void OnDependencyChange(object sender,   
   SqlNotificationEventArgs e )  
{  
  // Handle the event (for example, invalidate this cache entry).  
}  
  
void Termination()  
{  
    // Release the dependency.  
    SqlDependency.Stop(connectionString, queueName);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba18f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba18f-127">See Also</span></span>  
 [<span data-ttu-id="ba18f-128">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="ba18f-128">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="ba18f-129">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="ba18f-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
