---
title: 連接字串語法
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 4c5ed5000f075fb637915dc40e122a9337176e36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084949"
---
# <a name="connection-string-syntax"></a><span data-ttu-id="c8b68-102">連接字串語法</span><span class="sxs-lookup"><span data-stu-id="c8b68-102">Connection String Syntax</span></span>
<span data-ttu-id="c8b68-103">每個 .NET Framework 資料提供者都擁有一個 `Connection` 物件，繼承自 <xref:System.Data.Common.DbConnection> 以及提供者特定的 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c8b68-103">Each .NET Framework data provider has a `Connection` object that inherits from <xref:System.Data.Common.DbConnection> as well as a provider-specific <xref:System.Data.Common.DbConnection.ConnectionString%2A> property.</span></span> <span data-ttu-id="c8b68-104">每個提供者的特定連接字串語法會記錄在其 `ConnectionString` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="c8b68-104">The specific connection string syntax for each provider is documented in its `ConnectionString` property.</span></span> <span data-ttu-id="c8b68-105">下表列出 .NET Framework 中包含的四個資料提供者。</span><span class="sxs-lookup"><span data-stu-id="c8b68-105">The following table lists the four data providers that are included in the .NET Framework.</span></span>  
  
|<span data-ttu-id="c8b68-106">.NET Framework Data Provider - .NET Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="c8b68-106">.NET Framework data provider</span></span>|<span data-ttu-id="c8b68-107">描述</span><span class="sxs-lookup"><span data-stu-id="c8b68-107">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|<span data-ttu-id="c8b68-108">提供 Microsoft SQL Server 的資料存取。</span><span class="sxs-lookup"><span data-stu-id="c8b68-108">Provides data access for Microsoft SQL Server.</span></span> <span data-ttu-id="c8b68-109">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8b68-109">For more information on connection string syntax, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OleDb>|<span data-ttu-id="c8b68-110">為使用 OLE DB 所公開的資料來源提供資料存取。</span><span class="sxs-lookup"><span data-stu-id="c8b68-110">Provides data access for data sources exposed using OLE DB.</span></span> <span data-ttu-id="c8b68-111">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8b68-111">For more information on connection string syntax, see <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.Odbc>|<span data-ttu-id="c8b68-112">為使用 ODBC 所公開的資料來源提供資料存取。</span><span class="sxs-lookup"><span data-stu-id="c8b68-112">Provides data access for data sources exposed using ODBC.</span></span> <span data-ttu-id="c8b68-113">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8b68-113">For more information on connection string syntax, see <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OracleClient>|<span data-ttu-id="c8b68-114">提供 Oracle 8.1.7 (含) 以後版本的資料存取。</span><span class="sxs-lookup"><span data-stu-id="c8b68-114">Provides data access for Oracle version 8.1.7 or later.</span></span> <span data-ttu-id="c8b68-115">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8b68-115">For more information on connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>|  
  
## <a name="connection-string-builders"></a><span data-ttu-id="c8b68-116">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="c8b68-116">Connection String Builders</span></span>  
 <span data-ttu-id="c8b68-117">ADO.NET 2.0 針對 .NET Framework 資料提供者導入了下列連接字串產生器 (Builder)。</span><span class="sxs-lookup"><span data-stu-id="c8b68-117">ADO.NET 2.0 introduced the following connection string builders for the .NET Framework data providers.</span></span>  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 <span data-ttu-id="c8b68-118">連接字串產生器可讓您在執行階段建構語法有效的連接字串，所以您不需要在程式碼中手動串連連接字串值。</span><span class="sxs-lookup"><span data-stu-id="c8b68-118">The connection string builders allow you to construct syntactically valid connection strings at run time, so you do not have to manually concatenate connection string values in your code.</span></span> <span data-ttu-id="c8b68-119">如需詳細資訊，請參閱[連接字串建置器](../../../../docs/framework/data/adonet/connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b68-119">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  

## <a name="windows-authentication"></a><span data-ttu-id="c8b68-120">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="c8b68-120">Windows Authentication</span></span>  
 <span data-ttu-id="c8b68-121">我們建議使用 Windows 驗證 (有時稱為*整合式安全性*) 連接到支援它的資料來源。</span><span class="sxs-lookup"><span data-stu-id="c8b68-121">We recommend using Windows Authentication (sometimes referred to as *integrated security*) to connect to data sources that support it.</span></span> <span data-ttu-id="c8b68-122">連接字串所使用的語法隨提供者而異。</span><span class="sxs-lookup"><span data-stu-id="c8b68-122">The syntax employed in the connection string varies by provider.</span></span> <span data-ttu-id="c8b68-123">下列表格說明搭配 .NET Framework 資料提供者使用的「Windows 驗證」語法。</span><span class="sxs-lookup"><span data-stu-id="c8b68-123">The following table shows the Windows Authentication syntax used with the .NET Framework data providers.</span></span>  
  
|<span data-ttu-id="c8b68-124">提供者</span><span class="sxs-lookup"><span data-stu-id="c8b68-124">Provider</span></span>|<span data-ttu-id="c8b68-125">語法</span><span class="sxs-lookup"><span data-stu-id="c8b68-125">Syntax</span></span>|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  <span data-ttu-id="c8b68-126">與 `Integrated Security=true` 提供者搭配使用時，`OleDb` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8b68-126">`Integrated Security=true` throws an exception when used with the `OleDb` provider.</span></span>  
  
## <a name="sqlclient-connection-strings"></a><span data-ttu-id="c8b68-127">SqlClient 連接字串</span><span class="sxs-lookup"><span data-stu-id="c8b68-127">SqlClient Connection Strings</span></span>  
<span data-ttu-id="c8b68-128"><xref:System.Data.SqlClient.SqlConnection> 連接字串的語法列於 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="c8b68-128">The syntax for a <xref:System.Data.SqlClient.SqlConnection> connection string is documented in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c8b68-129">您可以使用 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 屬性來取得或設定 SQL Server 資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c8b68-129">You can use the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property to get or set a connection string for a SQL Server database.</span></span> <span data-ttu-id="c8b68-130">如果您需要連接至舊版的 SQL Server，則必須使用 .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>)。</span><span class="sxs-lookup"><span data-stu-id="c8b68-130">If you need to connect to an earlier version of SQL Server, you must use the .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>).</span></span> <span data-ttu-id="c8b68-131">大多數的連接字串關鍵字也可對應至 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="c8b68-131">Most connection string keywords also map to properties in the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="c8b68-132">預設值`Persist Security Info`關鍵字是`false`。</span><span class="sxs-lookup"><span data-stu-id="c8b68-132">The default setting for the `Persist Security Info` keyword is `false`.</span></span> <span data-ttu-id="c8b68-133">如果將其設為 `true` 或 `yes`，則在開啟連接後，可透過連接獲得機密資訊，包含使用者 ID 和密碼。</span><span class="sxs-lookup"><span data-stu-id="c8b68-133">Setting it to `true` or `yes` allows security-sensitive information, including the user ID and password, to be obtained from the connection after the connection has been opened.</span></span> <span data-ttu-id="c8b68-134">保持`Persist Security Info`設定為`false`來確保受信任的來源不能存取機密的連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="c8b68-134">Keep `Persist Security Info` set to `false` to ensure that an untrusted source does not have access to sensitive connection string information.</span></span>  

### <a name="windows-authentication-with-sqlclient"></a><span data-ttu-id="c8b68-135">使用 SqlClient 的 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="c8b68-135">Windows authentication with SqlClient</span></span> 
 <span data-ttu-id="c8b68-136">每個下列形式的語法會使用 Windows 驗證連接到**AdventureWorks**本機伺服器上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c8b68-136">Each of the following forms of syntax uses Windows Authentication to connect to the **AdventureWorks** database on a local server.</span></span>  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a><span data-ttu-id="c8b68-137">SqlClient 與 SQL Server 驗證</span><span class="sxs-lookup"><span data-stu-id="c8b68-137">SQL Server authentication with SqlClient</span></span>   
 <span data-ttu-id="c8b68-138">連接至 SQL Server 時慣用「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="c8b68-138">Windows Authentication is preferred for connecting to SQL Server.</span></span> <span data-ttu-id="c8b68-139">不過，如果需要「SQL Server 驗證」，請使用下列語法來指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c8b68-139">However, if SQL Server Authentication is required, use the following syntax to specify a user name and password.</span></span> <span data-ttu-id="c8b68-140">在這個範例中使用了星號來表示有效的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c8b68-140">In this example, asterisks are used to represent a valid user name and password.</span></span>  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

<span data-ttu-id="c8b68-141">當您連接到 Azure SQL Database 或 Azure SQL 資料倉儲，並提供登入，格式`user@servername`，確定`servername`在登入的值符合提供的值`Server=`。</span><span class="sxs-lookup"><span data-stu-id="c8b68-141">When you connect to Azure SQL Database or to Azure SQL Data Warehouse and provide a login in the format `user@servername`, make sure that the `servername` value in the login matches the value provided for `Server=`.</span></span>

> [!NOTE]
>  <span data-ttu-id="c8b68-142">Windows 驗證的優先順序高於 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="c8b68-142">Windows authentication takes precedence over SQL Server logins.</span></span> <span data-ttu-id="c8b68-143">如果您同時指定 Integrated Security=true 以及使用者名稱和密碼，系統就會忽略使用者名稱和密碼，而使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-143">If you specify both Integrated Security=true as well as a user name and password, the user name and password will be ignored and Windows authentication will be used.</span></span>  

### <a name="connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="c8b68-144">連接到 SQL Server 的具名執行個體</span><span class="sxs-lookup"><span data-stu-id="c8b68-144">Connect to a named instance of SQL Server</span></span>
<span data-ttu-id="c8b68-145">若要連接到 SQL Server 的具名執行個體，使用*伺服器名稱 \ 執行個體名稱*語法。</span><span class="sxs-lookup"><span data-stu-id="c8b68-145">To connect to a named instance of SQL Server, use the *server name\instance name* syntax.</span></span>  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
<span data-ttu-id="c8b68-146">您也可以在建立連接字串時，將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> 的 `SqlConnectionStringBuilder` 屬性設定為執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="c8b68-146">You can also set the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> property of the `SqlConnectionStringBuilder` to the instance name when building a connection string.</span></span> <span data-ttu-id="c8b68-147"><xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c8b68-147">The <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object is read-only.</span></span>  
  
### <a name="type-system-version-changes"></a><span data-ttu-id="c8b68-148">型別系統版本變更</span><span class="sxs-lookup"><span data-stu-id="c8b68-148">Type System Version Changes</span></span>  
 <span data-ttu-id="c8b68-149">`Type System Version`中的關鍵字<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>指定 SQL Server 類型的用戶端表示法。</span><span class="sxs-lookup"><span data-stu-id="c8b68-149">The `Type System Version` keyword in a <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> specifies the client-side representation of SQL Server types.</span></span> <span data-ttu-id="c8b68-150">如需 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 關鍵字的詳細資訊，請參閱 `Type System Version`。</span><span class="sxs-lookup"><span data-stu-id="c8b68-150">See <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> for more information about the `Type System Version` keyword.</span></span>  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a><span data-ttu-id="c8b68-151">連接和附加至 SQL Server Express 使用者執行個體</span><span class="sxs-lookup"><span data-stu-id="c8b68-151">Connecting and Attaching to SQL Server Express User Instances</span></span>  
 <span data-ttu-id="c8b68-152">使用者執行個體是 SQL Server Express 中的功能。</span><span class="sxs-lookup"><span data-stu-id="c8b68-152">User instances are a feature in SQL Server Express.</span></span> <span data-ttu-id="c8b68-153">透過使用者執行個體，在最低權限的本機 Windows 帳戶上執行的使用者不需要系統管理員權限，即可附加及執行 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c8b68-153">They allow a user running on a least-privileged local Windows account to attach and run a SQL Server database without requiring administrative privileges.</span></span> <span data-ttu-id="c8b68-154">使用者執行個體會使用使用者的 Windows 認證執行，而不是以服務方式執行。</span><span class="sxs-lookup"><span data-stu-id="c8b68-154">A user instance executes with the user's Windows credentials, not as a service.</span></span>  
  
 <span data-ttu-id="c8b68-155">如需有關使用使用者執行個體的詳細資訊，請參閱[SQL Server Express 使用者執行個體](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b68-155">For more information on working with user instances, see [SQL Server Express User Instances](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).</span></span>  
  
## <a name="using-trustservercertificate"></a><span data-ttu-id="c8b68-156">使用 TrustServerCertificate</span><span class="sxs-lookup"><span data-stu-id="c8b68-156">Using TrustServerCertificate</span></span>  
 <span data-ttu-id="c8b68-157">`TrustServerCertificate`關鍵字是有效的在連接到 SQL Server 執行個體的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-157">The `TrustServerCertificate` keyword is valid only when connecting to a SQL Server instance with a valid certificate.</span></span> <span data-ttu-id="c8b68-158">當 `TrustServerCertificate` 設定為 `true` 時，傳輸層 (Transport Layer) 會使用 SSL 來加密通道，而略過逐一檢查憑證鏈結以驗證信任的作業。</span><span class="sxs-lookup"><span data-stu-id="c8b68-158">When `TrustServerCertificate` is set to `true`, the transport layer will use SSL to encrypt the channel and bypass walking the certificate chain to validate trust.</span></span>  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  <span data-ttu-id="c8b68-159">如果 `TrustServerCertificate` 是設定為 `true` 且加密功能已開啟，則即使 `Encrypt` 在連接字串中是設定為 `false`，仍將使用伺服器上指定的加密等級，</span><span class="sxs-lookup"><span data-stu-id="c8b68-159">If `TrustServerCertificate` is set to `true` and encryption is turned on, the encryption level specified on the server will be used even if `Encrypt` is set to `false` in the connection string.</span></span> <span data-ttu-id="c8b68-160">否則連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c8b68-160">The connection will fail otherwise.</span></span>  
  
### <a name="enabling-encryption"></a><span data-ttu-id="c8b68-161">啟用加密</span><span class="sxs-lookup"><span data-stu-id="c8b68-161">Enabling Encryption</span></span>  
 <span data-ttu-id="c8b68-162">若要啟用加密時不在伺服器上，提供憑證**強制通訊協定加密**並**信任伺服器憑證**選項必須設定 SQL Server 組態管理員 」 中。</span><span class="sxs-lookup"><span data-stu-id="c8b68-162">To enable encryption when a certificate has not been provisioned on the server, the **Force Protocol Encryption** and the **Trust Server Certificate** options must be set in SQL Server Configuration Manager.</span></span> <span data-ttu-id="c8b68-163">在此種情況下，如果伺服器上未提供任何可驗證的憑證，則加密會使用自我簽署的伺服器憑證而不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-163">In this case, encryption will use a self-signed server certificate without validation if no verifiable certificate has been provisioned on the server.</span></span>  
  
 <span data-ttu-id="c8b68-164">應用程式設定無法降低 SQL Server 中設定的安全性層級，但可以選擇性地進行加強。</span><span class="sxs-lookup"><span data-stu-id="c8b68-164">Application settings cannot reduce the level of security configured in SQL Server, but can optionally strengthen it.</span></span> <span data-ttu-id="c8b68-165">應用程式可以要求加密，藉由設定`TrustServerCertificate`並`Encrypt`關鍵字來`true`，保證加密發生於即使尚未佈建伺服器憑證和**強制通訊協定加密**尚未設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="c8b68-165">An application can request encryption by setting the `TrustServerCertificate` and `Encrypt` keywords to `true`, guaranteeing that encryption takes place even when a server certificate has not been provisioned and **Force Protocol Encryption** has not been configured for the client.</span></span> <span data-ttu-id="c8b68-166">不過，如果用戶端組態中未啟用 `TrustServerCertificate`，則仍需要提供伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-166">However, if `TrustServerCertificate` is not enabled in the client configuration, a provisioned server certificate is still required.</span></span>  
  
 <span data-ttu-id="c8b68-167">下表說明所有案例。</span><span class="sxs-lookup"><span data-stu-id="c8b68-167">The following table describes all cases.</span></span>  
  
|<span data-ttu-id="c8b68-168">強制通訊協定加密用戶端設定</span><span class="sxs-lookup"><span data-stu-id="c8b68-168">Force Protocol Encryption client setting</span></span>|<span data-ttu-id="c8b68-169">信任伺服器憑證用戶端設定</span><span class="sxs-lookup"><span data-stu-id="c8b68-169">Trust Server Certificate client setting</span></span>|<span data-ttu-id="c8b68-170">資料連接字串/屬性的加密/使用加密</span><span class="sxs-lookup"><span data-stu-id="c8b68-170">Encrypt/Use Encryption for Data connection string/attribute</span></span>|<span data-ttu-id="c8b68-171">信任伺服器憑證連接字串/屬性</span><span class="sxs-lookup"><span data-stu-id="c8b68-171">Trust Server Certificate connection string/attribute</span></span>|<span data-ttu-id="c8b68-172">結果</span><span class="sxs-lookup"><span data-stu-id="c8b68-172">Result</span></span>|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|<span data-ttu-id="c8b68-173">否</span><span class="sxs-lookup"><span data-stu-id="c8b68-173">No</span></span>|<span data-ttu-id="c8b68-174">N/A</span><span class="sxs-lookup"><span data-stu-id="c8b68-174">N/A</span></span>|<span data-ttu-id="c8b68-175">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="c8b68-175">No (default)</span></span>|<span data-ttu-id="c8b68-176">略過</span><span class="sxs-lookup"><span data-stu-id="c8b68-176">Ignored</span></span>|<span data-ttu-id="c8b68-177">未發生任何加密。</span><span class="sxs-lookup"><span data-stu-id="c8b68-177">No encryption occurs.</span></span>|  
|<span data-ttu-id="c8b68-178">否</span><span class="sxs-lookup"><span data-stu-id="c8b68-178">No</span></span>|<span data-ttu-id="c8b68-179">N/A</span><span class="sxs-lookup"><span data-stu-id="c8b68-179">N/A</span></span>|<span data-ttu-id="c8b68-180">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-180">Yes</span></span>|<span data-ttu-id="c8b68-181">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="c8b68-181">No (default)</span></span>|<span data-ttu-id="c8b68-182">加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="c8b68-182">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="c8b68-183">否</span><span class="sxs-lookup"><span data-stu-id="c8b68-183">No</span></span>|<span data-ttu-id="c8b68-184">N/A</span><span class="sxs-lookup"><span data-stu-id="c8b68-184">N/A</span></span>|<span data-ttu-id="c8b68-185">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-185">Yes</span></span>|<span data-ttu-id="c8b68-186">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-186">Yes</span></span>|<span data-ttu-id="c8b68-187">加密一定會發生，但是可能會使用自我簽署的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-187">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
|<span data-ttu-id="c8b68-188">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-188">Yes</span></span>|<span data-ttu-id="c8b68-189">否</span><span class="sxs-lookup"><span data-stu-id="c8b68-189">No</span></span>|<span data-ttu-id="c8b68-190">略過</span><span class="sxs-lookup"><span data-stu-id="c8b68-190">Ignored</span></span>|<span data-ttu-id="c8b68-191">略過</span><span class="sxs-lookup"><span data-stu-id="c8b68-191">Ignored</span></span>|<span data-ttu-id="c8b68-192">驗證的伺服器憑證; 如果，就會發生加密否則，連線嘗試會失敗。</span><span class="sxs-lookup"><span data-stu-id="c8b68-192">Encryption occurs only if there is a verifiable server certificate; otherwise, the connection attempt fails.</span></span>|  
|<span data-ttu-id="c8b68-193">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-193">Yes</span></span>|<span data-ttu-id="c8b68-194">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-194">Yes</span></span>|<span data-ttu-id="c8b68-195">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="c8b68-195">No (default)</span></span>|<span data-ttu-id="c8b68-196">略過</span><span class="sxs-lookup"><span data-stu-id="c8b68-196">Ignored</span></span>|<span data-ttu-id="c8b68-197">加密一定會發生，但是可能會使用自我簽署的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-197">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
|<span data-ttu-id="c8b68-198">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-198">Yes</span></span>|<span data-ttu-id="c8b68-199">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-199">Yes</span></span>|<span data-ttu-id="c8b68-200">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-200">Yes</span></span>|<span data-ttu-id="c8b68-201">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="c8b68-201">No (default)</span></span>|<span data-ttu-id="c8b68-202">驗證的伺服器憑證; 如果，就會發生加密否則，連線嘗試會失敗。</span><span class="sxs-lookup"><span data-stu-id="c8b68-202">Encryption occurs only if there is a verifiable server certificate; otherwise, the connection attempt fails.</span></span>|  
|<span data-ttu-id="c8b68-203">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-203">Yes</span></span>|<span data-ttu-id="c8b68-204">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-204">Yes</span></span>|<span data-ttu-id="c8b68-205">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-205">Yes</span></span>|<span data-ttu-id="c8b68-206">是</span><span class="sxs-lookup"><span data-stu-id="c8b68-206">Yes</span></span>|<span data-ttu-id="c8b68-207">加密一定會發生，但是可能會使用自我簽署的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-207">Encryption always occurs, but may use a self-signed server certificate.</span></span>|  
  
 <span data-ttu-id="c8b68-208">如需詳細資訊，請參閱 <<c0> [ 使用加密而不需驗證](/sql/relational-databases/native-client/features/using-encryption-without-validation)。</span><span class="sxs-lookup"><span data-stu-id="c8b68-208">For more information, see [Using Encryption Without Validation](/sql/relational-databases/native-client/features/using-encryption-without-validation).</span></span>
  
## <a name="oledb-connection-strings"></a><span data-ttu-id="c8b68-209">OleDb 連接字串</span><span class="sxs-lookup"><span data-stu-id="c8b68-209">OleDb Connection Strings</span></span>  
 <span data-ttu-id="c8b68-210"><xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 的 <xref:System.Data.OleDb.OleDbConnection> 屬性可讓您取得或設定 OLE DB 資料來源 (例如 Microsoft Access) 的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c8b68-210">The <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> property of a <xref:System.Data.OleDb.OleDbConnection> allows you to get or set a connection string for an OLE DB data source, such as Microsoft Access.</span></span> <span data-ttu-id="c8b68-211">您也可以使用 `OleDb` 類別 (Class)，在執行階段建立 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 連接字串。</span><span class="sxs-lookup"><span data-stu-id="c8b68-211">You can also create an `OleDb` connection string at run time by using the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> class.</span></span>  
  
### <a name="oledb-connection-string-syntax"></a><span data-ttu-id="c8b68-212">OleDb 連接字串語法</span><span class="sxs-lookup"><span data-stu-id="c8b68-212">OleDb Connection String Syntax</span></span>  
 <span data-ttu-id="c8b68-213">您必須指定 <xref:System.Data.OleDb.OleDbConnection> 連接字串的提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="c8b68-213">You must specify a provider name for an <xref:System.Data.OleDb.OleDbConnection> connection string.</span></span> <span data-ttu-id="c8b68-214">下列連接字串會使用 Jet 提供者連接至 Microsoft Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c8b68-214">The following connection string connects to a Microsoft Access database using the Jet provider.</span></span> <span data-ttu-id="c8b68-215">請注意，如果資料庫未受保護 (預設值)，則 `User ID` 及 `Password` 關鍵字是選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c8b68-215">Note that the `User ID` and `Password` keywords are optional if the database is unsecured (the default).</span></span>  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 <span data-ttu-id="c8b68-216">如果您使用使用者層級安全性保護 Jet 資料庫的安全，則必須提供工作群組資訊檔 (.mdw) 的位置。</span><span class="sxs-lookup"><span data-stu-id="c8b68-216">If the Jet database is secured using user-level security, you must provide the location of the workgroup information file (.mdw).</span></span> <span data-ttu-id="c8b68-217">工作群組資訊檔是用於驗證連接字串中提供的認證。</span><span class="sxs-lookup"><span data-stu-id="c8b68-217">The workgroup information file is used to validate the credentials presented in the connection string.</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8b68-218">可提供連接資訊**OleDbConnection**在通用資料連結 (UDL) 檔案中; 不過您應該避免這種方式。</span><span class="sxs-lookup"><span data-stu-id="c8b68-218">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="c8b68-219">UDL 檔並未加密，並且會以純文字的格式公開連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="c8b68-219">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="c8b68-220">因為對您的應用程式而言，UDL 檔是外部的檔案型資源，所以您無法使用 .NET Framework 來保護該檔案。</span><span class="sxs-lookup"><span data-stu-id="c8b68-220">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span> <span data-ttu-id="c8b68-221">不支援 UDL 檔案**SqlClient**。</span><span class="sxs-lookup"><span data-stu-id="c8b68-221">UDL files are not supported for **SqlClient**.</span></span>  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a><span data-ttu-id="c8b68-222">使用 DataDirectory 連接至 Access/Jet</span><span class="sxs-lookup"><span data-stu-id="c8b68-222">Using DataDirectory to Connect to Access/Jet</span></span>  
 <span data-ttu-id="c8b68-223">`DataDirectory` 並不是由 `SqlClient` 所獨佔，</span><span class="sxs-lookup"><span data-stu-id="c8b68-223">`DataDirectory` is not exclusive to `SqlClient`.</span></span> <span data-ttu-id="c8b68-224">也可以搭配 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> .NET data 提供者使用。</span><span class="sxs-lookup"><span data-stu-id="c8b68-224">It can also be used with the <xref:System.Data.OleDb> and <xref:System.Data.Odbc> .NET data providers.</span></span> <span data-ttu-id="c8b68-225">下列範例 <xref:System.Data.OleDb.OleDbConnection> 字串所示範的語法，是連接到位於應用程式的 app_data 資料夾中的 Northwind.mdb 所需。</span><span class="sxs-lookup"><span data-stu-id="c8b68-225">The following sample <xref:System.Data.OleDb.OleDbConnection> string demonstrates the syntax required to connect to the Northwind.mdb located in the application's app_data folder.</span></span> <span data-ttu-id="c8b68-226">系統資料庫 (System.mdw) 也是儲存於該位置。</span><span class="sxs-lookup"><span data-stu-id="c8b68-226">The system database (System.mdw) is also stored in that location.</span></span>  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8b68-227">如果 Access/Jet 資料庫未受保護，則不需要在連接字串中指定系統資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="c8b68-227">Specifying the location of the system database in the connection string is not required if the Access/Jet database is unsecured.</span></span> <span data-ttu-id="c8b68-228">安全性預設為關閉，且所有連接的使用者都是使用空白密碼的內建 Admin 使用者。</span><span class="sxs-lookup"><span data-stu-id="c8b68-228">Security is off by default, with all users connecting as the built-in Admin user with a blank password.</span></span> <span data-ttu-id="c8b68-229">即使已正確地實作使用者層級的安全性，Jet 資料庫仍很容易受到攻擊。</span><span class="sxs-lookup"><span data-stu-id="c8b68-229">Even when user-level security is correctly implemented, a Jet database remains vulnerable to attack.</span></span> <span data-ttu-id="c8b68-230">因此，不建議在 Access/Jet 資料庫中儲存機密資訊，因為其檔案架構的安全性配置原本就有弱點。</span><span class="sxs-lookup"><span data-stu-id="c8b68-230">Therefore, storing sensitive information in an Access/Jet database is not recommended because of the inherent weakness of its file-based security scheme.</span></span>  
  
### <a name="connecting-to-excel"></a><span data-ttu-id="c8b68-231">連接至 Excel</span><span class="sxs-lookup"><span data-stu-id="c8b68-231">Connecting to Excel</span></span>  
 <span data-ttu-id="c8b68-232">Microsoft Jet 提供者可用於連接至 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="c8b68-232">The Microsoft Jet provider is used to connect to an Excel workbook.</span></span> <span data-ttu-id="c8b68-233">在下列連接字串中，由 `Extended Properties` 關鍵字設定 Excel 特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="c8b68-233">In the following connection string, the `Extended Properties` keyword sets properties that are specific to Excel.</span></span> <span data-ttu-id="c8b68-234">"HDR=Yes;" 表示第一個資料列包含資料行名稱，而非資料；"IMEX=1;" 表示驅動程式會將「混合」資料行一律讀取為文字。</span><span class="sxs-lookup"><span data-stu-id="c8b68-234">"HDR=Yes;" indicates that the first row contains column names, not data, and "IMEX=1;" tells the driver to always read "intermixed" data columns as text.</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 <span data-ttu-id="c8b68-235">請注意，`Extended Properties` 所需的雙引號字元還必須以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="c8b68-235">Note that the double quotation character required for the `Extended Properties` must also be enclosed in double quotation marks.</span></span>  
  
### <a name="data-shape-provider-connection-string-syntax"></a><span data-ttu-id="c8b68-236">Data Shape 提供者連接字串語法</span><span class="sxs-lookup"><span data-stu-id="c8b68-236">Data Shape Provider Connection String Syntax</span></span>  
 <span data-ttu-id="c8b68-237">使用 Microsoft Data Shape 提供者時，使用 `Provider` 及 `Data Provider` 這兩個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c8b68-237">Use both the `Provider` and the `Data Provider` keywords when using the Microsoft Data Shape provider.</span></span> <span data-ttu-id="c8b68-238">下列範例使用 Shape 提供者連接至 SQL Server 的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="c8b68-238">The following example uses the Shape provider to connect to a local instance of SQL Server.</span></span>  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a><span data-ttu-id="c8b68-239">Odbc 連接字串</span><span class="sxs-lookup"><span data-stu-id="c8b68-239">Odbc Connection Strings</span></span>  
 <span data-ttu-id="c8b68-240"><xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> 的 <xref:System.Data.Odbc.OdbcConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c8b68-240">The <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> property of a <xref:System.Data.Odbc.OdbcConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="c8b68-241">Odbc 連接字串也受到 <xref:System.Data.Odbc.OdbcConnectionStringBuilder> 的支援。</span><span class="sxs-lookup"><span data-stu-id="c8b68-241">Odbc connection strings are also supported by the <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="c8b68-242">下列連接字串使用 Microsoft Text Driver。</span><span class="sxs-lookup"><span data-stu-id="c8b68-242">The following connection string uses the Microsoft Text Driver.</span></span>  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a><span data-ttu-id="c8b68-243">使用 DataDirectory 連接至 Visual FoxPro</span><span class="sxs-lookup"><span data-stu-id="c8b68-243">Using DataDirectory to Connect to Visual FoxPro</span></span>  
 <span data-ttu-id="c8b68-244">下列的 <xref:System.Data.Odbc.OdbcConnection> 連接字串範例示範如何使用 `DataDirectory` 連接到 Microsoft Visual FoxPro 檔案。</span><span class="sxs-lookup"><span data-stu-id="c8b68-244">The following <xref:System.Data.Odbc.OdbcConnection> connection string sample demonstrates using `DataDirectory` to connect to a Microsoft Visual FoxPro file.</span></span>  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a><span data-ttu-id="c8b68-245">Oracle 連接字串</span><span class="sxs-lookup"><span data-stu-id="c8b68-245">Oracle Connection Strings</span></span>  
 <span data-ttu-id="c8b68-246"><xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> 的 <xref:System.Data.OracleClient.OracleConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c8b68-246">The <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> property of a <xref:System.Data.OracleClient.OracleConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="c8b68-247">Oracle 連接字串也受到 <xref:System.Data.OracleClient.OracleConnectionStringBuilder> 的支援。</span><span class="sxs-lookup"><span data-stu-id="c8b68-247">Oracle connection strings are also supported by the <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .</span></span>  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 <span data-ttu-id="c8b68-248">如需 ODBC 連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8b68-248">For more information on ODBC connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b68-249">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8b68-249">See also</span></span>

- [<span data-ttu-id="c8b68-250">連接字串</span><span class="sxs-lookup"><span data-stu-id="c8b68-250">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="c8b68-251">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="c8b68-251">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="c8b68-252">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c8b68-252">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
