---
title: 執行資料庫目錄作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: c1d8b9dd579cae7f4868058343c034caf17c5fff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362060"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="099d7-102">執行資料庫目錄作業</span><span class="sxs-lookup"><span data-stu-id="099d7-102">Performing Catalog Operations</span></span>
<span data-ttu-id="099d7-103">若要執行的命令來修改資料庫或目錄，例如 CREATE TABLE 或 CREATE PROCEDURE 陳述式，建立**命令**物件使用適當的 SQL 陳述式和**連接**物件。</span><span class="sxs-lookup"><span data-stu-id="099d7-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="099d7-104">執行命令並搭配**ExecuteNonQuery**方法**命令**物件。</span><span class="sxs-lookup"><span data-stu-id="099d7-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="099d7-105">下列程式碼範例會在 Microsoft SQL Server 資料庫中建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="099d7-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="099d7-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="099d7-106">See Also</span></span>  
 [<span data-ttu-id="099d7-107">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="099d7-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="099d7-108">命令和參數</span><span class="sxs-lookup"><span data-stu-id="099d7-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="099d7-109">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="099d7-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
