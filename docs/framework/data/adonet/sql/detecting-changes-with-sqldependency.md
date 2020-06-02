---
title: 使用 SqlDependency 偵測變更
description: 將 SqlDependency 物件與 SqlCommand 建立關聯，以偵測查詢結果與 ADO.NET 中原本抓取時的不同。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: b196d42477e1778c45df64b1390502645fdd649d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286464"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="d7a35-103">使用 SqlDependency 偵測變更</span><span class="sxs-lookup"><span data-stu-id="d7a35-103">Detecting Changes with SqlDependency</span></span>

<span data-ttu-id="d7a35-104"><xref:System.Data.SqlClient.SqlDependency> 物件可以與 <xref:System.Data.SqlClient.SqlCommand> 相關聯，以偵測查詢結果與原先擷取的結果是否不同。</span><span class="sxs-lookup"><span data-stu-id="d7a35-104">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="d7a35-105">您也可以將委派指派給 `OnChange` 事件，這會在相關聯命令的結果變更時引發。</span><span class="sxs-lookup"><span data-stu-id="d7a35-105">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="d7a35-106">執行命令之前，必須先將 <xref:System.Data.SqlClient.SqlDependency> 與命令建立關聯。</span><span class="sxs-lookup"><span data-stu-id="d7a35-106">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="d7a35-107"><xref:System.Data.SqlClient.SqlDependency> 的 `HasChanges` 屬性也可以用來判斷自第一次擷取資料之後，查詢結果是否已經變更。</span><span class="sxs-lookup"><span data-stu-id="d7a35-107">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="d7a35-108">安全性考量</span><span class="sxs-lookup"><span data-stu-id="d7a35-108">Security Considerations</span></span>

<span data-ttu-id="d7a35-109">相依性基礎結構會依賴呼叫 <xref:System.Data.SqlClient.SqlDependency.Start%2A> 時開啟的 <xref:System.Data.SqlClient.SqlConnection>，以便接收底層資料已針對指定命令變更的通知。</span><span class="sxs-lookup"><span data-stu-id="d7a35-109">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="d7a35-110">用戶端起始呼叫 `SqlDependency.Start` 的能力是透過使用 <xref:System.Data.SqlClient.SqlClientPermission> 和程式碼存取安全性屬性來控制的。</span><span class="sxs-lookup"><span data-stu-id="d7a35-110">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="d7a35-111">如需詳細資訊，請參閱[啟用查詢通知](enabling-query-notifications.md)和[代碼啟用安全性和 ADO.NET](../code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="d7a35-111">For more information, see [Enabling Query Notifications](enabling-query-notifications.md) and [Code Access Security and ADO.NET](../code-access-security.md).</span></span>

### <a name="example"></a><span data-ttu-id="d7a35-112">範例</span><span class="sxs-lookup"><span data-stu-id="d7a35-112">Example</span></span>

<span data-ttu-id="d7a35-113">下列步驟說明如何宣告相依性、執行命令，並在結果集變更時收到通知：</span><span class="sxs-lookup"><span data-stu-id="d7a35-113">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>

1. <span data-ttu-id="d7a35-114">起始與伺服器的 `SqlDependency` 連線。</span><span class="sxs-lookup"><span data-stu-id="d7a35-114">Initiate a `SqlDependency` connection to the server.</span></span>

2. <span data-ttu-id="d7a35-115">建立 <xref:System.Data.SqlClient.SqlConnection> 與 <xref:System.Data.SqlClient.SqlCommand> 物件，以連接到伺服器並定義 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d7a35-115">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>

3. <span data-ttu-id="d7a35-116">建立新 `SqlDependency` 物件或使用現有物件，並將其繫結至 `SqlCommand` 物件。</span><span class="sxs-lookup"><span data-stu-id="d7a35-116">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="d7a35-117">就內部而言，這會建立一個 <xref:System.Data.Sql.SqlNotificationRequest> 物件，並視需要將其繫結至命令物件。</span><span class="sxs-lookup"><span data-stu-id="d7a35-117">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="d7a35-118">此通知要求包含可唯一識別此 `SqlDependency` 物件的內部識別碼。</span><span class="sxs-lookup"><span data-stu-id="d7a35-118">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="d7a35-119">如果用戶端接聽程式尚未啟用，也會加以啟用。</span><span class="sxs-lookup"><span data-stu-id="d7a35-119">It also starts the client listener if it is not already active.</span></span>

4. <span data-ttu-id="d7a35-120">訂閱 `SqlDependency` 物件之 `OnChange` 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d7a35-120">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>

5. <span data-ttu-id="d7a35-121">使用 `SqlCommand` 物件的任何 `Execute` 方法來執行命令。</span><span class="sxs-lookup"><span data-stu-id="d7a35-121">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="d7a35-122">因為命令已繫結至通知物件，所以伺服器了解必須產生通知，而且佇列資訊將指向相依性佇列。</span><span class="sxs-lookup"><span data-stu-id="d7a35-122">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>

6. <span data-ttu-id="d7a35-123">停止對伺服器的 `SqlDependency` 連線。</span><span class="sxs-lookup"><span data-stu-id="d7a35-123">Stop the `SqlDependency` connection to the server.</span></span>

<span data-ttu-id="d7a35-124">如果有任何使用者後續變更底層資料，Microsoft SQL Server 會偵測到有此類變更的待處理通知，並透過藉由呼叫 `SqlDependency.Start` 所建立的底層 `SqlConnection`，張貼已處理並轉送到用戶端的通知。</span><span class="sxs-lookup"><span data-stu-id="d7a35-124">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="d7a35-125">用戶端接聽程式會接收到失效訊息。</span><span class="sxs-lookup"><span data-stu-id="d7a35-125">The client listener receives the invalidation message.</span></span> <span data-ttu-id="d7a35-126">然後，用戶端接聽程式會找出相關聯的 `SqlDependency` 物件，並引發 `OnChange` 事件。</span><span class="sxs-lookup"><span data-stu-id="d7a35-126">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>

<span data-ttu-id="d7a35-127">下列程式碼片段顯示您會用來建立範例應用程式的設計模式。</span><span class="sxs-lookup"><span data-stu-id="d7a35-127">The following code fragment shows the design pattern you would use to create a sample application.</span></span>

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
        ' Maintain the refernce in a class member.
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

## <a name="see-also"></a><span data-ttu-id="d7a35-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7a35-128">See also</span></span>

- [<span data-ttu-id="d7a35-129">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="d7a35-129">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- <span data-ttu-id="d7a35-130">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="d7a35-130">[ADO.NET Overview](../ado-net-overview.md)</span></span>
