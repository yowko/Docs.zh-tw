---
title: .NET Framework 資料提供者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: 3891cae272d93c2bb1ba8929a40fbdb8c332765c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785646"
---
# <a name="net-framework-data-providers"></a>.NET Framework 資料提供者
.NET Framework Data Provider 用來連接到資料庫、執行命令和抓取結果。 這些結果會直接處理、放入 <xref:System.Data.DataSet> 中以便視需要而公開給使用者、與多個來源的資料結合，或在各層之間進行遠端控制。 .NET Framework 資料提供者是輕量的，可在資料來源和程式碼之間建立最小的層級，而不會犧牲功能而提升效能。  
  
 下表列出包含在 .NET Framework 中的資料提供者。  
  
|.NET Framework Data Provider - .NET Framework 資料提供者|說明|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET Framework Data Provider for SQL Server|提供 Microsoft SQL Server 的資料存取。 使用 <xref:System.Data.SqlClient> 命名空間。|  
|.NET Framework Data Provider for OLE DB|使用 OLE DB 公開的資料來源。 使用 <xref:System.Data.OleDb> 命名空間。|  
|.NET Framework Data Provider for ODBC|使用 ODBC 公開的資料來源。 使用 <xref:System.Data.Odbc> 命名空間。|  
|.NET Framework Data Provider for Oracle|針對 Oracle 資料來源。 Oracle 的 .NET Framework Data Provider 支援 oracle 用戶端軟體版本8.1.7 和更新版本，並使用<xref:System.Data.OracleClient>命名空間。|  
|EntityClient 提供者|為實體資料模型 (EDM) 應用程式提供資料存取。 使用 <xref:System.Data.EntityClient> 命名空間。|  
|SQL Server Compact 4.0 的 .NET Framework Data Provider。|提供 Microsoft SQL Server Compact 4.0 的資料存取。 使用 [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) 命名空間。|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>.NET Framework 資料提供者的核心物件  
 下表概述組成 .NET Framework Data Provider 的四個核心物件。  
  
|Object|描述|  
|------------|-----------------|  
|`Connection`|建立連至特定資料來源的連接。 `Connection` 類別是所有 <xref:System.Data.Common.DbConnection> 物件的基底類別 (Base Class)。|  
|`Command`|對資料來源執行命令。 公開 `Parameters` ，並可在 `Transaction` 的 `Connection`範圍中執行。 `Command` 類別是所有 <xref:System.Data.Common.DbCommand> 物件的基底類別 (Base Class)。|  
|`DataReader`|從資料來源讀取順向唯讀的資料流。 `DataReader` 類別是所有 <xref:System.Data.Common.DbDataReader> 物件的基底類別 (Base Class)。|  
|`DataAdapter`|使用資料來源填入 `DataSet` 並解析更新。 `DataAdapter` 類別是所有 <xref:System.Data.Common.DbDataAdapter> 物件的基底類別 (Base Class)。|  
  
 除了本檔稍早的表格中所列的核心類別之外，.NET Framework Data Provider 也包含下表所列的類別。  
  
|Object|描述|  
|------------|-----------------|  
|`Transaction`|可讓您將命令登記在資料來源的異動中。 `Transaction` 類別是所有 <xref:System.Data.Common.DbTransaction> 物件的基底類別 (Base Class)。 ADO.NET 也支援使用 <xref:System.Transactions> 命名空間中類別的交易。|  
|`CommandBuilder`|Helper 物件，可自動產生 `DataAdapter` 的命令屬性，或從預存程序衍生參數資訊並填入 `Parameters` 物件的 `Command` 集合。 `CommandBuilder` 類別是所有 <xref:System.Data.Common.DbCommandBuilder> 物件的基底類別 (Base Class)。|  
|`ConnectionStringBuilder`|Helper 物件，可讓您簡單地建立和管理 `Connection` 物件所使用的連接字串內容。 `ConnectionStringBuilder` 類別是所有 <xref:System.Data.Common.DbConnectionStringBuilder> 物件的基底類別 (Base Class)。|  
|`Parameter`|定義命令和預存程序的輸入、輸出和傳回值參數。 `Parameter` 類別是所有 <xref:System.Data.Common.DbParameter> 物件的基底類別 (Base Class)。|  
|`Exception`|在資料來源發生錯誤時傳回。 若為用戶端發生的錯誤，.NET Framework 資料提供者會擲回 .NET Framework 例外狀況。 `Exception` 類別是所有 <xref:System.Data.Common.DbException> 物件的基底類別 (Base Class)。|  
|`Error`|公開資料來源傳回的警告或錯誤資訊。|  
|`ClientPermission`|提供 .NET Framework Data Provider 代碼啟用安全性屬性。 `ClientPermission` 類別是所有 <xref:System.Data.Common.DBDataPermission> 物件的基底類別 (Base Class)。|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>.NET Framework Data Provider for SQL Server (SqlClient)  
 SQL Server （SqlClient）的 .NET Framework Data Provider 會使用自己的通訊協定與 SQL Server 進行通訊。 它既輕量又順利執行，因為它已經過優化，而不會加入 OLE DB 或開放式資料庫連接（ODBC）層，而直接存取 SQL Server。 下圖會將 SQL Server 的 .NET Framework Data Provider 與 Data Provider 的 .NET Framework OLE DB 形成對比。 OLE DB 的 .NET Framework Data Provider 會透過 OLE DB 服務元件（可提供連接共用和交易服務）和資料來源的 OLE DB 提供者，與 OLE DB 資料來源進行通訊。  
  
> [!NOTE]
> ODBC 的 .NET Framework Data Provider 與 OLE DB 的 .NET Framework Data Provider 有類似的架構;例如，它會呼叫 ODBC 服務元件。  
  
 ![資料提供者](./media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
比較 .NET Framework Data Provider for SQL Server 和 .NET Framework Data Provider for OLE DB  
  
 SQL Server 類別的 .NET Framework Data Provider 位於<xref:System.Data.SqlClient>命名空間中。  
  
 SQL Server 的 .NET Framework Data Provider 同時支援本機和分散式交易。 若為分散式交易，SQL Server 的 .NET Framework Data Provider 預設會自動在交易中登記，並從 Windows 元件服務或<xref:System.Transactions>取得交易詳細資料。 如需詳細資訊，請參閱[交易和並行](transactions-and-concurrency.md)。  
  
 下列程式碼範例顯示如何將 `System.Data.SqlClient` 命名空間納入您的應用程式。  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>.NET Framework Data Provider for OLE DB  
 OLE DB （OleDb）的 .NET Framework Data Provider 會透過 COM Interop 使用原生 OLE DB 來啟用資料存取。 OLE DB 的 .NET Framework Data Provider 同時支援本機和分散式交易。 若為分散式交易，OLE DB 的 .NET Framework Data Provider 預設會自動在交易中登記，並從 Windows 元件服務取得交易詳細資料。 如需詳細資訊，請參閱[交易和並行](transactions-and-concurrency.md)。  
  
 下表顯示已使用 ADO.NET 測試的提供者。  
  
|驅動器|提供者|  
|------------|--------------|  
|SQLOLEDB|適用于 SQL Server 的 Microsoft OLE DB 提供者|  
|MSDAORA|Microsoft OLE DB Provider for Oracle|  
|Microsoft.Jet.OLEDB.4.0|OLE DB provider for Microsoft Jet|  
  
> [!NOTE]
> 不建議使用 Access （Jet）資料庫做為多執行緒應用程式（例如 ASP.NET 應用程式）的資料來源。 如果您必須使用 Jet 作為 ASP.NET 應用程式的資料來源，請注意，連接到 Access 資料庫的 ASP.NET 應用程式可能會遇到連接問題。  
  
 OLE DB 的 .NET Framework Data Provider 不支援 OLE DB 版本2.5 介面。 需要 OLE DB 2.5 介面支援的 OLE DB 提供者，將無法使用 OLE DB 的 .NET Framework Data Provider 來正常運作。 這包括 Microsoft OLE DB provider for Exchange 和 Microsoft OLE DB provider for Internet Publishing。  
  
 OLE DB 的 .NET Framework Data Provider 無法與 ODBC 的 OLE DB 提供者（MSDASQL）搭配使用。 若要使用 ADO.NET 存取 ODBC 資料來源，請使用 ODBC 的 .NET Framework Data Provider。  
  
 OLE DB 類別的 .NET Framework Data Provider 位於<xref:System.Data.OleDb>命名空間中。 下列程式碼範例顯示如何將 `System.Data.OleDb` 命名空間納入您的應用程式。  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>.NET Framework Data Provider for ODBC  
 ODBC （Odbc）的 .NET Framework Data Provider 會使用原生 ODBC 驅動程式管理員（DM）來啟用資料存取。 ODBC 資料提供者支援本機和分散式交易。 若為分散式異動，則 ODBC 資料提供者預設會自動在異動中登記，並從 Windows 元件服務取得異動詳細資料。 如需詳細資訊，請參閱[交易和並行](transactions-and-concurrency.md)。  
  
 下表顯示以 ADO.NET 測試的 ODBC 驅動程式。  
  
|驅動器|  
|------------|  
|SQL Server|  
|Oracle 的 Microsoft ODBC|  
|Microsoft Access Driver (*.mdb)|  
  
 ODBC 類別的 .NET Framework Data Provider 位於<xref:System.Data.Odbc>命名空間中。  
  
 下列程式碼範例顯示如何將 `System.Data.Odbc` 命名空間納入您的應用程式。  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
> ODBC 的 .NET Framework Data Provider 需要 MDAC 2.6 或更新版本，建議使用 MDAC 2.8 SP1。 您可以從 [Data Access and Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173)(資料存取和儲存開發人員中心) 下載 MDAC 2.8 SP1。  
  
## <a name="net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle  
 Oracle 的 .NET Framework Data Provider （OracleClient）可讓您透過 Oracle 用戶端連線軟體，對 Oracle 資料來源進行資料存取。 資料提供者支援 Oracle 用戶端軟體 8.1.7 (含) 以後版本。 資料提供者支援本機和分散式異動。 如需詳細資訊，請參閱[交易和並行](transactions-and-concurrency.md)。  
  
 Oracle 的 .NET Framework Data Provider 需要系統上的 Oracle 用戶端軟體（版本8.1.7 或更新版本），您才能連接到 Oracle 資料來源。  
  
 Oracle 類別的 .NET Framework Data Provider 位於<xref:System.Data.OracleClient>命名空間中，而且包含`System.Data.OracleClient.dll`在元件中。 如果編譯的應用程式有使用資料提供者，則必須參考 `System.Data.dll` 和 `System.Data.OracleClient.dll` 。  
  
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
 視您應用程式的設計和資料來源而定，您選擇的 .NET Framework Data Provider 可以改善應用程式的效能、功能及完整性。 下表討論每個 .NET Framework Data Provider 的優點和限制。  
  
|提供者|注意|  
|--------------|-----------|  
|.NET Framework Data Provider for SQL Server|建議使用 Microsoft SQL Server 的中介層應用程式。<br /><br /> 建議使用 Microsoft 資料庫引擎（MSDE）或 SQL Server 的單一層應用程式。<br /><br /> 建議使用適用于 SQL Server （SQLOLEDB）的 OLE DB 提供者搭配 OLE DB 的 .NET Framework Data Provider。|  
|.NET Framework Data Provider for OLE DB|針對 SQL Server，建議使用 SQL Server 的 .NET Framework Data Provider，而不是此提供者。<br /><br /> 建議使用 Microsoft Access 資料庫的單層應用程式採用。 不建議中介層應用程式採用 Access 資料庫。|  
|.NET Framework Data Provider for ODBC|建議使用 ODBC 資料來源的中介層及單層應用程式採用。|  
|.NET Framework Data Provider for Oracle|建議使用 Oracle 資料來源的中介層及單層應用程式採用。|  
  
## <a name="entityclient-provider"></a>EntityClient 提供者  
 EntityClient 提供者是用於根據實體資料模型 (EDM) 存取資料。 與其他 .NET Framework 資料提供者不同的是，它不會直接與資料來源互動。 不過，它會使用 Entity SQL 與基礎資料提供者進行通訊。 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](./ef/entityclient-provider-for-the-entity-framework.md)。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](ado-net-overview.md)
- [在 ADO.NET 中擷取和修改資料](retrieving-and-modifying-data.md)
