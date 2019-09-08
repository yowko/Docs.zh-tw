---
title: 命令和參數
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 1d0c3adb56e5ff44b5c5e065ac040f25584a1946
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784962"
---
# <a name="commands-and-parameters"></a>命令和參數
建立連至資料來源的連接後，您可以執行命令，並使用 <xref:System.Data.Common.DbCommand> 物件從資料來源傳回結果。 您可以使用目前使用中 .NET Framework 資料提供者的其中一個命令建構函式 (Constructor) 來建立命令。 建構函式可以接受選擇性引數，例如要在資料來源執行的 SQL 陳述式、<xref:System.Data.Common.DbConnection> 物件或 <xref:System.Data.Common.DbTransaction> 物件。 此外，您也可以將這些物件設定為命令的屬性。 您還可以使用 <xref:System.Data.Common.DbConnection.CreateCommand%2A> 物件的 `DbConnection` 方法，針對特定連接建立命令。 您可以使用 <xref:System.Data.Common.DbCommand.CommandText%2A> 屬性來設定正由命令執行的 SQL 陳述式。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有一個 `Command` 物件。 .NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbCommand> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlCommand> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcCommand> 物件，而 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleCommand> 物件。  
  
## <a name="in-this-section"></a>本節內容  
 [執行命令](executing-a-command.md)  
 說明 ADO.NET `Command` 物件，以及如何用它來針對資料來源執行查詢和命令。  
  
 [設定參數和參數資料類型](configuring-parameters-and-parameter-data-types.md)  
 說明如何使用 `Command` 參數，包括方向、資料型別和參數語法。  
  
 [使用 CommandBuilder 產生命令](generating-commands-with-commandbuilders.md)  
 說明如何使用命令產生器，針對具有單一資料表 SELECT 命令的 `DataAdapter` 自動產生 INSERT、UPDATE 和 DELETE 命令。  
  
 [從資料庫取得單一值](obtaining-a-single-value-from-a-database.md)  
 說明如何使用 `ExecuteScalar` 物件的 `Command` 方法，從資料庫查詢傳回單一值。  
  
 [使用命令修改資料](using-commands-to-modify-data.md)  
 說明如何使用資料提供者來執行預存程序 (Stored Procedure) 或資料定義語言 (DDL) 陳述式。  
  
## <a name="see-also"></a>另請參閱

- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [DataSet、DataTable 和 DataView](./dataset-datatable-dataview/index.md)
- [連接至資料來源](connecting-to-a-data-source.md)
- [ADO.NET 概觀](ado-net-overview.md)
