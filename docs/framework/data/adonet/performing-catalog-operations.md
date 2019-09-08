---
title: 執行資料庫目錄作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 0291b6684092ec15fc672c39c909caf7781194e3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783251"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="2ac3a-102">執行資料庫目錄作業</span><span class="sxs-lookup"><span data-stu-id="2ac3a-102">Performing Catalog Operations</span></span>
<span data-ttu-id="2ac3a-103">若要執行命令來修改資料庫或目錄，例如 CREATE TABLE 或 CREATE PROCEDURE 語句，請使用適當的 SQL 語句和**連接**物件來建立**命令**物件。</span><span class="sxs-lookup"><span data-stu-id="2ac3a-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="2ac3a-104">使用**command**物件的**ExecuteNonQuery**方法來執行命令。</span><span class="sxs-lookup"><span data-stu-id="2ac3a-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="2ac3a-105">下列程式碼範例會在 Microsoft SQL Server 資料庫中建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="2ac3a-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ac3a-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ac3a-106">See also</span></span>

- [<span data-ttu-id="2ac3a-107">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="2ac3a-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="2ac3a-108">命令和參數</span><span class="sxs-lookup"><span data-stu-id="2ac3a-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="2ac3a-109">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="2ac3a-109">ADO.NET Overview</span></span>](ado-net-overview.md)
