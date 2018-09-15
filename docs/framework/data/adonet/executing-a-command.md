---
title: 執行命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: ed5ae1cbab40b57676219ffbe7d1d5696ac3bec4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647271"
---
# <a name="executing-a-command"></a>執行命令
內含在 .NET Framework 中的每個 .NET Framework 資料提供者本身都有命令物件，此物件是繼承自 <xref:System.Data.Common.DbCommand>。 .NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbCommand> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlCommand> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcCommand> 物件，而 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleCommand> 物件。 上述每種物件都會根據命令類型和想要的傳回值而公開 (Expose) 執行命令的方法，如下表所述。  
  
|命令|傳回值|  
|-------------|------------------|  
|`ExecuteReader`|傳回 `DataReader` 物件。|  
|`ExecuteScalar`|傳回單一純量值。|  
|`ExecuteNonQuery`|執行不會傳回任何資料列的命令。|  
|`ExecuteXMLReader`|傳回 <xref:System.Xml.XmlReader>。 僅適用於 `SqlCommand` 物件。|  
  
 每個強型別 (Strongly Typed) 的命令物件也會支援 <xref:System.Data.CommandType> 列舉型別 (Enumeration)，此型別可指定解譯命令字串的方式。  
  
|CommandType|描述|  
|-----------------|-----------------|  
|`Text`|SQL 命令，可定義在資料來源執行的陳述式。|  
|`StoredProcedure`|預存程序 (Stored Procedure) 的名稱。 您可以使用命令的 `Parameters` 屬性來存取輸入和輸出參數及傳回值，不論呼叫的是哪一個 `Execute` 方法。 在使用 `ExecuteReader` 時，無法在 `DataReader` 關閉之前存取傳回值和輸出參數。|  
|`TableDirect`|資料表的名稱。|  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立 <xref:System.Data.SqlClient.SqlCommand> 物件，以藉由設定其屬性來執行預存程序。 用來指定預存程序輸出參數的 <xref:System.Data.SqlClient.SqlParameter> 物件。 此命令是藉由使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法來執行，而 <xref:System.Data.SqlClient.SqlDataReader> 的輸出則會顯示在主控台視窗中。  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>疑難排解命令  
 .NET Framework Data Provider for SQL Server 加入一個效能計數器，可讓您偵測與失敗命令執行相關的週期性問題。 如需詳細資訊，請參閱[效能計數器](../../../../docs/framework/data/adonet/performance-counters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [使用 Datareader](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
