---
title: 連接到資料來源
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: b9e69b029ad37c583e51c219f87ff9d7d8e7315c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203770"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>在 ADO.NET 中連接至資料來源

在 ADO.NET 中，您可以藉由在連接字串中提供必要的驗證資訊，使用 **連接** 物件連接到特定的資料來源。 您使用的 **連接** 物件取決於資料來源的類型。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbConnection> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbConnection> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlConnection> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcConnection> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleConnection> 物件。  
  
## <a name="in-this-section"></a>本節內容  

 [建立連接](establishing-the-connection.md)\
 描述如何使用 **連接** 物件來建立與資料來源的連接。  
  
 [連接事件](connection-events.md)\
 描述如何使用 **InfoMessage** 事件從資料來源取出資訊訊息。  
  
## <a name="see-also"></a>另請參閱

- [連接字串](connection-strings.md)
- [連接共用](connection-pooling.md)
- [命令和參數](commands-and-parameters.md)
- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [異動和並行存取](transactions-and-concurrency.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
