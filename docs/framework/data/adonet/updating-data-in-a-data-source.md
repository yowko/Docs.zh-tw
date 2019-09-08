---
title: 更新資料來源中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780609"
---
# <a name="updating-data-in-a-data-source"></a>更新資料來源中的資料
會修改資料的 SQL 陳述式 (例如 INSERT、UPDATE 或 DELETE) 不會傳回資料列。 同樣地，許多預存程序會執行動作但不傳回資料列。 若要執行不會傳回資料列的命令，請使用適當的 SQL 命令和**連接**（包括任何必要的**參數**）來建立**命令**物件。 使用**command**物件的**ExecuteNonQuery**方法來執行命令。  
  
 **ExecuteNonQuery**方法會傳回一個整數，表示受執行的語句或預存程式所影響的資料列數目。 如果執行多個陳述式，傳回的值就是受到所有執行的陳述式影響的記錄數總和。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用**ExecuteNonQuery**來執行 insert 語句，將記錄插入資料庫中。  
  
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
  
 下列程式碼範例會執行[執行目錄作業](performing-catalog-operations.md)中的範例程式碼所建立的預存程式。 預存程式不會傳回任何資料列，因此會使用**ExecuteNonQuery**方法，但預存程式確實會接收輸入參數，並傳回輸出參數和傳回值。  
  
 若為物件，必須先將 ReturnValue 參數新增至 Parameters 集合。 <xref:System.Data.OleDb.OleDbCommand>  
  
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
- [ADO.NET 概觀](ado-net-overview.md)
