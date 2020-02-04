---
title: 連接資料來源
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 84dc15c0965b7ac8209bd9115d611162e57d6dda
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980245"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>在 ADO.NET 中連接至資料來源
在 ADO.NET 中，您可以使用**連接**物件來連接到特定資料來源，方法是在連接字串中提供必要的驗證資訊。 您所使用的**連接**物件取決於資料來源的類型。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbConnection> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbConnection> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlConnection> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcConnection> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleConnection> 物件。  
  
## <a name="in-this-section"></a>本章節內容  
 [建立連線](establishing-the-connection.md)  
 描述如何使用**連接**物件來建立資料來源的連接。  
  
 [Connection 事件](connection-events.md)  
 描述如何使用**InfoMessage**事件從資料來源取出參考用訊息。  
  
## <a name="see-also"></a>請參閱

- [連接字串](connection-strings.md)
- [連接共用](connection-pooling.md)
- [命令和參數](commands-and-parameters.md)
- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [異動和並行存取](transactions-and-concurrency.md)
- [ADO.NET 概觀](ado-net-overview.md)
