---
title: 在 ADO.NET 中連接至資料來源
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 27653c3e1f14e08fc8b5e1225a441072778a0cc8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-a-data-source-in-adonet"></a>在 ADO.NET 中連接至資料來源
在 ADO.NET 中使用**連接**物件連接至特定資料來源，藉由提供連接字串中的必要的驗證資訊。 **連接**的資料來源類型取決於您使用的物件。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbConnection> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbConnection> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlConnection> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcConnection> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleConnection> 物件。  
  
## <a name="in-this-section"></a>本節內容  
 [建立連線](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 描述如何使用**連接**物件來建立資料來源的連接。  
  
 [Connection 事件](../../../../docs/framework/data/adonet/connection-events.md)  
 描述如何使用**InfoMessage**事件，以擷取從資料來源的參考用訊息。  
  
## <a name="see-also"></a>另請參閱  
 [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)  
 [連接共用](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
