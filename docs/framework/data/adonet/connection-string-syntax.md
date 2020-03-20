---
title: 連接字串語法
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 3df97419391fe17ef77a3b8f24c4f0689a04602f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151646"
---
# <a name="connection-string-syntax"></a><span data-ttu-id="f8181-102">連接字串語法</span><span class="sxs-lookup"><span data-stu-id="f8181-102">Connection String Syntax</span></span>
<span data-ttu-id="f8181-103">每個 .NET Framework 資料提供者都擁有一個 `Connection` 物件，繼承自 <xref:System.Data.Common.DbConnection> 以及提供者特定的 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f8181-103">Each .NET Framework data provider has a `Connection` object that inherits from <xref:System.Data.Common.DbConnection> as well as a provider-specific <xref:System.Data.Common.DbConnection.ConnectionString%2A> property.</span></span> <span data-ttu-id="f8181-104">每個提供者的特定連接字串語法會記錄在其 `ConnectionString` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="f8181-104">The specific connection string syntax for each provider is documented in its `ConnectionString` property.</span></span> <span data-ttu-id="f8181-105">下表列出 .NET Framework 中包含的四個資料提供者。</span><span class="sxs-lookup"><span data-stu-id="f8181-105">The following table lists the four data providers that are included in the .NET Framework.</span></span>  
  
|<span data-ttu-id="f8181-106">.NET Framework Data Provider - .NET Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="f8181-106">.NET Framework data provider</span></span>|<span data-ttu-id="f8181-107">描述</span><span class="sxs-lookup"><span data-stu-id="f8181-107">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|<span data-ttu-id="f8181-108">提供 Microsoft SQL Server 的資料存取。</span><span class="sxs-lookup"><span data-stu-id="f8181-108">Provides data access for Microsoft SQL Server.</span></span> <span data-ttu-id="f8181-109">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="f8181-109">For more information on connection string syntax, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OleDb>|<span data-ttu-id="f8181-110">為使用 OLE DB 所公開的資料來源提供資料存取。</span><span class="sxs-lookup"><span data-stu-id="f8181-110">Provides data access for data sources exposed using OLE DB.</span></span> <span data-ttu-id="f8181-111">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="f8181-111">For more information on connection string syntax, see <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.Odbc>|<span data-ttu-id="f8181-112">為使用 ODBC 所公開的資料來源提供資料存取。</span><span class="sxs-lookup"><span data-stu-id="f8181-112">Provides data access for data sources exposed using ODBC.</span></span> <span data-ttu-id="f8181-113">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="f8181-113">For more information on connection string syntax, see <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OracleClient>|<span data-ttu-id="f8181-114">提供 Oracle 8.1.7 (含) 以後版本的資料存取。</span><span class="sxs-lookup"><span data-stu-id="f8181-114">Provides data access for Oracle version 8.1.7 or later.</span></span> <span data-ttu-id="f8181-115">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="f8181-115">For more information on connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>|  
  
## <a name="connection-string-builders"></a><span data-ttu-id="f8181-116">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="f8181-116">Connection String Builders</span></span>  
 <span data-ttu-id="f8181-117">ADO.NET 2.0 針對 .NET Framework 資料提供者導入了下列連接字串產生器 (Builder)。</span><span class="sxs-lookup"><span data-stu-id="f8181-117">ADO.NET 2.0 introduced the following connection string builders for the .NET Framework data providers.</span></span>  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 <span data-ttu-id="f8181-118">連接字串產生器可讓您在執行階段建構語法有效的連接字串，所以您不需要在程式碼中手動串連連接字串值。</span><span class="sxs-lookup"><span data-stu-id="f8181-118">The connection string builders allow you to construct syntactically valid connection strings at run time, so you do not have to manually concatenate connection string values in your code.</span></span> <span data-ttu-id="f8181-119">如需詳細資訊，請參閱[連接字串建置器](connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="f8181-119">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  

## <a name="windows-authentication"></a><span data-ttu-id="f8181-120">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="f8181-120">Windows Authentication</span></span>  
 <span data-ttu-id="f8181-121">我們建議使用 Windows 身份驗證（有時稱為*集成安全性*）連接到支援它的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f8181-121">We recommend using Windows Authentication (sometimes referred to as *integrated security*) to connect to data sources that support it.</span></span> <span data-ttu-id="f8181-122">連接字串所使用的語法隨提供者而異。</span><span class="sxs-lookup"><span data-stu-id="f8181-122">The syntax employed in the connection string varies by provider.</span></span> <span data-ttu-id="f8181-123">下列表格說明搭配 .NET Framework 資料提供者使用的「Windows 驗證」語法。</span><span class="sxs-lookup"><span data-stu-id="f8181-123">The following table shows the Windows Authentication syntax used with the .NET Framework data providers.</span></span>  
  
|<span data-ttu-id="f8181-124">提供者</span><span class="sxs-lookup"><span data-stu-id="f8181-124">Provider</span></span>|<span data-ttu-id="f8181-125">語法</span><span class="sxs-lookup"><span data-stu-id="f8181-125">Syntax</span></span>|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> <span data-ttu-id="f8181-126">與 `Integrated Security=true` 提供者搭配使用時，`OleDb` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8181-126">`Integrated Security=true` throws an exception when used with the `OleDb` provider.</span></span>  
  
## <a name="sqlclient-connection-strings"></a><span data-ttu-id="f8181-127">SqlClient 連接字串</span><span class="sxs-lookup"><span data-stu-id="f8181-127">SqlClient Connection Strings</span></span>  
<span data-ttu-id="f8181-128"><xref:System.Data.SqlClient.SqlConnection> 連接字串的語法列於 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="f8181-128">The syntax for a <xref:System.Data.SqlClient.SqlConnection> connection string is documented in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f8181-129">您可以使用 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 屬性來取得或設定 SQL Server 資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="f8181-129">You can use the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property to get or set a connection string for a SQL Server database.</span></span> <span data-ttu-id="f8181-130">如果您需要連接至舊版的 SQL Server，則必須使用 .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>)。</span><span class="sxs-lookup"><span data-stu-id="f8181-130">If you need to connect to an earlier version of SQL Server, you must use the .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>).</span></span> <span data-ttu-id="f8181-131">大多數的連接字串關鍵字也可對應至 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f8181-131">Most connection string keywords also map to properties in the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="f8181-132">關鍵字的`Persist Security Info`預設設置為`false`。</span><span class="sxs-lookup"><span data-stu-id="f8181-132">The default setting for the `Persist Security Info` keyword is `false`.</span></span> <span data-ttu-id="f8181-133">如果將其設為 `true` 或 `yes`，則在開啟連接後，可透過連接獲得機密資訊，包含使用者 ID 和密碼。</span><span class="sxs-lookup"><span data-stu-id="f8181-133">Setting it to `true` or `yes` allows security-sensitive information, including the user ID and password, to be obtained from the connection after the connection has been opened.</span></span> <span data-ttu-id="f8181-134">保持`Persist Security Info`設置`false`以確保不受信任的源無法訪問敏感的連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="f8181-134">Keep `Persist Security Info` set to `false` to ensure that an untrusted source does not have access to sensitive connection string information.</span></span>  

### <a name="windows-authentication-with-sqlclient"></a><span data-ttu-id="f8181-135">使用 SqlClient 進行 Windows 身份驗證</span><span class="sxs-lookup"><span data-stu-id="f8181-135">Windows authentication with SqlClient</span></span>
 <span data-ttu-id="f8181-136">以下每種語法形式都使用 Windows 身份驗證連接到本機伺服器上的**AdventureWorks**資料庫。</span><span class="sxs-lookup"><span data-stu-id="f8181-136">Each of the following forms of syntax uses Windows Authentication to connect to the **AdventureWorks** database on a local server.</span></span>  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a><span data-ttu-id="f8181-137">SQL Server 身份驗證與 SqlClient</span><span class="sxs-lookup"><span data-stu-id="f8181-137">SQL Server authentication with SqlClient</span></span>
 <span data-ttu-id="f8181-138">連接至 SQL Server 時慣用「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="f8181-138">Windows Authentication is preferred for connecting to SQL Server.</span></span> <span data-ttu-id="f8181-139">不過，如果需要「SQL Server 驗證」，請使用下列語法來指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="f8181-139">However, if SQL Server Authentication is required, use the following syntax to specify a user name and password.</span></span> <span data-ttu-id="f8181-140">在這個範例中使用了星號來表示有效的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="f8181-140">In this example, asterisks are used to represent a valid user name and password.</span></span>  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

<span data-ttu-id="f8181-141">當您連接到 Azure SQL 資料庫或 Azure SQL 資料倉儲並提供格式`user@servername`的登錄名時，請確保登錄`servername`名中的值與 提供`Server=`的值匹配。</span><span class="sxs-lookup"><span data-stu-id="f8181-141">When you connect to Azure SQL Database or to Azure SQL Data Warehouse and provide a login in the format `user@servername`, make sure that the `servername` value in the login matches the value provided for `Server=`.</span></span>

> [!NOTE]
> <span data-ttu-id="f8181-142">Windows 驗證的優先順序高於 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="f8181-142">Windows authentication takes precedence over SQL Server logins.</span></span> <span data-ttu-id="f8181-143">如果您同時指定 Integrated Security=true 以及使用者名稱和密碼，系統就會忽略使用者名稱和密碼，而使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="f8181-143">If you specify both Integrated Security=true as well as a user name and password, the user name and password will be ignored and Windows authentication will be used.</span></span>  

### <a name="connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="f8181-144">連接到 SQL Server 的命名實例</span><span class="sxs-lookup"><span data-stu-id="f8181-144">Connect to a named instance of SQL Server</span></span>
<span data-ttu-id="f8181-145">要連接到 SQL Server 的命名實例，請使用*伺服器名稱\實例名稱*語法。</span><span class="sxs-lookup"><span data-stu-id="f8181-145">To connect to a named instance of SQL Server, use the *server name\instance name* syntax.</span></span>  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

<span data-ttu-id="f8181-146">您也可以在建立連接字串時，將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> 的 `SqlConnectionStringBuilder` 屬性設定為執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="f8181-146">You can also set the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> property of the `SqlConnectionStringBuilder` to the instance name when building a connection string.</span></span> <span data-ttu-id="f8181-147"><xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f8181-147">The <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object is read-only.</span></span>  
  
### <a name="type-system-version-changes"></a><span data-ttu-id="f8181-148">型別系統版本變更</span><span class="sxs-lookup"><span data-stu-id="f8181-148">Type System Version Changes</span></span>  
 <span data-ttu-id="f8181-149">中的`Type System Version`關鍵字<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>指定 SQL Server 類型的用戶端表示形式。</span><span class="sxs-lookup"><span data-stu-id="f8181-149">The `Type System Version` keyword in a <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> specifies the client-side representation of SQL Server types.</span></span> <span data-ttu-id="f8181-150">如需 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 關鍵字的詳細資訊，請參閱 `Type System Version`。</span><span class="sxs-lookup"><span data-stu-id="f8181-150">See <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> for more information about the `Type System Version` keyword.</span></span>  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a><span data-ttu-id="f8181-151">連接和附加至 SQL Server Express 使用者執行個體</span><span class="sxs-lookup"><span data-stu-id="f8181-151">Connecting and Attaching to SQL Server Express User Instances</span></span>  
 <span data-ttu-id="f8181-152">使用者執行個體是 SQL Server Express 中的功能。</span><span class="sxs-lookup"><span data-stu-id="f8181-152">User instances are a feature in SQL Server Express.</span></span> <span data-ttu-id="f8181-153">透過使用者執行個體，在最低權限的本機 Windows 帳戶上執行的使用者不需要系統管理員權限，即可附加及執行 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f8181-153">They allow a user running on a least-privileged local Windows account to attach and run a SQL Server database without requiring administrative privileges.</span></span> <span data-ttu-id="f8181-154">使用者執行個體會使用使用者的 Windows 認證執行，而不是以服務方式執行。</span><span class="sxs-lookup"><span data-stu-id="f8181-154">A user instance executes with the user's Windows credentials, not as a service.</span></span>  
  
 <span data-ttu-id="f8181-155">有關使用使用者實例的詳細資訊，請參閱[SQL Server Express 使用者實例](./sql/sql-server-express-user-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="f8181-155">For more information on working with user instances, see [SQL Server Express User Instances](./sql/sql-server-express-user-instances.md).</span></span>  
  
## <a name="using-trustservercertificate"></a><span data-ttu-id="f8181-156">使用 TrustServerCertificate</span><span class="sxs-lookup"><span data-stu-id="f8181-156">Using TrustServerCertificate</span></span>  
 <span data-ttu-id="f8181-157">僅當`TrustServerCertificate`使用有效證書連接到 SQL Server 實例時，關鍵字才有效。</span><span class="sxs-lookup"><span data-stu-id="f8181-157">The `TrustServerCertificate` keyword is valid only when connecting to a SQL Server instance with a valid certificate.</span></span> <span data-ttu-id="f8181-158">當 `TrustServerCertificate` 設定為 `true` 時，傳輸層 (Transport Layer) 會使用 SSL 來加密通道，而略過逐一檢查憑證鏈結以驗證信任的作業。</span><span class="sxs-lookup"><span data-stu-id="f8181-158">When `TrustServerCertificate` is set to `true`, the transport layer will use SSL to encrypt the channel and bypass walking the certificate chain to validate trust.</span></span>  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="f8181-159">如果 `TrustServerCertificate` 是設定為 `true` 且加密功能已開啟，則即使 `Encrypt` 在連接字串中是設定為 `false`，仍將使用伺服器上指定的加密等級，</span><span class="sxs-lookup"><span data-stu-id="f8181-159">If `TrustServerCertificate` is set to `true` and encryption is turned on, the encryption level specified on the server will be used even if `Encrypt` is set to `false` in the connection string.</span></span> <span data-ttu-id="f8181-160">否則連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f8181-160">The connection will fail otherwise.</span></span>  
  
### <a name="enabling-encryption"></a><span data-ttu-id="f8181-161">啟用加密</span><span class="sxs-lookup"><span data-stu-id="f8181-161">Enabling Encryption</span></span>  
 <span data-ttu-id="f8181-162">要在伺服器上未預配證書時啟用加密，必須在 SQL 伺服器組態管理員中設置**強制協定加密\*\*\*\*和信任伺服器憑證**選項。</span><span class="sxs-lookup"><span data-stu-id="f8181-162">To enable encryption when a certificate has not been provisioned on the server, the **Force Protocol Encryption** and the **Trust Server Certificate** options must be set in SQL Server Configuration Manager.</span></span> <span data-ttu-id="f8181-163">在此情況下，如果伺服器上未提供任何可驗證的憑證，加密將會使用自行簽署的伺服器憑證，而不需驗證。</span><span class="sxs-lookup"><span data-stu-id="f8181-163">In this case, encryption will use a self-signed server certificate without validation if no verifiable certificate has been provisioned on the server.</span></span>  
  
 <span data-ttu-id="f8181-164">應用程式設定無法降低 SQL Server 中設定的安全性層級，但可以選擇性地進行加強。</span><span class="sxs-lookup"><span data-stu-id="f8181-164">Application settings cannot reduce the level of security configured in SQL Server, but can optionally strengthen it.</span></span> <span data-ttu-id="f8181-165">應用程式可以通過將`TrustServerCertificate`和`Encrypt`關鍵字設置為 來請求`true`加密，從而保證即使在尚未預配伺服器憑證且尚未為用戶端配置**強制協定加密**的情況下也會進行加密。</span><span class="sxs-lookup"><span data-stu-id="f8181-165">An application can request encryption by setting the `TrustServerCertificate` and `Encrypt` keywords to `true`, guaranteeing that encryption takes place even when a server certificate has not been provisioned and **Force Protocol Encryption** has not been configured for the client.</span></span> <span data-ttu-id="f8181-166">不過，如果用戶端組態中未啟用 `TrustServerCertificate`，則仍需要提供伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="f8181-166">However, if `TrustServerCertificate` is not enabled in the client configuration, a provisioned server certificate is still required.</span></span>  
  
 <span data-ttu-id="f8181-167">下表說明所有案例。</span><span class="sxs-lookup"><span data-stu-id="f8181-167">The following table describes all cases.</span></span>  
  
|<span data-ttu-id="f8181-168">強制通訊協定加密用戶端設定</span><span class="sxs-lookup"><span data-stu-id="f8181-168">Force Protocol Encryption client setting</span></span>|<span data-ttu-id="f8181-169">信任伺服器憑證用戶端設定</span><span class="sxs-lookup"><span data-stu-id="f8181-169">Trust Server Certificate client setting</span></span>|<span data-ttu-id="f8181-170">資料連接字串/屬性的加密/使用加密</span><span class="sxs-lookup"><span data-stu-id="f8181-170">Encrypt/Use Encryption for Data connection string/attribute</span></span>|<span data-ttu-id="f8181-171">信任伺服器憑證連接字串/屬性</span><span class="sxs-lookup"><span data-stu-id="f8181-171">Trust Server Certificate connection string/attribute</span></span>|<span data-ttu-id="f8181-172">結果</span><span class="sxs-lookup"><span data-stu-id="f8181-172">Result</span></span>|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|<span data-ttu-id="f8181-173">否</span><span class="sxs-lookup"><span data-stu-id="f8181-173">No</span></span>|<span data-ttu-id="f8181-174">N/A</span><span class="sxs-lookup"><span data-stu-id="f8181-174">N/A</span></span>|<span data-ttu-id="f8181-175">無 (預設值)</span><span class="sxs-lookup"><span data-stu-id="f8181-175">No (default)</span></span>|<span data-ttu-id="f8181-176">忽略</span><span class="sxs-lookup"><span data-stu-id="f8181-176">Ignored</span></span>|<span data-ttu-id="f8181-177">不發生任何加密。</span><span class="sxs-lookup"><span data-stu-id="f8181-177">No encryption occurs.</span></span>|  
|<span data-ttu-id="f8181-178">否</span><span class="sxs-lookup"><span data-stu-id="f8181-178">No</span></span>|<span data-ttu-id="f8181-179">N/A</span><span class="sxs-lookup"><span data-stu-id="f8181-179">N/A</span></span>|<span data-ttu-id="f8181-180">是</span><span class="sxs-lookup"><span data-stu-id="f8181-180">Yes</span></span>|<span data-ttu-id="f8181-181">無 (預設值)</span><span class="sxs-lookup"><span data-stu-id="f8181-181">No (default)</span></span>|<span data-ttu-id="f8181-182">只有當有可驗證的伺服器憑證時才會發生加密，否則連接嘗試會失敗。</span><span class="sxs-lookup"><span data-stu-id="f8181-182">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="f8181-183">否</span><span class="sxs-lookup"><span data-stu-id="f8181-183">No</span></span>|<span data-ttu-id="f8181-184">N/A</span><span class="sxs-lookup"><span data-stu-id="f8181-184">N/A</span></span>|<span data-ttu-id="f8181-185">是</span><span class="sxs-lookup"><span data-stu-id="f8181-185">Yes</span></span>|<span data-ttu-id="f8181-186">是</span><span class="sxs-lookup"><span data-stu-id="f8181-186">Yes</span></span>|<span data-ttu-id="f8181-187">加密一定會發生，但是可能會使用自行簽署的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="f8181-187">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
|<span data-ttu-id="f8181-188">是</span><span class="sxs-lookup"><span data-stu-id="f8181-188">Yes</span></span>|<span data-ttu-id="f8181-189">否</span><span class="sxs-lookup"><span data-stu-id="f8181-189">No</span></span>|<span data-ttu-id="f8181-190">忽略</span><span class="sxs-lookup"><span data-stu-id="f8181-190">Ignored</span></span>|<span data-ttu-id="f8181-191">忽略</span><span class="sxs-lookup"><span data-stu-id="f8181-191">Ignored</span></span>|<span data-ttu-id="f8181-192">僅當存在可驗證的伺服器憑證時，才會進行加密;否則，連接嘗試失敗。</span><span class="sxs-lookup"><span data-stu-id="f8181-192">Encryption occurs only if there is a verifiable server certificate; otherwise, the connection attempt fails.</span></span>|  
|<span data-ttu-id="f8181-193">是</span><span class="sxs-lookup"><span data-stu-id="f8181-193">Yes</span></span>|<span data-ttu-id="f8181-194">是</span><span class="sxs-lookup"><span data-stu-id="f8181-194">Yes</span></span>|<span data-ttu-id="f8181-195">無 (預設值)</span><span class="sxs-lookup"><span data-stu-id="f8181-195">No (default)</span></span>|<span data-ttu-id="f8181-196">忽略</span><span class="sxs-lookup"><span data-stu-id="f8181-196">Ignored</span></span>|<span data-ttu-id="f8181-197">加密一定會發生，但是可能會使用自行簽署的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="f8181-197">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
|<span data-ttu-id="f8181-198">是</span><span class="sxs-lookup"><span data-stu-id="f8181-198">Yes</span></span>|<span data-ttu-id="f8181-199">是</span><span class="sxs-lookup"><span data-stu-id="f8181-199">Yes</span></span>|<span data-ttu-id="f8181-200">是</span><span class="sxs-lookup"><span data-stu-id="f8181-200">Yes</span></span>|<span data-ttu-id="f8181-201">無 (預設值)</span><span class="sxs-lookup"><span data-stu-id="f8181-201">No (default)</span></span>|<span data-ttu-id="f8181-202">僅當存在可驗證的伺服器憑證時，才會進行加密;否則，連接嘗試失敗。</span><span class="sxs-lookup"><span data-stu-id="f8181-202">Encryption occurs only if there is a verifiable server certificate; otherwise, the connection attempt fails.</span></span>|  
|<span data-ttu-id="f8181-203">是</span><span class="sxs-lookup"><span data-stu-id="f8181-203">Yes</span></span>|<span data-ttu-id="f8181-204">是</span><span class="sxs-lookup"><span data-stu-id="f8181-204">Yes</span></span>|<span data-ttu-id="f8181-205">是</span><span class="sxs-lookup"><span data-stu-id="f8181-205">Yes</span></span>|<span data-ttu-id="f8181-206">是</span><span class="sxs-lookup"><span data-stu-id="f8181-206">Yes</span></span>|<span data-ttu-id="f8181-207">加密一定會發生，但是可能會使用自行簽署的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="f8181-207">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
  
 <span data-ttu-id="f8181-208">如需詳細資訊，請參閱[使用加密而不需驗證](/sql/relational-databases/native-client/features/using-encryption-without-validation)。</span><span class="sxs-lookup"><span data-stu-id="f8181-208">For more information, see [Using Encryption Without Validation](/sql/relational-databases/native-client/features/using-encryption-without-validation).</span></span>
  
## <a name="oledb-connection-strings"></a><span data-ttu-id="f8181-209">OleDb 連接字串</span><span class="sxs-lookup"><span data-stu-id="f8181-209">OleDb Connection Strings</span></span>  
 <span data-ttu-id="f8181-210"><xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 的 <xref:System.Data.OleDb.OleDbConnection> 屬性可讓您取得或設定 OLE DB 資料來源 (例如 Microsoft Access) 的連接字串。</span><span class="sxs-lookup"><span data-stu-id="f8181-210">The <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> property of a <xref:System.Data.OleDb.OleDbConnection> allows you to get or set a connection string for an OLE DB data source, such as Microsoft Access.</span></span> <span data-ttu-id="f8181-211">您也可以使用 `OleDb` 類別 (Class)，在執行階段建立 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 連接字串。</span><span class="sxs-lookup"><span data-stu-id="f8181-211">You can also create an `OleDb` connection string at run time by using the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> class.</span></span>  
  
### <a name="oledb-connection-string-syntax"></a><span data-ttu-id="f8181-212">OleDb 連接字串語法</span><span class="sxs-lookup"><span data-stu-id="f8181-212">OleDb Connection String Syntax</span></span>  
 <span data-ttu-id="f8181-213">您必須指定 <xref:System.Data.OleDb.OleDbConnection> 連接字串的提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="f8181-213">You must specify a provider name for an <xref:System.Data.OleDb.OleDbConnection> connection string.</span></span> <span data-ttu-id="f8181-214">下列連接字串會使用 Jet 提供者連接至 Microsoft Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f8181-214">The following connection string connects to a Microsoft Access database using the Jet provider.</span></span> <span data-ttu-id="f8181-215">請注意，如果資料庫未受保護 (預設值)，則 `User ID` 及 `Password` 關鍵字是選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f8181-215">Note that the `User ID` and `Password` keywords are optional if the database is unsecured (the default).</span></span>  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 <span data-ttu-id="f8181-216">如果您使用使用者層級安全性保護 Jet 資料庫的安全，則必須提供工作群組資訊檔 (.mdw) 的位置。</span><span class="sxs-lookup"><span data-stu-id="f8181-216">If the Jet database is secured using user-level security, you must provide the location of the workgroup information file (.mdw).</span></span> <span data-ttu-id="f8181-217">工作群組資訊檔是用於驗證連接字串中提供的認證。</span><span class="sxs-lookup"><span data-stu-id="f8181-217">The workgroup information file is used to validate the credentials presented in the connection string.</span></span>  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f8181-218">可以在通用資料連結 （UDL） 檔中為**OleDbConnection**提供連接資訊;但是，您應該避免這樣做。</span><span class="sxs-lookup"><span data-stu-id="f8181-218">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="f8181-219">UDL 檔並未加密，並且會以純文字的格式公開連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="f8181-219">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="f8181-220">因為對您的應用程式而言，UDL 檔是外部的檔案型資源，所以您無法使用 .NET Framework 來保護該檔案。</span><span class="sxs-lookup"><span data-stu-id="f8181-220">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span> <span data-ttu-id="f8181-221">**SqlClient**不支援 UDL 檔。</span><span class="sxs-lookup"><span data-stu-id="f8181-221">UDL files are not supported for **SqlClient**.</span></span>  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a><span data-ttu-id="f8181-222">使用 DataDirectory 連接至 Access/Jet</span><span class="sxs-lookup"><span data-stu-id="f8181-222">Using DataDirectory to Connect to Access/Jet</span></span>  
 <span data-ttu-id="f8181-223">`DataDirectory` 並不是由 `SqlClient` 所獨佔，</span><span class="sxs-lookup"><span data-stu-id="f8181-223">`DataDirectory` is not exclusive to `SqlClient`.</span></span> <span data-ttu-id="f8181-224">也可以搭配 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> .NET data 提供者使用。</span><span class="sxs-lookup"><span data-stu-id="f8181-224">It can also be used with the <xref:System.Data.OleDb> and <xref:System.Data.Odbc> .NET data providers.</span></span> <span data-ttu-id="f8181-225">下列範例 <xref:System.Data.OleDb.OleDbConnection> 字串所示範的語法，是連接到位於應用程式的 app_data 資料夾中的 Northwind.mdb 所需。</span><span class="sxs-lookup"><span data-stu-id="f8181-225">The following sample <xref:System.Data.OleDb.OleDbConnection> string demonstrates the syntax required to connect to the Northwind.mdb located in the application's app_data folder.</span></span> <span data-ttu-id="f8181-226">系統資料庫 (System.mdw) 也是儲存於該位置。</span><span class="sxs-lookup"><span data-stu-id="f8181-226">The system database (System.mdw) is also stored in that location.</span></span>  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f8181-227">如果 Access/Jet 資料庫未受保護，則不需要在連接字串中指定系統資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="f8181-227">Specifying the location of the system database in the connection string is not required if the Access/Jet database is unsecured.</span></span> <span data-ttu-id="f8181-228">安全性預設為關閉，且所有連接的使用者都是使用空白密碼的內建 Admin 使用者。</span><span class="sxs-lookup"><span data-stu-id="f8181-228">Security is off by default, with all users connecting as the built-in Admin user with a blank password.</span></span> <span data-ttu-id="f8181-229">即使已正確地實作使用者層級的安全性，Jet 資料庫仍很容易受到攻擊。</span><span class="sxs-lookup"><span data-stu-id="f8181-229">Even when user-level security is correctly implemented, a Jet database remains vulnerable to attack.</span></span> <span data-ttu-id="f8181-230">因此，不建議在 Access/Jet 資料庫中儲存機密資訊，因為其檔案架構的安全性配置原本就有弱點。</span><span class="sxs-lookup"><span data-stu-id="f8181-230">Therefore, storing sensitive information in an Access/Jet database is not recommended because of the inherent weakness of its file-based security scheme.</span></span>  
  
### <a name="connecting-to-excel"></a><span data-ttu-id="f8181-231">連接至 Excel</span><span class="sxs-lookup"><span data-stu-id="f8181-231">Connecting to Excel</span></span>  
 <span data-ttu-id="f8181-232">Microsoft Jet 提供者可用於連接至 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="f8181-232">The Microsoft Jet provider is used to connect to an Excel workbook.</span></span> <span data-ttu-id="f8181-233">在下列連接字串中，由 `Extended Properties` 關鍵字設定 Excel 特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="f8181-233">In the following connection string, the `Extended Properties` keyword sets properties that are specific to Excel.</span></span> <span data-ttu-id="f8181-234">"HDR=Yes;" 表示第一個資料列包含資料行名稱，而非資料；"IMEX=1;" 表示驅動程式會將「混合」資料行一律讀取為文字。</span><span class="sxs-lookup"><span data-stu-id="f8181-234">"HDR=Yes;" indicates that the first row contains column names, not data, and "IMEX=1;" tells the driver to always read "intermixed" data columns as text.</span></span>  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 <span data-ttu-id="f8181-235">請注意，`Extended Properties` 所需的雙引號字元還必須以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="f8181-235">Note that the double quotation character required for the `Extended Properties` must also be enclosed in double quotation marks.</span></span>  
  
### <a name="data-shape-provider-connection-string-syntax"></a><span data-ttu-id="f8181-236">Data Shape 提供者連接字串語法</span><span class="sxs-lookup"><span data-stu-id="f8181-236">Data Shape Provider Connection String Syntax</span></span>  
 <span data-ttu-id="f8181-237">使用 Microsoft Data Shape 提供者時，使用 `Provider` 及 `Data Provider` 這兩個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f8181-237">Use both the `Provider` and the `Data Provider` keywords when using the Microsoft Data Shape provider.</span></span> <span data-ttu-id="f8181-238">下列範例使用 Shape 提供者連接至 SQL Server 的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8181-238">The following example uses the Shape provider to connect to a local instance of SQL Server.</span></span>  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a><span data-ttu-id="f8181-239">Odbc 連接字串</span><span class="sxs-lookup"><span data-stu-id="f8181-239">Odbc Connection Strings</span></span>  
 <span data-ttu-id="f8181-240"><xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> 的 <xref:System.Data.Odbc.OdbcConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="f8181-240">The <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> property of a <xref:System.Data.Odbc.OdbcConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="f8181-241">Odbc 連接字串也受到 <xref:System.Data.Odbc.OdbcConnectionStringBuilder> 的支援。</span><span class="sxs-lookup"><span data-stu-id="f8181-241">Odbc connection strings are also supported by the <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="f8181-242">下列連接字串使用 Microsoft Text Driver。</span><span class="sxs-lookup"><span data-stu-id="f8181-242">The following connection string uses the Microsoft Text Driver.</span></span>  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a><span data-ttu-id="f8181-243">使用 DataDirectory 連接至 Visual FoxPro</span><span class="sxs-lookup"><span data-stu-id="f8181-243">Using DataDirectory to Connect to Visual FoxPro</span></span>  
 <span data-ttu-id="f8181-244">下列的 <xref:System.Data.Odbc.OdbcConnection> 連接字串範例示範如何使用 `DataDirectory` 連接到 Microsoft Visual FoxPro 檔案。</span><span class="sxs-lookup"><span data-stu-id="f8181-244">The following <xref:System.Data.Odbc.OdbcConnection> connection string sample demonstrates using `DataDirectory` to connect to a Microsoft Visual FoxPro file.</span></span>  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a><span data-ttu-id="f8181-245">Oracle 連接字串</span><span class="sxs-lookup"><span data-stu-id="f8181-245">Oracle Connection Strings</span></span>  
 <span data-ttu-id="f8181-246"><xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> 的 <xref:System.Data.OracleClient.OracleConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="f8181-246">The <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> property of a <xref:System.Data.OracleClient.OracleConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="f8181-247">Oracle 連接字串也受到 <xref:System.Data.OracleClient.OracleConnectionStringBuilder> 的支援。</span><span class="sxs-lookup"><span data-stu-id="f8181-247">Oracle connection strings are also supported by the <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .</span></span>  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 <span data-ttu-id="f8181-248">如需 ODBC 連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="f8181-248">For more information on ODBC connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8181-249">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8181-249">See also</span></span>

- [<span data-ttu-id="f8181-250">連接字串</span><span class="sxs-lookup"><span data-stu-id="f8181-250">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="f8181-251">連接到資料來源</span><span class="sxs-lookup"><span data-stu-id="f8181-251">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- <span data-ttu-id="f8181-252">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="f8181-252">[ADO.NET Overview](ado-net-overview.md)</span></span>
