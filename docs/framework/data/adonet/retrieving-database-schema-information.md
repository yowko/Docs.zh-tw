---
title: 擷取資料庫結構描述資訊
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 1ac39a556fd7539550b12cb71b701c4bd3224a0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359685"
---
# <a name="retrieving-database-schema-information"></a>擷取資料庫結構描述資訊
從資料庫取得結構描述資訊是透過結構描述探索處理序來完成。 結構描述探索允許應用程式要求 managed 提供者尋找並傳回資料庫結構描述的相關資訊，也稱為*中繼資料*，針對給定的資料庫。 不同的資料庫結構描述項目 (如資料表、資料行及預存程序) 都透過結構描述集合公開。 每個結構描述集合都包含正在使用的提供者之各種特定的結構描述資訊。  
  
 每個.NET Framework managed 提供者實作**GetSchema**方法中的**連接**類別，而從傳回的結構描述資訊**GetSchema**方法的形式提供<xref:System.Data.DataTable>。 **GetSchema**方法是多載的方法，為指定要傳回結構描述集合及限制傳回的資訊量，提供選擇性參數。  
  
 .NET Framework Data Provider for OLE DB、 ODBC、 Oracle 和 SqlClient 提供**GetSchemaTable**方法會傳回描述資料行中繼資料的 DataTable **DataReader**。  
  
 .NET Framework Data Provider for OLE DB 也會使用 <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> 物件的 <xref:System.Data.OleDb.OleDbConnection> 方法來公開結構描述資訊。 做為引數， **GetOleDbSchemaTable**採用<xref:System.Data.OleDb.OleDbSchemaGuid>可識別要傳回的結構描述資訊以及陣列的那些限制傳回資料行。 **GetOleDbSchemaTable**傳回<xref:System.Data.DataTable>填入要求的結構描述資訊。  
  
## <a name="in-this-section"></a>本節內容  
 [GetSchema 和結構描述集合](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 描述**GetSchema**方法，以及如何使用它來擷取及限制資料庫的結構描述資訊。  
  
 結構描述限制  
 描述可以搭配使用的結構描述限制**GetSchema**。  
  
 [一般結構描述集合](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 說明所有 .NET Framework Managed 提供者支援的所有通用結構描述集合。  
  
 [SQL Server 結構描述集合](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 說明 .NET Framework Provider for SQL Server 所支援的結構描述集合。  
  
 [Oracle 結構描述集合](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 說明 .NET Framework Provider for Oracle 所支援的結構描述集合。  
  
 [ODBC 結構描述集合](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 說明 ODBC 驅動程式的結構描述集合。  
  
 [OLE DB 結構描述集合](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 說明 OLE DB 提供者的結構描述集合。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 描述**GetSchema**方法<xref:System.Data.Common.DbConnection>類別。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 描述**GetSchema**方法<xref:System.Data.Odbc.OdbcConnection>類別。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 描述**GetSchema**方法<xref:System.Data.OleDb.OleDbConnection>類別。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 描述**GetSchema**方法<xref:System.Data.OracleClient.OracleConnection>類別。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 描述**GetSchema**方法<xref:System.Data.SqlClient.SqlConnection>類別。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 描述**GetSchemaTable**方法<xref:System.Data.Common.DbDataReader>類別。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 描述**GetSchemaTable**方法<xref:System.Data.Odbc.OdbcDataReader>類別。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 描述**GetSchemaTable**方法<xref:System.Data.OleDb.OleDbDataReader>類別。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 描述**GetSchemaTable**方法<xref:System.Data.OracleClient.OracleDataReader>類別。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 描述**GetSchemaTable**方法<xref:System.Data.SqlClient.SqlDataReader>類別。  
  
## <a name="see-also"></a>另請參閱  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
