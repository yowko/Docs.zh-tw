---
title: 更新資料來源中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 18bb03e17b19243ee1bc6e3f7ebd70afb4d4c60b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174442"
---
# <a name="updating-data-in-a-data-source"></a>更新資料來源中的資料
會修改資料的 SQL 陳述式 (例如 INSERT、UPDATE 或 DELETE) 不會傳回資料列。 同樣地，許多預存程序會執行動作但不傳回資料列。 要執行不返回行的命令，請使用相應的 SQL 命令和**連接**創建**命令**物件，包括任何必需**的參數**。 使用命令物件的**ExecuteNonQuery**方法執行**命令**。  
  
 **ExecuteNonQuery**方法返回一個整數，表示受所執行語句或預存程序影響的行數。 如果執行多個陳述式，傳回的值就是受到所有執行的陳述式影響的記錄數總和。  
  
## <a name="example"></a>範例  
 以下代碼示例執行 INSERT 語句，以便使用**ExecuteNonQuery**將記錄插入到資料庫中。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 以下代碼示例執行[由執行目錄操作](performing-catalog-operations.md)中的示例代碼創建的預存程序。 預存程序不返回任何行，因此使用**ExecuteNonQuery**方法，但預存程序確實接收輸入參數並返回輸出參數和傳回值。  
  
 對於<xref:System.Data.OleDb.OleDbCommand>物件，必須首先將**ReturnValue** **參數添加到參數**集合中。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a>另請參閱

- [使用命令修改資料](using-commands-to-modify-data.md)
- [使用 DataAdapter 更新資料來源](updating-data-sources-with-dataadapters.md)
- [命令和參數](commands-and-parameters.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
