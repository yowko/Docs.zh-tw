---
title: 連接字串語法
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 4ec2b8a0a478f59ca66f8699e7846004a3a409cf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583604"
---
# <a name="connection-string-syntax"></a>連接字串語法
每個 .NET Framework 資料提供者都擁有一個 `Connection` 物件，繼承自 <xref:System.Data.Common.DbConnection> 以及提供者特定的 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性。 每個提供者的特定連接字串語法會記錄在其 `ConnectionString` 屬性中。 下表列出 .NET Framework 中包含的四個資料提供者。  
  
|.NET Framework Data Provider - .NET Framework 資料提供者|描述|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|提供 Microsoft SQL Server 的資料存取。 如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。|  
|<xref:System.Data.OleDb>|為使用 OLE DB 所公開的資料來源提供資料存取。 如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>。|  
|<xref:System.Data.Odbc>|為使用 ODBC 所公開的資料來源提供資料存取。 如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>。|  
|<xref:System.Data.OracleClient>|提供 Oracle 8.1.7 (含) 以後版本的資料存取。 如需連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。|  
  
## <a name="connection-string-builders"></a>連接字串產生器  
 ADO.NET 2.0 針對 .NET Framework 資料提供者導入了下列連接字串產生器 (Builder)。  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 連接字串產生器可讓您在執行階段建構語法有效的連接字串，所以您不需要在程式碼中手動串連連接字串值。 如需詳細資訊，請參閱[連接字串建置器](../../../../docs/framework/data/adonet/connection-string-builders.md)。  

## <a name="windows-authentication"></a>Windows 驗證  
 我們建議使用 Windows 驗證 (有時稱為*整合式安全性*) 連接到支援它的資料來源。 連接字串所使用的語法隨提供者而異。 下列表格說明搭配 .NET Framework 資料提供者使用的「Windows 驗證」語法。  
  
|提供者|語法|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  與 `Integrated Security=true` 提供者搭配使用時，`OleDb` 會擲回例外狀況。  
  
## <a name="sqlclient-connection-strings"></a>SqlClient 連接字串  
<xref:System.Data.SqlClient.SqlConnection> 連接字串的語法列於 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 屬性中。 您可以使用 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 屬性來取得或設定 SQL Server 資料庫的連接字串。 如果您需要連接至舊版的 SQL Server，則必須使用 .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>)。 大多數的連接字串關鍵字也可對應至 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 中的屬性。  

> [!IMPORTANT]
>  預設值`Persist Security Info`關鍵字是`false`。 如果將其設為 `true` 或 `yes`，則在開啟連接後，可透過連接獲得機密資訊，包含使用者 ID 和密碼。 保持`Persist Security Info`設定為`false`來確保受信任的來源不能存取機密的連接字串資訊。  

### <a name="windows-authentication-with-sqlclient"></a>使用 SqlClient 的 Windows 驗證 
 每個下列形式的語法會使用 Windows 驗證連接到**AdventureWorks**本機伺服器上的資料庫。  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>SqlClient 與 SQL Server 驗證   
 連接至 SQL Server 時慣用「Windows 驗證」。 不過，如果需要「SQL Server 驗證」，請使用下列語法來指定使用者名稱和密碼。 在這個範例中使用了星號來表示有效的使用者名稱和密碼。  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

當您連接到 Azure SQL Database 或 Azure SQL 資料倉儲，並提供登入，格式`user@servername`，確定`servername`在登入的值符合提供的值`Server=`。

> [!NOTE]
>  Windows 驗證的優先順序高於 SQL Server 登入。 如果您同時指定 Integrated Security=true 以及使用者名稱和密碼，系統就會忽略使用者名稱和密碼，而使用 Windows 驗證。  

### <a name="connect-to-a-named-instance-of-sql-server"></a>連接到 SQL Server 的具名執行個體
若要連接到 SQL Server 的具名執行個體，使用*伺服器名稱 \ 執行個體名稱*語法。  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
您也可以在建立連接字串時，將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> 的 `SqlConnectionStringBuilder` 屬性設定為執行個體名稱。 <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性是唯讀的。  
  
### <a name="type-system-version-changes"></a>型別系統版本變更  
 `Type System Version`中的關鍵字<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>指定 SQL Server 類型的用戶端表示法。 如需 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 關鍵字的詳細資訊，請參閱 `Type System Version`。  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>連接和附加至 SQL Server Express 使用者執行個體  
 使用者執行個體是 SQL Server Express 中的功能。 透過使用者執行個體，在最低權限的本機 Windows 帳戶上執行的使用者不需要系統管理員權限，即可附加及執行 SQL Server 資料庫。 使用者執行個體會使用使用者的 Windows 認證執行，而不是以服務方式執行。  
  
 如需有關使用使用者執行個體的詳細資訊，請參閱[SQL Server Express 使用者執行個體](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)。  
  
## <a name="using-trustservercertificate"></a>使用 TrustServerCertificate  
 `TrustServerCertificate`關鍵字是有效的在連接到 SQL Server 執行個體的有效憑證。 當 `TrustServerCertificate` 設定為 `true` 時，傳輸層 (Transport Layer) 會使用 SSL 來加密通道，而略過逐一檢查憑證鏈結以驗證信任的作業。  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  如果 `TrustServerCertificate` 是設定為 `true` 且加密功能已開啟，則即使 `Encrypt` 在連接字串中是設定為 `false`，仍將使用伺服器上指定的加密等級， 否則連接將會失敗。  
  
### <a name="enabling-encryption"></a>啟用加密  
 若要啟用加密時不在伺服器上，提供憑證**強制通訊協定加密**並**信任伺服器憑證**選項必須設定 SQL Server 組態管理員 」 中。 在此種情況下，如果伺服器上未提供任何可驗證的憑證，則加密會使用自我簽署的伺服器憑證而不進行驗證。  
  
 應用程式設定無法降低 SQL Server 中設定的安全性層級，但可以選擇性地進行加強。 應用程式可以要求加密，藉由設定`TrustServerCertificate`並`Encrypt`關鍵字來`true`，保證加密發生於即使尚未佈建伺服器憑證和**強制通訊協定加密**尚未設定用戶端。 不過，如果用戶端組態中未啟用 `TrustServerCertificate`，則仍需要提供伺服器憑證。  
  
 下表說明所有案例。  
  
|強制通訊協定加密用戶端設定|信任伺服器憑證用戶端設定|資料連接字串/屬性的加密/使用加密|信任伺服器憑證連接字串/屬性|結果|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|否|N/A|否 (預設值)|略過|未發生任何加密。|  
|否|N/A|是|否 (預設值)|加密只有在有可驗證的伺服器憑證時才會發生，否則連接嘗試就會失敗。|  
|否|N/A|是|是|加密一定會發生，但是可能會使用自我簽署的伺服器憑證。|  
|是|否|略過|略過|驗證的伺服器憑證; 如果，就會發生加密否則，連線嘗試會失敗。|  
|是|是|否 (預設值)|略過|加密一定會發生，但是可能會使用自我簽署的伺服器憑證。|  
|是|是|是|否 (預設值)|驗證的伺服器憑證; 如果，就會發生加密否則，連線嘗試會失敗。|  
|是|是|是|是|加密一定會發生，但是可能會使用自我簽署的伺服器憑證。|  
  
 如需詳細資訊，請參閱 <<c0> [ 使用加密而不需驗證](/sql/relational-databases/native-client/features/using-encryption-without-validation)。
  
## <a name="oledb-connection-strings"></a>OleDb 連接字串  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 的 <xref:System.Data.OleDb.OleDbConnection> 屬性可讓您取得或設定 OLE DB 資料來源 (例如 Microsoft Access) 的連接字串。 您也可以使用 `OleDb` 類別 (Class)，在執行階段建立 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 連接字串。  
  
### <a name="oledb-connection-string-syntax"></a>OleDb 連接字串語法  
 您必須指定 <xref:System.Data.OleDb.OleDbConnection> 連接字串的提供者名稱。 下列連接字串會使用 Jet 提供者連接至 Microsoft Access 資料庫。 請注意，如果資料庫未受保護 (預設值)，則 `User ID` 及 `Password` 關鍵字是選擇性項目。  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 如果您使用使用者層級安全性保護 Jet 資料庫的安全，則必須提供工作群組資訊檔 (.mdw) 的位置。 工作群組資訊檔是用於驗證連接字串中提供的認證。  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  可提供連接資訊**OleDbConnection**在通用資料連結 (UDL) 檔案中; 不過您應該避免這種方式。 UDL 檔並未加密，並且會以純文字的格式公開連接字串資訊。 因為對您的應用程式而言，UDL 檔是外部的檔案型資源，所以您無法使用 .NET Framework 來保護該檔案。 不支援 UDL 檔案**SqlClient**。  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>使用 DataDirectory 連接至 Access/Jet  
 `DataDirectory` 並不是由 `SqlClient` 所獨佔， 也可以搭配 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> .NET data 提供者使用。 下列範例 <xref:System.Data.OleDb.OleDbConnection> 字串所示範的語法，是連接到位於應用程式的 app_data 資料夾中的 Northwind.mdb 所需。 系統資料庫 (System.mdw) 也是儲存於該位置。  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  如果 Access/Jet 資料庫未受保護，則不需要在連接字串中指定系統資料庫的位置。 安全性預設為關閉，且所有連接的使用者都是使用空白密碼的內建 Admin 使用者。 即使已正確地實作使用者層級的安全性，Jet 資料庫仍很容易受到攻擊。 因此，不建議在 Access/Jet 資料庫中儲存機密資訊，因為其檔案架構的安全性配置原本就有弱點。  
  
### <a name="connecting-to-excel"></a>連接至 Excel  
 Microsoft Jet 提供者可用於連接至 Excel 活頁簿。 在下列連接字串中，由 `Extended Properties` 關鍵字設定 Excel 特定的屬性。 "HDR=Yes;" 表示第一個資料列包含資料行名稱，而非資料；"IMEX=1;" 表示驅動程式會將「混合」資料行一律讀取為文字。  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 請注意，`Extended Properties` 所需的雙引號字元還必須以雙引號括住。  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Data Shape 提供者連接字串語法  
 使用 Microsoft Data Shape 提供者時，使用 `Provider` 及 `Data Provider` 這兩個關鍵字。 下列範例使用 Shape 提供者連接至 SQL Server 的本機執行個體。  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Odbc 連接字串  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> 的 <xref:System.Data.Odbc.OdbcConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。 Odbc 連接字串也受到 <xref:System.Data.Odbc.OdbcConnectionStringBuilder> 的支援。  
  
 下列連接字串使用 Microsoft Text Driver。  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>使用 DataDirectory 連接至 Visual FoxPro  
 下列的 <xref:System.Data.Odbc.OdbcConnection> 連接字串範例示範如何使用 `DataDirectory` 連接到 Microsoft Visual FoxPro 檔案。  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle 連接字串  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> 的 <xref:System.Data.OracleClient.OracleConnection> 屬性可讓您取得或設定 OLE DB 資料來源的連接字串。 Oracle 連接字串也受到 <xref:System.Data.OracleClient.OracleConnectionStringBuilder> 的支援。  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 如需 ODBC 連接字串語法的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。  
  
## <a name="see-also"></a>另請參閱

- [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)
- [連接至資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
