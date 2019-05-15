---
title: .NET Framework 資料提供者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: 9fead8a5d54fba7232831bba349f27b7eed4657b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583794"
---
# <a name="net-framework-data-providers"></a>.NET Framework 資料提供者
.NET Framework 資料提供者用於連接到資料庫、 執行命令和擷取結果。 這些結果會直接處理、放入 <xref:System.Data.DataSet> 中以便視需要而公開給使用者、與多個來源的資料結合，或在各層之間進行遠端控制。 .NET framework 資料提供者是輕量級、 建立最小層之間的資料來源和程式碼，以提升效能而不犧牲功能。  
  
 下表列出包含在.NET Framework 資料提供者。  
  
|.NET Framework Data Provider - .NET Framework 資料提供者|描述|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET Framework Data Provider for SQL Server|提供 Microsoft SQL Server 的資料存取。 使用 <xref:System.Data.SqlClient> 命名空間。|  
|.NET Framework Data Provider for OLE DB|使用 OLE DB 公開的資料來源。 使用 <xref:System.Data.OleDb> 命名空間。|  
|.NET Framework Data Provider for ODBC|使用 ODBC 公開的資料來源。 使用 <xref:System.Data.Odbc> 命名空間。|  
|.NET Framework Data Provider for Oracle|針對 Oracle 資料來源。 .NET Framework Data Provider for Oracle 支援 Oracle 用戶端軟體 8.1.7 和更新版本，並使用<xref:System.Data.OracleClient>命名空間。|  
|EntityClient 提供者|為實體資料模型 (EDM) 應用程式提供資料存取。 使用 <xref:System.Data.EntityClient> 命名空間。|  
|.NET framework Data Provider for SQL Server Compact 4.0。|提供的 Microsoft SQL Server Compact 4.0 資料存取。 使用 [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) 命名空間。|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>.NET Framework 資料提供者的核心物件  
 下表概述構成.NET Framework 資料提供者的四個核心物件。  
  
|Object|描述|  
|------------|-----------------|  
|`Connection`|建立連至特定資料來源的連接。 `Connection` 類別是所有 <xref:System.Data.Common.DbConnection> 物件的基底類別 (Base Class)。|  
|`Command`|對資料來源執行命令。 公開 `Parameters` ，並可在 `Transaction` 的 `Connection`範圍中執行。 `Command` 類別是所有 <xref:System.Data.Common.DbCommand> 物件的基底類別 (Base Class)。|  
|`DataReader`|從資料來源讀取順向唯讀的資料流。 `DataReader` 類別是所有 <xref:System.Data.Common.DbDataReader> 物件的基底類別 (Base Class)。|  
|`DataAdapter`|使用資料來源填入 `DataSet` 並解析更新。 `DataAdapter` 類別是所有 <xref:System.Data.Common.DbDataAdapter> 物件的基底類別 (Base Class)。|  
  
 除了本文件稍早表格中所列的核心類別，.NET Framework 資料提供者也會包含下表中列出的類別。  
  
|Object|描述|  
|------------|-----------------|  
|`Transaction`|可讓您將命令登記在資料來源的異動中。 `Transaction` 類別是所有 <xref:System.Data.Common.DbTransaction> 物件的基底類別 (Base Class)。 ADO.NET 也支援使用 <xref:System.Transactions> 命名空間中類別的交易。|  
|`CommandBuilder`|Helper 物件，可自動產生 `DataAdapter` 的命令屬性，或從預存程序衍生參數資訊並填入 `Parameters` 物件的 `Command` 集合。 `CommandBuilder` 類別是所有 <xref:System.Data.Common.DbCommandBuilder> 物件的基底類別 (Base Class)。|  
|`ConnectionStringBuilder`|Helper 物件，可讓您簡單地建立和管理 `Connection` 物件所使用的連接字串內容。 `ConnectionStringBuilder` 類別是所有 <xref:System.Data.Common.DbConnectionStringBuilder> 物件的基底類別 (Base Class)。|  
|`Parameter`|定義命令和預存程序的輸入、輸出和傳回值參數。 `Parameter` 類別是所有 <xref:System.Data.Common.DbParameter> 物件的基底類別 (Base Class)。|  
|`Exception`|在資料來源發生錯誤時傳回。 錯誤發生在用戶端，.NET Framework 資料提供者會擲回.NET Framework 例外狀況。 `Exception` 類別是所有 <xref:System.Data.Common.DbException> 物件的基底類別 (Base Class)。|  
|`Error`|公開資料來源傳回的警告或錯誤資訊。|  
|`ClientPermission`|提供.NET Framework 資料提供者程式碼存取安全性屬性。 `ClientPermission` 類別是所有 <xref:System.Data.Common.DBDataPermission> 物件的基底類別 (Base Class)。|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>.NET Framework Data Provider for SQL Server (SqlClient)  
 .NET Framework Data Provider for SQL Server (SqlClient) 會使用它自己的通訊協定，與 SQL Server 通訊。 它是輕量，並執行很棒，因為它已最佳化，可加入的 OLE DB 或開放式資料庫連接 (ODBC) 層不直接存取 SQL Server。 下圖會對照.NET Framework Data Provider for SQL Server 與.NET Framework Data Provider for OLE DB。 .NET Framework Data Provider for OLE DB 會以透過 OLE DB 服務元件，可提供連接共用和交易服務和資料來源的 OLE DB 提供者的 OLE DB 資料來源進行通訊。  
  
> [!NOTE]
>  .NET Framework Data Provider for ODBC 有類似的架構，以.NET Framework Data Provider for OLE DB 中;比方說，它會呼叫 ODBC Service 元件。  
  
 ![資料提供者](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
比較 .NET Framework Data Provider for SQL Server 和 .NET Framework Data Provider for OLE DB  
  
 .NET Framework Data Provider for SQL Server 類別位於<xref:System.Data.SqlClient>命名空間。  
  
 .NET Framework Data Provider for SQL Server 支援本機和分散式交易。 若是分散式交易，.NET Framework Data Provider for SQL Server，根據預設，自動登記在交易中，並從 Windows 元件服務取得交易詳細資料或<xref:System.Transactions>。 如需詳細資訊，請參閱 <<c0> [ 異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 下列程式碼範例顯示如何將 `System.Data.SqlClient` 命名空間納入您的應用程式。  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>.NET Framework Data Provider for OLE DB  
 .NET Framework Data Provider for OLE DB (OleDb) 會使用原生 OLE DB 透過 COM interop 來啟用資料存取。 .NET Framework Data Provider for OLE DB 支援本機和分散式交易。 若是分散式交易，.NET Framework Data Provider for OLE DB，根據預設，自動登記在交易中，並從 Windows 元件服務取得交易詳細資料。 如需詳細資訊，請參閱 <<c0> [ 異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 下表顯示用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]測試過的提供者。  
  
|驅動器|提供者|  
|------------|--------------|  
|SQLOLEDB|SQL Server 的 Microsoft OLE DB 提供者|  
|MSDAORA|Microsoft OLE DB Provider for Oracle|  
|Microsoft.Jet.OLEDB.4.0|OLE DB provider for Microsoft Jet|  
  
> [!NOTE]
>  建議您最好不要將 Access (Jet) 資料庫當做多執行緒應用程式 (例如 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式) 的資料來源。 如果 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式必須使用 Jet 做為資料來源，則 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式連接 Access 資料庫時，可能會出現連接問題。  
  
 .NET Framework Data Provider for OLE DB 不支援 OLE DB 2.5 版的介面。 OLE DB 提供者，需要支援的 OLE DB 2.5 介面將無法正常搭配.NET Framework Data Provider for OLE DB。 這包括 Microsoft OLE DB provider for Exchange 和 Microsoft OLE DB provider for Internet Publishing。  
  
 .NET Framework Data Provider for OLE DB 無法搭配 OLE DB provider for ODBC (MSDASQL)。 若要存取 ODBC 資料來源使用[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]，使用.NET Framework Data Provider for ODBC。  
  
 .NET framework Data Provider for OLE DB 類別位於<xref:System.Data.OleDb>命名空間。 下列程式碼範例顯示如何將 `System.Data.OleDb` 命名空間納入您的應用程式。  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>.NET Framework Data Provider for ODBC  
 .NET Framework Data Provider for ODBC (Odbc) 會使用原生 ODBC 驅動程式管理員 」 (DM) 來啟用資料存取。 ODBC 資料提供者支援本機和分散式交易。 若為分散式異動，則 ODBC 資料提供者預設會自動在異動中登記，並從 Windows 元件服務取得異動詳細資料。 如需詳細資訊，請參閱 <<c0> [ 異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 下表顯示 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]測試過的 ODBC 驅動程式。  
  
|驅動器|  
|------------|  
|SQL Server|  
|Oracle 的 Microsoft ODBC|  
|Microsoft Access Driver (*.mdb)|  
  
 .NET framework Data Provider for ODBC 類別位於<xref:System.Data.Odbc>命名空間。  
  
 下列程式碼範例顯示如何將 `System.Data.Odbc` 命名空間納入您的應用程式。  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  .NET Framework Data Provider for ODBC 需要 MDAC 2.6 或更新版本，並建議使用 MDAC 2.8 SP1。 您可以從 [Data Access and Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173)(資料存取和儲存開發人員中心) 下載 MDAC 2.8 SP1。  
  
## <a name="net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle  
 .NET Framework Data Provider for Oracle (OracleClient) 可讓您透過 Oracle 用戶端連接軟體的 Oracle 資料來源的資料存取。 資料提供者支援 Oracle 用戶端軟體 8.1.7 (含) 以後版本。 資料提供者支援本機和分散式異動。 如需詳細資訊，請參閱 <<c0> [ 異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 .NET Framework Data Provider for Oracle 需要 Oracle 用戶端軟體 （8.1.7 或更新版本） 的系統上，才能連接到 Oracle 資料來源。  
  
 .NET framework Data Provider for Oracle 類別位於<xref:System.Data.OracleClient>命名空間，且包含在`System.Data.OracleClient.dll`組件。 如果編譯的應用程式有使用資料提供者，則必須參考 `System.Data.dll` 和 `System.Data.OracleClient.dll` 。  
  
 下列程式碼範例顯示如何將 `System.Data.OracleClient` 命名空間納入您的應用程式。  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>選擇 .NET Framework 資料提供者  
 根據您的應用程式的設計和資料來源，您所選擇的.NET Framework 資料提供者可以改善效能、 功能及您的應用程式的完整性。 下表討論的優點和限制每個.NET Framework 資料提供者。  
  
|提供者|注意|  
|--------------|-----------|  
|.NET Framework Data Provider for SQL Server|建議使用 Microsoft SQL Server 的中介層應用程式。<br /><br /> 建議使用 Microsoft Database Engine (MSDE) 或 SQL Server 的單層應用程式。<br /><br /> 建議使用的 OLE DB provider for SQL Server (SQLOLEDB) 搭配.NET Framework Data Provider for OLE DB。|  
|.NET Framework Data Provider for OLE DB|SQL Server 的.NET Framework Data Provider for SQL Server 建議而不是此提供者。<br /><br /> 建議使用 Microsoft Access 資料庫的單層應用程式採用。 不建議中介層應用程式採用 Access 資料庫。|  
|.NET Framework Data Provider for ODBC|建議使用 ODBC 資料來源的中介層及單層應用程式採用。|  
|.NET Framework Data Provider for Oracle|建議使用 Oracle 資料來源的中介層及單層應用程式採用。|  
  
## <a name="entityclient-provider"></a>EntityClient 提供者  
 EntityClient 提供者是用於根據實體資料模型 (EDM) 存取資料。 與其他 .NET Framework 資料提供者不同的是，它不會直接與資料來源互動。 不過，它會使用 Entity SQL 與基礎資料提供者進行通訊。 如需詳細資訊，請參閱 < [Entity Framework 的 EntityClient 提供者](./ef/entityclient-provider-for-the-entity-framework.md)。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
