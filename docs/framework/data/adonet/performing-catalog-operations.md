---
title: 執行資料庫目錄作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: bedeb4e9c510a3feeedc038e9c4cef6c4721e345
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149241"
---
# <a name="performing-catalog-operations"></a>執行資料庫目錄作業
要執行修改資料庫或目錄的命令（如創建表或創建過程語句），請使用相應的 SQL 語句和**連接**物件創建**命令**物件。 使用命令物件的**ExecuteNonQuery**方法執行**命令**。  
  
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

- [使用命令修改資料](using-commands-to-modify-data.md)
- [命令和參數](commands-and-parameters.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
