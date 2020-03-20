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
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="d6719-102">更新資料來源中的資料</span><span class="sxs-lookup"><span data-stu-id="d6719-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="d6719-103">會修改資料的 SQL 陳述式 (例如 INSERT、UPDATE 或 DELETE) 不會傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="d6719-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="d6719-104">同樣地，許多預存程序會執行動作但不傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="d6719-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="d6719-105">要執行不返回行的命令，請使用相應的 SQL 命令和**連接**創建**命令**物件，包括任何必需**的參數**。</span><span class="sxs-lookup"><span data-stu-id="d6719-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="d6719-106">使用命令物件的**ExecuteNonQuery**方法執行**命令**。</span><span class="sxs-lookup"><span data-stu-id="d6719-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="d6719-107">**ExecuteNonQuery**方法返回一個整數，表示受所執行語句或預存程序影響的行數。</span><span class="sxs-lookup"><span data-stu-id="d6719-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="d6719-108">如果執行多個陳述式，傳回的值就是受到所有執行的陳述式影響的記錄數總和。</span><span class="sxs-lookup"><span data-stu-id="d6719-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6719-109">範例</span><span class="sxs-lookup"><span data-stu-id="d6719-109">Example</span></span>  
 <span data-ttu-id="d6719-110">以下代碼示例執行 INSERT 語句，以便使用**ExecuteNonQuery**將記錄插入到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d6719-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="d6719-111">以下代碼示例執行[由執行目錄操作](performing-catalog-operations.md)中的示例代碼創建的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d6719-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="d6719-112">預存程序不返回任何行，因此使用**ExecuteNonQuery**方法，但預存程序確實接收輸入參數並返回輸出參數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="d6719-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="d6719-113">對於<xref:System.Data.OleDb.OleDbCommand>物件，必須首先將**ReturnValue** **參數添加到參數**集合中。</span><span class="sxs-lookup"><span data-stu-id="d6719-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6719-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6719-114">See also</span></span>

- [<span data-ttu-id="d6719-115">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="d6719-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="d6719-116">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="d6719-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="d6719-117">命令和參數</span><span class="sxs-lookup"><span data-stu-id="d6719-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- <span data-ttu-id="d6719-118">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="d6719-118">[ADO.NET Overview](ado-net-overview.md)</span></span>
