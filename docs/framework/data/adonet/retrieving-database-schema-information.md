---
title: 擷取資料庫結構描述資訊
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: c0aaadc82771d1c2a36d797bc157d88b8d3cacdc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177354"
---
# <a name="retrieving-database-schema-information"></a>擷取資料庫結構描述資訊

從資料庫取得結構描述資訊是透過結構描述探索處理序來完成。 架構探索可讓應用程式要求受管理的提供者尋找並傳回指定資料庫之資料庫架構（也稱為 *中繼資料*）的相關資訊。 不同的資料庫結構描述項目 (如資料表、資料行及預存程序) 都透過結構描述集合公開。 每個結構描述集合都包含正在使用的提供者之各種特定的結構描述資訊。  
  
 每個 .NET Framework managed 提供者都會在**連接**類別中執行**GetSchema**方法，而從**GetSchema**方法傳回的架構資訊則會以的形式呈現 <xref:System.Data.DataTable> 。 **GetSchema**方法是一種多載方法，可提供選擇性參數來指定要傳回的架構集合，以及限制傳回的資訊量。  
  
 適用于 OLE DB、ODBC、Oracle 和 SqlClient 的 .NET Framework 資料提供者會提供 **GetSchemaTable** 方法，以傳回描述 **DataReader**之資料行中繼資料的 DataTable。  
  
 .NET Framework Data Provider for OLE DB 也會使用 <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> 物件的 <xref:System.Data.OleDb.OleDbConnection> 方法來公開結構描述資訊。 作為引數， **GetOleDbSchemaTable** 會接受 <xref:System.Data.OleDb.OleDbSchemaGuid> ，以識別要傳回的架構資訊，以及對這些傳回之資料行的限制陣列。 **GetOleDbSchemaTable** 會傳回 <xref:System.Data.DataTable> 填入所要求架構資訊的。  
  
## <a name="in-this-section"></a>本節內容  

 [GetSchema 和結構描述集合](getschema-and-schema-collections.md)  
 描述 **GetSchema** 方法，以及如何使用它來從資料庫中取出和限制架構資訊。  
  
 結構描述限制  
 描述可搭配 **GetSchema**使用的架構限制。  
  
 [一般結構描述集合](common-schema-collections.md)  
 說明所有 .NET Framework Managed 提供者支援的所有通用結構描述集合。  
  
 [SQL Server 結構描述集合](sql-server-schema-collections.md)  
 說明 .NET Framework Provider for SQL Server 所支援的結構描述集合。  
  
 [Oracle 結構描述集合](oracle-schema-collections.md)  
 說明 .NET Framework Provider for Oracle 所支援的結構描述集合。  
  
 [ODBC 結構描述集合](odbc-schema-collections.md)  
 說明 ODBC 驅動程式的結構描述集合。  
  
 [OLE DB 結構描述集合](ole-db-schema-collections.md)  
 說明 OLE DB 提供者的結構描述集合。  
  
## <a name="reference"></a>參考  

 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 描述類別的 **GetSchema** 方法 <xref:System.Data.Common.DbConnection> 。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 描述類別的 **GetSchema** 方法 <xref:System.Data.Odbc.OdbcConnection> 。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 描述類別的 **GetSchema** 方法 <xref:System.Data.OleDb.OleDbConnection> 。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 描述類別的 **GetSchema** 方法 <xref:System.Data.OracleClient.OracleConnection> 。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 描述類別的 **GetSchema** 方法 <xref:System.Data.SqlClient.SqlConnection> 。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 描述類別的 **GetSchemaTable** 方法 <xref:System.Data.Common.DbDataReader> 。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 描述類別的 **GetSchemaTable** 方法 <xref:System.Data.Odbc.OdbcDataReader> 。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 描述類別的 **GetSchemaTable** 方法 <xref:System.Data.OleDb.OleDbDataReader> 。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 描述類別的 **GetSchemaTable** 方法 <xref:System.Data.OracleClient.OracleDataReader> 。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 描述類別的 **GetSchemaTable** 方法 <xref:System.Data.SqlClient.SqlDataReader> 。  
  
## <a name="see-also"></a>另請參閱

- [在 ADO.NET 中傳送和修改資料](retrieving-and-modifying-data.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
