---
title: "建立連接"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 416d89aef35fef5dd0ac2bca92fb8a90d757a2d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="establishing-the-connection"></a><span data-ttu-id="35f66-102">建立連接</span><span class="sxs-lookup"><span data-stu-id="35f66-102">Establishing the Connection</span></span>
<span data-ttu-id="35f66-103">若要連接至 Microsoft SQL Server，請使用 .NET Framework Data Provider for SQL Server 的 <xref:System.Data.SqlClient.SqlConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="35f66-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="35f66-104">若要連接至 OLE DB 資料來源，請使用 .NET Framework Data Provider for OLE DB 的 <xref:System.Data.OleDb.OleDbConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="35f66-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="35f66-105">若要連接至 ODBC 資料來源，請使用 ODBC 的 .NET Framework 資料提供者的 <xref:System.Data.Odbc.OdbcConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="35f66-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="35f66-106">若要連接至 Oracle 資料來源，請使用 Oracle 的 .NET Framework 資料提供者的 <xref:System.Data.OracleClient.OracleConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="35f66-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="35f66-107">安全地儲存及擷取連接字串，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="35f66-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="35f66-108">關閉連接</span><span class="sxs-lookup"><span data-stu-id="35f66-108">Closing Connections</span></span>  
 <span data-ttu-id="35f66-109">建議您在使用完連接後一律關閉該連接，以便將連接傳回集區。</span><span class="sxs-lookup"><span data-stu-id="35f66-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="35f66-110">即使有未處理的例外狀況，Visual Basic 或 C# 中的 `Using` 區塊也會在程式碼結束該區塊時自動處理連接。</span><span class="sxs-lookup"><span data-stu-id="35f66-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="35f66-111">請參閱[使用陳述式](~/docs/csharp/language-reference/keywords/using-statement.md)和[Using 陳述式](~/docs/visual-basic/language-reference/statements/using-statement.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="35f66-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="35f66-112">您也可針對使用的提供者，使用連接物件的 `Close` 或 `Dispose` 方法。</span><span class="sxs-lookup"><span data-stu-id="35f66-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="35f66-113">可能不會將未明確關閉的連接加入或傳回集區。</span><span class="sxs-lookup"><span data-stu-id="35f66-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="35f66-114">例如，已離開範圍但尚未明確關閉的連接僅會在已達到最大集區大小，且連接仍然有效時，才會回到連接集區。</span><span class="sxs-lookup"><span data-stu-id="35f66-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="35f66-115">如需詳細資訊，請參閱[OLE DB、 ODBC 和 Oracle 連接共用](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="35f66-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35f66-116">請勿呼叫`Close`或`Dispose`上**連接**、 **DataReader**，或在任何其他 managed 的物件`Finalize`類別的方法。</span><span class="sxs-lookup"><span data-stu-id="35f66-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="35f66-117">在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="35f66-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="35f66-118">如果類別未擁有任何 Unmanaged 資源，請不要在類別定義中包含 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="35f66-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="35f66-119">如需詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="35f66-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35f66-120">從連接集區中擷取連接或將連接傳回連接集區時，系統不會在伺服器上引發登入和登出事件，因為當連接傳回連接集區時，連接實際上並未關閉。</span><span class="sxs-lookup"><span data-stu-id="35f66-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="35f66-121">如需詳細資訊，請參閱[SQL Server 連接共用 (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="35f66-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="35f66-122">連接至 SQL Server</span><span class="sxs-lookup"><span data-stu-id="35f66-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="35f66-123">SQL Server 的 .NET Framework 資料提供者支援與 OLE DB (ADO) 連接字串格式類似的連接字串格式。</span><span class="sxs-lookup"><span data-stu-id="35f66-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="35f66-124">如需有效的字串格式名稱及值，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性。</span><span class="sxs-lookup"><span data-stu-id="35f66-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="35f66-125">您也可以使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 類別在執行階段建立語法有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="35f66-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="35f66-126">如需詳細資訊，請參閱[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="35f66-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="35f66-127">下列程式碼範例示範如何建立及開啟與 SQL Server 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="35f66-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="35f66-128">整合安全性與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="35f66-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="35f66-129">SQL Server 整合安全性 (也稱為信任連接) 可在連接至 SQL Server 時，協助提供保護，因為它不會在連接字串中公開使用者 ID 及密碼，因此建議在驗證連接時使用。</span><span class="sxs-lookup"><span data-stu-id="35f66-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="35f66-130">整合安全性會使用執行中處理序的目前安全性識別或語彙基元。</span><span class="sxs-lookup"><span data-stu-id="35f66-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="35f66-131">對於桌面應用程式，這通常是目前已登入使用者的識別。</span><span class="sxs-lookup"><span data-stu-id="35f66-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="35f66-132">ASP.NET 應用程式的安全性識別可設為數個不同的選項之一。</span><span class="sxs-lookup"><span data-stu-id="35f66-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="35f66-133">若要進一步了解連接到 SQL Server 時，會使用 ASP.NET 應用程式的安全性識別，請參閱[ASP.NET 模擬](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d)， [ASP.NET 驗證](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)，和[如何： 存取 SQL伺服器使用 Windows 整合式安全性](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5)。</span><span class="sxs-lookup"><span data-stu-id="35f66-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET Authentication](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), and [How to: Access SQL Server Using Windows Integrated Security](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="35f66-134">連接至 OLE DB 資料來源</span><span class="sxs-lookup"><span data-stu-id="35f66-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="35f66-135">.NET Framework Data Provider for OLE DB 提供使用 OLE DB （透過 SQLOLEDB，OLE DB Provider for SQL Server)，公開的資料來源連接使用**OleDbConnection**物件。</span><span class="sxs-lookup"><span data-stu-id="35f66-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="35f66-136">對於 OLE DB 的 .NET Framework 資料提供者，連接字串格式與 ADO 中使用的連接字串格式相同，但下列情況例外：</span><span class="sxs-lookup"><span data-stu-id="35f66-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="35f66-137">**提供者**關鍵字是必要項。</span><span class="sxs-lookup"><span data-stu-id="35f66-137">The **Provider** keyword is required.</span></span>  
  
-   <span data-ttu-id="35f66-138">**URL**，**遠端提供者**，和**遠端伺服器**不支援的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="35f66-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="35f66-139">如需 OLE DB 連接字串的詳細資訊，請參閱 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 主題。</span><span class="sxs-lookup"><span data-stu-id="35f66-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="35f66-140">您也可以使用 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 在執行階段建立連接字串。</span><span class="sxs-lookup"><span data-stu-id="35f66-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35f66-141">**OleDbConnection**物件不支援設定或擷取特定的 OLE DB 提供者的動態屬性。</span><span class="sxs-lookup"><span data-stu-id="35f66-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="35f66-142">僅支援 OLE DB 提供者之連接字串中可傳遞的屬性。</span><span class="sxs-lookup"><span data-stu-id="35f66-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="35f66-143">下列程式碼範例說明如何建立及開啟與 OLE DB 資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="35f66-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="35f66-144">不使用通用資料連結檔</span><span class="sxs-lookup"><span data-stu-id="35f66-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="35f66-145">可提供連接資訊**OleDbConnection**在通用資料連結 (UDL) 檔案中; 但是您應該避免這樣。</span><span class="sxs-lookup"><span data-stu-id="35f66-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="35f66-146">UDL 檔並未加密，並且會以純文字的格式公開連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="35f66-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="35f66-147">因為對您的應用程式而言，UDL 檔是外部的檔案型資源，所以您無法使用 .NET Framework 來保護該檔案。</span><span class="sxs-lookup"><span data-stu-id="35f66-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="35f66-148">連接至 ODBC 資料來源</span><span class="sxs-lookup"><span data-stu-id="35f66-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="35f66-149">.NET Framework Data Provider for ODBC 提供公開使用 ODBC 資料來源的連接能力**OdbcConnection**物件。</span><span class="sxs-lookup"><span data-stu-id="35f66-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="35f66-150">對於 ODBC 的 .NET Framework 資料提供者，會將連接字串格式設計為儘可能與 ODBC 連接字串格式相符。</span><span class="sxs-lookup"><span data-stu-id="35f66-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="35f66-151">您也可以提供 ODBC 資料來源名稱 (DSN)。</span><span class="sxs-lookup"><span data-stu-id="35f66-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="35f66-152">如需詳細資訊，在**OdbcConnection** ，請參閱<xref:System.Data.Odbc.OdbcConnection>。</span><span class="sxs-lookup"><span data-stu-id="35f66-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="35f66-153">下列程式碼範例說明如何建立及開啟與 ODBC 資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="35f66-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="35f66-154">連接至 Oracle 資料來源</span><span class="sxs-lookup"><span data-stu-id="35f66-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="35f66-155">.NET Framework Data Provider for Oracle 提供的 Oracle 資料來源使用的連接能力**OracleConnection**物件。</span><span class="sxs-lookup"><span data-stu-id="35f66-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="35f66-156">對於 Oracle 的 .NET Framework 資料提供者，會將連接字串格式設計為儘可能與 Oracle OLE DB 提供者 (MSDAORA) 連接字串格式相符。</span><span class="sxs-lookup"><span data-stu-id="35f66-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="35f66-157">如需詳細資訊，在**OracleConnection**，請參閱<xref:System.Data.OracleClient.OracleConnection>。</span><span class="sxs-lookup"><span data-stu-id="35f66-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="35f66-158">下列程式碼範例說明如何建立及開啟與 Oracle 資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="35f66-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="35f66-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="35f66-159">See Also</span></span>  
 [<span data-ttu-id="35f66-160">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="35f66-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="35f66-161">連接字串</span><span class="sxs-lookup"><span data-stu-id="35f66-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="35f66-162">OLE DB、ODBC 和 Oracle 連接共用</span><span class="sxs-lookup"><span data-stu-id="35f66-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="35f66-163">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="35f66-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
