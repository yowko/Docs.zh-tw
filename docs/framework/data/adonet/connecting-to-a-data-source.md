---
title: 在 ADO.NET 中連接至資料來源
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: f5788b9b0b19f32d03c917575db7b3f40324c0a2
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274079"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>在 ADO.NET 中連接至資料來源
在 ADO.NET 中使用**連線**物件來連接到特定的資料來源提供連接字串中的所需的驗證資訊。 **連線**您所使用的物件取決於資料來源的類型。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbConnection> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbConnection> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlConnection> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcConnection> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleConnection> 物件。  
  
## <a name="in-this-section"></a>本節內容  
 [建立連線](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 描述如何使用**連線**物件來建立資料來源的連接。  
  
 [Connection 事件](../../../../docs/framework/data/adonet/connection-events.md)  
 描述如何使用**InfoMessage**事件，以擷取從資料來源的參考用訊息。  
  
## <a name="see-also"></a>另請參閱  
 [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)  
 [連接共用](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
