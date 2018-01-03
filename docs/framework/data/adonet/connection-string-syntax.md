---
title: "連接字串語法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3be73589897bf4ffeb3d80a82bf2b560e814a4a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="connection-string-syntax"></a><span data-ttu-id="6591a-102">連接字串語法</span><span class="sxs-lookup"><span data-stu-id="6591a-102">Connection String Syntax</span></span>
<span data-ttu-id="6591a-103">每個 .NET Framework 資料提供者都擁有一個 `Connection` 物件，繼承自 <xref:System.Data.Common.DbConnection> 以及提供者特定的 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6591a-103">Each .NET Framework data provider has a `Connection` object that inherits from <xref:System.Data.Common.DbConnection> as well as a provider-specific <xref:System.Data.Common.DbConnection.ConnectionString%2A> property.</span></span> <span data-ttu-id="6591a-104">每個提供者的特定連接字串語法會記錄在其 `ConnectionString` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="6591a-104">The specific connection string syntax for each provider is documented in its `ConnectionString` property.</span></span> <span data-ttu-id="6591a-105">下表列出 .NET Framework 中包含的四個資料提供者。</span><span class="sxs-lookup"><span data-stu-id="6591a-105">The following table lists the four data providers that are included in the .NET Framework.</span></span>  
  
|<span data-ttu-id="6591a-106">.NET Framework Data Provider - .NET Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="6591a-106">.NET Framework data provider</span></span>|<span data-ttu-id="6591a-107">描述</span><span class="sxs-lookup"><span data-stu-id="6591a-107">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|<span data-ttu-id="6591a-108">提供 Microsoft SQL Server 的資料存取。</span><span class="sxs-lookup"><span data-stu-id="6591a-108">Provides data access for Microsoft SQL Server.</span></span> <span data-ttu-id="6591a-109">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="6591a-109">For more information on connection string syntax, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OleDb>|<span data-ttu-id="6591a-110">為使用 OLE DB 所公開的資料來源提供資料存取。</span><span class="sxs-lookup"><span data-stu-id="6591a-110">Provides data access for data sources exposed using OLE DB.</span></span> <span data-ttu-id="6591a-111">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="6591a-111">For more information on connection string syntax, see <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.Odbc>|<span data-ttu-id="6591a-112">為使用 ODBC 所公開的資料來源提供資料存取。</span><span class="sxs-lookup"><span data-stu-id="6591a-112">Provides data access for data sources exposed using ODBC.</span></span> <span data-ttu-id="6591a-113">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="6591a-113">For more information on connection string syntax, see <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OracleClient>|<span data-ttu-id="6591a-114">提供 Oracle 8.1.7 (含) 以後版本的資料存取。</span><span class="sxs-lookup"><span data-stu-id="6591a-114">Provides data access for Oracle version 8.1.7 or later.</span></span> <span data-ttu-id="6591a-115">如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="6591a-115">For more information on connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>|  
  
## <a name="connection-string-builders"></a><span data-ttu-id="6591a-116">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="6591a-116">Connection String Builders</span></span>  
 <span data-ttu-id="6591a-117">ADO.NET 2.0 針對 .NET Framework 資料提供者導入了下列連接字串產生器 (Builder)。</span><span class="sxs-lookup"><span data-stu-id="6591a-117">ADO.NET 2.0 introduced the following connection string builders for the .NET Framework data providers.</span></span>  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 <span data-ttu-id="6591a-118">連接字串產生器可讓您在執行階段建構語法有效的連接字串，所以您不需要在程式碼中手動串連連接字串值。</span><span class="sxs-lookup"><span data-stu-id="6591a-118">The connection string builders allow you to construct syntactically valid connection strings at run time, so you do not have to manually concatenate connection string values in your code.</span></span> <span data-ttu-id="6591a-119">如需詳細資訊，請參閱[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="6591a-119">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
## <a name="windows-authentication"></a><span data-ttu-id="6591a-120">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="6591a-120">Windows Authentication</span></span>  
 <span data-ttu-id="6591a-121">我們建議使用 Windows 驗證 (有時稱為*整合式安全性*) 連接到支援的資料來源。</span><span class="sxs-lookup"><span data-stu-id="6591a-121">We recommend using Windows Authentication (sometimes referred to as *integrated security*) to connect to data sources that support it.</span></span> <span data-ttu-id="6591a-122">連接字串所使用的語法隨提供者而異。</span><span class="sxs-lookup"><span data-stu-id="6591a-122">The syntax employed in the connection string varies by provider.</span></span> <span data-ttu-id="6591a-123">下列表格說明搭配 .NET Framework 資料提供者使用的「Windows 驗證」語法。</span><span class="sxs-lookup"><span data-stu-id="6591a-123">The following table shows the Windows Authentication syntax used with the .NET Framework data providers.</span></span>  
  
|<span data-ttu-id="6591a-124">提供者</span><span class="sxs-lookup"><span data-stu-id="6591a-124">Provider</span></span>|<span data-ttu-id="6591a-125">語法</span><span class="sxs-lookup"><span data-stu-id="6591a-125">Syntax</span></span>|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  <span data-ttu-id="6591a-126">與 `Integrated Security=true` 提供者搭配使用時，`OleDb` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6591a-126">`Integrated Security=true` throws an exception when used with the `OleDb` provider.</span></span>  
  
## <a name="sqlclient-connection-strings"></a><span data-ttu-id="6591a-127">SqlClient 連接字串</span><span class="sxs-lookup"><span data-stu-id="6591a-127">SqlClient Connection Strings</span></span>  
 <span data-ttu-id="6591a-128"><xref:System.Data.SqlClient.SqlConnection> 連接字串的語法列於 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="6591a-128">The syntax for a <xref:System.Data.SqlClient.SqlConnection> connection string is documented in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6591a-129">您可以使用 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 屬性來取得或設定 SQL Server 資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="6591a-129">You can use the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property to get or set a connection string for a SQL Server database.</span></span> <span data-ttu-id="6591a-130">如果您需要連接至舊版的 SQL Server，則必須使用 .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>)。</span><span class="sxs-lookup"><span data-stu-id="6591a-130">If you need to connect to an earlier version of SQL Server, you must use the .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>).</span></span> <span data-ttu-id="6591a-131">大多數的連接字串關鍵字也可對應至 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="6591a-131">Most connection string keywords also map to properties in the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="6591a-132">每個下列形式的語法會使用 Windows 驗證來連接到**AdventureWorks**本機伺服器上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6591a-132">Each of the following forms of syntax will use Windows Authentication to connect to the **AdventureWorks** database on a local server.</span></span>  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-logins"></a><span data-ttu-id="6591a-133">SQL Server 登入</span><span class="sxs-lookup"><span data-stu-id="6591a-133">SQL Server Logins</span></span>  
 <span data-ttu-id="6591a-134">連接至 SQL Server 時慣用「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="6591a-134">Windows Authentication is preferred for connecting to SQL Server.</span></span> <span data-ttu-id="6591a-135">不過，如果需要「SQL Server 驗證」，請使用下列語法來指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6591a-135">However, if SQL Server Authentication is required, use the following syntax to specify a user name and password.</span></span> <span data-ttu-id="6591a-136">在這個範例中使用了星號來表示有效的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6591a-136">In this example, asterisks are used to represent a valid user name and password.</span></span>  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="6591a-137">預設設定`Persist Security Info`關鍵字是`false`。</span><span class="sxs-lookup"><span data-stu-id="6591a-137">The default setting for the `Persist Security Info` keyword is `false`.</span></span> <span data-ttu-id="6591a-138">如果將其設為 `true` 或 `yes`，則在開啟連接後，可透過連接獲得機密資訊，包含使用者 ID 和密碼。</span><span class="sxs-lookup"><span data-stu-id="6591a-138">Setting it to `true` or `yes` allows security-sensitive information, including the user ID and password, to be obtained from the connection after the connection has been opened.</span></span> <span data-ttu-id="6591a-139">保留`Persist Security Info`設`false`以確保不受信任的來源，並沒有存取機密的連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="6591a-139">Keep `Persist Security Info` set to `false` to ensure that an untrusted source does not have access to sensitive connection string information.</span></span>  
  
 <span data-ttu-id="6591a-140">若要連接到 SQL Server 的具名執行個體，使用*伺服器名稱 \ 執行個體名稱*語法。</span><span class="sxs-lookup"><span data-stu-id="6591a-140">To connect to a named instance of SQL Server, use the *server name\instance name* syntax.</span></span>  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
  
 <span data-ttu-id="6591a-141">您也可以在建立連接字串時，將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> 的 `SqlConnectionStringBuilder` 屬性設定為執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="6591a-141">You can also set the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> property of the `SqlConnectionStringBuilder` to the instance name when building a connection string.</span></span> <span data-ttu-id="6591a-142"><xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="6591a-142">The <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object is read-only.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6591a-143">Windows 驗證的優先順序高於 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="6591a-143">Windows authentication takes precedence over SQL Server logins.</span></span> <span data-ttu-id="6591a-144">如果您同時指定 Integrated Security=true 以及使用者名稱和密碼，系統就會忽略使用者名稱和密碼，而使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="6591a-144">If you specify both Integrated Security=true as well as a user name and password, the user name and password will be ignored and Windows authentication will be used.</span></span>  
  
### <a name="type-system-version-changes"></a><span data-ttu-id="6591a-145">型別系統版本變更</span><span class="sxs-lookup"><span data-stu-id="6591a-145">Type System Version Changes</span></span>  
 <span data-ttu-id="6591a-146">`Type System Version` 中的 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 關鍵字指定 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 型別的用戶端表示。</span><span class="sxs-lookup"><span data-stu-id="6591a-146">The `Type System Version` keyword in a <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> specifies the client-side representation of [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="6591a-147">如需 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 關鍵字的詳細資訊，請參閱 `Type System Version`。</span><span class="sxs-lookup"><span data-stu-id="6591a-147">See <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> for more information about the `Type System Version` keyword.</span></span>  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a><span data-ttu-id="6591a-148">連接和附加至 SQL Server Express 使用者執行個體</span><span class="sxs-lookup"><span data-stu-id="6591a-148">Connecting and Attaching to SQL Server Express User Instances</span></span>  
 <span data-ttu-id="6591a-149">使用者執行個體是 SQL Server Express 中的功能。</span><span class="sxs-lookup"><span data-stu-id="6591a-149">User instances are a feature in SQL Server Express.</span></span> <span data-ttu-id="6591a-150">透過使用者執行個體，在最低權限的本機 Windows 帳戶上執行的使用者不需要系統管理員權限，即可附加及執行 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6591a-150">They allow a user running on a least-privileged local Windows account to attach and run a SQL Server database without requiring administrative privileges.</span></span> <span data-ttu-id="6591a-151">使用者執行個體會使用使用者的 Windows 認證執行，而不是以服務方式執行。</span><span class="sxs-lookup"><span data-stu-id="6591a-151">A user instance executes with the user's Windows credentials, not as a service.</span></span>  
  
 <span data-ttu-id="6591a-152">如需使用使用者執行個體的詳細資訊，請參閱[SQL Server Express 使用者執行個體](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="6591a-152">For more information on working with user instances, see [SQL Server Express User Instances](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).</span></span>  
  
## <a name="using-trustservercertificate"></a><span data-ttu-id="6591a-153">使用 TrustServerCertificate</span><span class="sxs-lookup"><span data-stu-id="6591a-153">Using TrustServerCertificate</span></span>  
 <span data-ttu-id="6591a-154">`TrustServerCertificate` 關鍵字僅在使用有效憑證連接到 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 執行個體時才為有效。</span><span class="sxs-lookup"><span data-stu-id="6591a-154">The `TrustServerCertificate` keyword is valid only when connecting to a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance with a valid certificate.</span></span> <span data-ttu-id="6591a-155">當 `TrustServerCertificate` 設定為 `true` 時，傳輸層 (Transport Layer) 會使用 SSL 來加密通道，而略過逐一檢查憑證鏈結以驗證信任的作業。</span><span class="sxs-lookup"><span data-stu-id="6591a-155">When `TrustServerCertificate` is set to `true`, the transport layer will use SSL to encrypt the channel and bypass walking the certificate chain to validate trust.</span></span>  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  <span data-ttu-id="6591a-156">如果 `TrustServerCertificate` 是設定為 `true` 且加密功能已開啟，則即使 `Encrypt` 在連接字串中是設定為 `false`，仍將使用伺服器上指定的加密等級，</span><span class="sxs-lookup"><span data-stu-id="6591a-156">If `TrustServerCertificate` is set to `true` and encryption is turned on, the encryption level specified on the server will be used even if `Encrypt` is set to `false` in the connection string.</span></span> <span data-ttu-id="6591a-157">否則連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="6591a-157">The connection will fail otherwise.</span></span>  
  
### <a name="enabling-encryption"></a><span data-ttu-id="6591a-158">啟用加密</span><span class="sxs-lookup"><span data-stu-id="6591a-158">Enabling Encryption</span></span>  
 <span data-ttu-id="6591a-159">若要啟用加密不在伺服器上，提供憑證時**強制通訊協定加密**和**信任伺服器憑證**選項必須設定 SQL Server 組態管理員 」 中。</span><span class="sxs-lookup"><span data-stu-id="6591a-159">To enable encryption when a certificate has not been provisioned on the server, the **Force Protocol Encryption** and the **Trust Server Certificate** options must be set in SQL Server Configuration Manager.</span></span> <span data-ttu-id="6591a-160">在此種情況下，如果伺服器上未提供任何可驗證的憑證，則加密會使用自我簽署的伺服器憑證而不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="6591a-160">In this case, encryption will use a self-signed server certificate without validation if no verifiable certificate has been provisioned on the server.</span></span>  
  
 <span data-ttu-id="6591a-161">應用程式設定無法降低 SQL Server 中設定的安全性層級，但可以選擇性地進行加強。</span><span class="sxs-lookup"><span data-stu-id="6591a-161">Application settings cannot reduce the level of security configured in SQL Server, but can optionally strengthen it.</span></span> <span data-ttu-id="6591a-162">應用程式可以藉由設定要求加密`TrustServerCertificate`和`Encrypt`關鍵字`true`，保證，仍會進行加密即使尚未佈建伺服器憑證和**強制通訊協定加密**尚未設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="6591a-162">An application can request encryption by setting the `TrustServerCertificate` and `Encrypt` keywords to `true`, guaranteeing that encryption takes place even when a server certificate has not been provisioned and **Force Protocol Encryption** has not been configured for the client.</span></span> <span data-ttu-id="6591a-163">不過，如果用戶端組態中未啟用 `TrustServerCertificate`，則仍需要提供伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="6591a-163">However, if `TrustServerCertificate` is not enabled in the client configuration, a provisioned server certificate is still required.</span></span>  
  
 <span data-ttu-id="6591a-164">下表說明所有案例。</span><span class="sxs-lookup"><span data-stu-id="6591a-164">The following table describes all cases.</span></span>  
  
|<span data-ttu-id="6591a-165">強制通訊協定加密用戶端設定</span><span class="sxs-lookup"><span data-stu-id="6591a-165">Force Protocol Encryption client setting</span></span>|<span data-ttu-id="6591a-166">信任伺服器憑證用戶端設定</span><span class="sxs-lookup"><span data-stu-id="6591a-166">Trust Server Certificate client setting</span></span>|<span data-ttu-id="6591a-167">資料連接字串/屬性的加密/使用加密</span><span class="sxs-lookup"><span data-stu-id="6591a-167">Encrypt/Use Encryption for Data connection string/attribute</span></span>|<span data-ttu-id="6591a-168">信任伺服器憑證連接字串/屬性</span><span class="sxs-lookup"><span data-stu-id="6591a-168">Trust Server Certificate connection string/attribute</span></span>|<span data-ttu-id="6591a-169">結果</span><span class="sxs-lookup"><span data-stu-id="6591a-169">Result</span></span>|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|<span data-ttu-id="6591a-170">否</span><span class="sxs-lookup"><span data-stu-id="6591a-170">No</span></span>|<span data-ttu-id="6591a-171">N/A</span><span class="sxs-lookup"><span data-stu-id="6591a-171">N/A</span></span>|<span data-ttu-id="6591a-172">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="6591a-172">No (default)</span></span>|<span data-ttu-id="6591a-173">略過</span><span class="sxs-lookup"><span data-stu-id="6591a-173">Ignored</span></span>|<span data-ttu-id="6591a-174">未發生任何加密。</span><span class="sxs-lookup"><span data-stu-id="6591a-174">No encryption occurs.</span></span>|  
|<span data-ttu-id="6591a-175">否</span><span class="sxs-lookup"><span data-stu-id="6591a-175">No</span></span>|<span data-ttu-id="6591a-176">N/A</span><span class="sxs-lookup"><span data-stu-id="6591a-176">N/A</span></span>|<span data-ttu-id="6591a-177">是</span><span class="sxs-lookup"><span data-stu-id="6591a-177">Yes</span></span>|<span data-ttu-id="6591a-178">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="6591a-178">No (default)</span></span>|<span data-ttu-id="6591a-179">加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6591a-179">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="6591a-180">否</span><span class="sxs-lookup"><span data-stu-id="6591a-180">No</span></span>|<span data-ttu-id="6591a-181">N/A</span><span class="sxs-lookup"><span data-stu-id="6591a-181">N/A</span></span>|<span data-ttu-id="6591a-182">是</span><span class="sxs-lookup"><span data-stu-id="6591a-182">Yes</span></span>|<span data-ttu-id="6591a-183">是</span><span class="sxs-lookup"><span data-stu-id="6591a-183">Yes</span></span>|<span data-ttu-id="6591a-184">加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6591a-184">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="6591a-185">是</span><span class="sxs-lookup"><span data-stu-id="6591a-185">Yes</span></span>|<span data-ttu-id="6591a-186">否</span><span class="sxs-lookup"><span data-stu-id="6591a-186">No</span></span>|<span data-ttu-id="6591a-187">略過</span><span class="sxs-lookup"><span data-stu-id="6591a-187">Ignored</span></span>|<span data-ttu-id="6591a-188">略過</span><span class="sxs-lookup"><span data-stu-id="6591a-188">Ignored</span></span>|<span data-ttu-id="6591a-189">加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6591a-189">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="6591a-190">是</span><span class="sxs-lookup"><span data-stu-id="6591a-190">Yes</span></span>|<span data-ttu-id="6591a-191">是</span><span class="sxs-lookup"><span data-stu-id="6591a-191">Yes</span></span>|<span data-ttu-id="6591a-192">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="6591a-192">No (default)</span></span>|<span data-ttu-id="6591a-193">略過</span><span class="sxs-lookup"><span data-stu-id="6591a-193">Ignored</span></span>|<span data-ttu-id="6591a-194">加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6591a-194">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="6591a-195">是</span><span class="sxs-lookup"><span data-stu-id="6591a-195">Yes</span></span>|<span data-ttu-id="6591a-196">是</span><span class="sxs-lookup"><span data-stu-id="6591a-196">Yes</span></span>|<span data-ttu-id="6591a-197">是</span><span class="sxs-lookup"><span data-stu-id="6591a-197">Yes</span></span>|<span data-ttu-id="6591a-198">否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="6591a-198">No (default)</span></span>|<span data-ttu-id="6591a-199">加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6591a-199">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="6591a-200">是</span><span class="sxs-lookup"><span data-stu-id="6591a-200">Yes</span></span>|<span data-ttu-id="6591a-201">是</span><span class="sxs-lookup"><span data-stu-id="6591a-201">Yes</span></span>|<span data-ttu-id="6591a-202">是</span><span class="sxs-lookup"><span data-stu-id="6591a-202">Yes</span></span>|<span data-ttu-id="6591a-203">是</span><span class="sxs-lookup"><span data-stu-id="6591a-203">Yes</span></span>|<span data-ttu-id="6591a-204">加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6591a-204">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
  
 <span data-ttu-id="6591a-205">如需詳細資訊，請參閱[使用加密而不需驗證](http://go.microsoft.com/fwlink/?LinkId=120500)SQL Server 線上叢書 》 中。</span><span class="sxs-lookup"><span data-stu-id="6591a-205">For more information, see [Using Encryption Without Validation](http://go.microsoft.com/fwlink/?LinkId=120500) in SQL Server Books Online.</span></span>  
  
## <a name="oledb-connection-strings"></a><span data-ttu-id="6591a-206">OleDb 連接字串</span><span class="sxs-lookup"><span data-stu-id="6591a-206">OleDb Connection Strings</span></span>  
 <span data-ttu-id="6591a-207"><xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 的 <xref:System.Data.OleDb.OleDbConnection> 屬性可讓您取得或設定 OLE DB 資料來源 (例如 Microsoft Access) 的連接字串。</span><span class="sxs-lookup"><span data-stu-id="6591a-207">The <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> property of a <xref:System.Data.OleDb.OleDbConnection> allows you to get or set a connection string for an OLE DB data source, such as Microsoft Access.</span></span> <span data-ttu-id="6591a-208">您也可以使用 `OleDb` 類別 (Class)，在執行階段建立 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 連接字串。</span><span class="sxs-lookup"><span data-stu-id="6591a-208">You can also create an `OleDb` connection string at run time by using the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> class.</span></span>  
  
### <a name="oledb-connection-string-syntax"></a><span data-ttu-id="6591a-209">OleDb 連接字串語法</span><span class="sxs-lookup"><span data-stu-id="6591a-209">OleDb Connection String Syntax</span></span>  
 <span data-ttu-id="6591a-210">您必須指定 <xref:System.Data.OleDb.OleDbConnection> 連接字串的提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="6591a-210">You must specify a provider name for an <xref:System.Data.OleDb.OleDbConnection> connection string.</span></span> <span data-ttu-id="6591a-211">下列連接字串會使用 Jet 提供者連接至 Microsoft Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6591a-211">The following connection string connects to a Microsoft Access database using the Jet provider.</span></span> <span data-ttu-id="6591a-212">請注意，如果資料庫未受保護 (預設值)，則 `UserID` 及 `Password` 關鍵字是選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="6591a-212">Note that the `UserID` and `Password` keywords are optional if the database is unsecured (the default).</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 <span data-ttu-id="6591a-213">如果您使用使用者層級安全性保護 Jet 資料庫的安全，則必須提供工作群組資訊檔 (.mdw) 的位置。</span><span class="sxs-lookup"><span data-stu-id="6591a-213">If the Jet database is secured using user-level security, you must provide the location of the workgroup information file (.mdw).</span></span> <span data-ttu-id="6591a-214">工作群組資訊檔是用於驗證連接字串中提供的認證。</span><span class="sxs-lookup"><span data-stu-id="6591a-214">The workgroup information file is used to validate the credentials presented in the connection string.</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="6591a-215">可提供連接資訊**OleDbConnection**在通用資料連結 (UDL) 檔案中; 但是您應該避免這樣。</span><span class="sxs-lookup"><span data-stu-id="6591a-215">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="6591a-216">UDL 檔並未加密，並且會以純文字的格式公開連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="6591a-216">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="6591a-217">因為對您的應用程式而言，UDL 檔是外部的檔案型資源，所以您無法使用 .NET Framework 來保護該檔案。</span><span class="sxs-lookup"><span data-stu-id="6591a-217">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span> <span data-ttu-id="6591a-218">不支援 UDL 檔案**SqlClient**。</span><span class="sxs-lookup"><span data-stu-id="6591a-218">UDL files are not supported for **SqlClient**.</span></span>  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a><span data-ttu-id="6591a-219">使用 DataDirectory 連接至 Access/Jet</span><span class="sxs-lookup"><span data-stu-id="6591a-219">Using DataDirectory to Connect to Access/Jet</span></span>  
 <span data-ttu-id="6591a-220">`DataDirectory` 並不是由 `SqlClient` 所獨佔，</span><span class="sxs-lookup"><span data-stu-id="6591a-220">`DataDirectory` is not exclusive to `SqlClient`.</span></span> <span data-ttu-id="6591a-221">也可以搭配 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> .NET data 提供者使用。</span><span class="sxs-lookup"><span data-stu-id="6591a-221">It can also be used with the <xref:System.Data.OleDb> and <xref:System.Data.Odbc> .NET data providers.</span></span> <span data-ttu-id="6591a-222">下列範例 <xref:System.Data.OleDb.OleDbConnection> 字串所示範的語法，是連接到位於應用程式的 app_data 資料夾中的 Northwind.mdb 所需。</span><span class="sxs-lookup"><span data-stu-id="6591a-222">The following sample <xref:System.Data.OleDb.OleDbConnection> string demonstrates the syntax required to connect to the Northwind.mdb located in the application's app_data folder.</span></span> <span data-ttu-id="6591a-223">系統資料庫 (System.mdw) 也是儲存於該位置。</span><span class="sxs-lookup"><span data-stu-id="6591a-223">The system database (System.mdw) is also stored in that location.</span></span>  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="6591a-224">如果 Access/Jet 資料庫未受保護，則不需要在連接字串中指定系統資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="6591a-224">Specifying the location of the system database in the connection string is not required if the Access/Jet database is unsecured.</span></span> <span data-ttu-id="6591a-225">安全性預設為關閉，且所有連接的使用者都是使用空白密碼的內建 Admin 使用者。</span><span class="sxs-lookup"><span data-stu-id="6591a-225">Security is off by default, with all users connecting as the built-in Admin user with a blank password.</span></span> <span data-ttu-id="6591a-226">即使已正確地實作使用者層級的安全性，Jet 資料庫仍很容易受到攻擊。</span><span class="sxs-lookup"><span data-stu-id="6591a-226">Even when user-level security is correctly implemented, a Jet database remains vulnerable to attack.</span></span> <span data-ttu-id="6591a-227">因此，不建議在 Access/Jet 資料庫中儲存機密資訊，因為其檔案架構的安全性配置原本就有弱點。</span><span class="sxs-lookup"><span data-stu-id="6591a-227">Therefore, storing sensitive information in an Access/Jet database is not recommended because of the inherent weakness of its file-based security scheme.</span></span>  
  
### <a name="connecting-to-excel"></a><span data-ttu-id="6591a-228">連接至 Excel</span><span class="sxs-lookup"><span data-stu-id="6591a-228">Connecting to Excel</span></span>  
 <span data-ttu-id="6591a-229">Microsoft Jet 提供者可用於連接至 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="6591a-229">The Microsoft Jet provider is used to connect to an Excel workbook.</span></span> <span data-ttu-id="6591a-230">在下列連接字串中，由 `Extended Properties` 關鍵字設定 Excel 特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="6591a-230">In the following connection string, the `Extended Properties` keyword sets properties that are specific to Excel.</span></span> <span data-ttu-id="6591a-231">"HDR=Yes;" 表示第一個資料列包含資料行名稱，而非資料；"IMEX=1;" 表示驅動程式會將「混合」資料行一律讀取為文字。</span><span class="sxs-lookup"><span data-stu-id="6591a-231">"HDR=Yes;" indicates that the first row contains column names, not data, and "IMEX=1;" tells the driver to always read "intermixed" data columns as text.</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 <span data-ttu-id="6591a-232">請注意，`Extended Properties` 所需的雙引號字元還必須以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="6591a-232">Note that the double quotation character required for the `Extended Properties` must also be enclosed in double quotation marks.</span></span>  
  
### <a name="data-shape-provider-connection-string-syntax"></a><span data-ttu-id="6591a-233">Data Shape 提供者連接字串語法</span><span class="sxs-lookup"><span data-stu-id="6591a-233">Data Shape Provider Connection String Syntax</span></span>  
 <span data-ttu-id="6591a-234">使用 Microsoft Data Shape 提供者時，使用 `Provider` 及 `Data Provider` 這兩個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6591a-234">Use both the `Provider` and the `Data Provider` keywords when using the Microsoft Data Shape provider.</span></span> <span data-ttu-id="6591a-235">下列範例使用 Shape 提供者連接至 SQL Server 的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="6591a-235">The following example uses the Shape provider to connect to a local instance of SQL Server.</span></span>  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a><span data-ttu-id="6591a-236">Odbc 連接字串</span><span class="sxs-lookup"><span data-stu-id="6591a-236">Odbc Connection Strings</span></span>  
 <span data-ttu-id="6591a-237"><xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> 的 <xref:System.Data.Odbc.OdbcConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="6591a-237">The <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> property of a <xref:System.Data.Odbc.OdbcConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="6591a-238">Odbc 連接字串也受到 <xref:System.Data.Odbc.OdbcConnectionStringBuilder> 的支援。</span><span class="sxs-lookup"><span data-stu-id="6591a-238">Odbc connection strings are also supported by the <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="6591a-239">下列連接字串使用 Microsoft Text Driver。</span><span class="sxs-lookup"><span data-stu-id="6591a-239">The following connection string uses the Microsoft Text Driver.</span></span>  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a><span data-ttu-id="6591a-240">使用 DataDirectory 連接至 Visual FoxPro</span><span class="sxs-lookup"><span data-stu-id="6591a-240">Using DataDirectory to Connect to Visual FoxPro</span></span>  
 <span data-ttu-id="6591a-241">下列的 <xref:System.Data.Odbc.OdbcConnection> 連接字串範例示範如何使用 `DataDirectory` 連接到 Microsoft Visual FoxPro 檔案。</span><span class="sxs-lookup"><span data-stu-id="6591a-241">The following <xref:System.Data.Odbc.OdbcConnection> connection string sample demonstrates using `DataDirectory` to connect to a Microsoft Visual FoxPro file.</span></span>  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a><span data-ttu-id="6591a-242">Oracle 連接字串</span><span class="sxs-lookup"><span data-stu-id="6591a-242">Oracle Connection Strings</span></span>  
 <span data-ttu-id="6591a-243"><xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> 的 <xref:System.Data.OracleClient.OracleConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="6591a-243">The <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> property of a <xref:System.Data.OracleClient.OracleConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="6591a-244">Oracle 連接字串也受到 <xref:System.Data.OracleClient.OracleConnectionStringBuilder> 的支援。</span><span class="sxs-lookup"><span data-stu-id="6591a-244">Oracle connection strings are also supported by the <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .</span></span>  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 <span data-ttu-id="6591a-245">如需 ODBC 連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="6591a-245">For more information on ODBC connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6591a-246">請參閱</span><span class="sxs-lookup"><span data-stu-id="6591a-246">See Also</span></span>  
 [<span data-ttu-id="6591a-247">連接字串</span><span class="sxs-lookup"><span data-stu-id="6591a-247">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="6591a-248">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="6591a-248">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="6591a-249">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6591a-249">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
