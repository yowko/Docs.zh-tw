---
title: 執行資料庫目錄作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: beb5d2db898df1c98662d53190ac1432acc746e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141449"
---
# <a name="performing-catalog-operations"></a>執行資料庫目錄作業
若要執行的命令來修改資料庫或目錄，例如 CREATE TABLE 或 CREATE PROCEDURE 陳述式中，建立**命令**物件使用適當的 SQL 陳述式並**連線**物件。 執行命令**ExecuteNonQuery**方法**命令**物件。  
  
 下列程式碼範例會在 Microsoft SQL Server 資料庫中建立預存程序。  
  
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
  
## <a name="see-also"></a>另請參閱

- [使用命令修改資料](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
