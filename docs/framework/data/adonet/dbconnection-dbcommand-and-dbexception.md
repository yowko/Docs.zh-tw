---
title: "DbConnection、DbCommand 和 DbException"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6fb5783ad8d0863ffcce0665795081c6f2041d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection、DbCommand 和 DbException
在建立 <xref:System.Data.Common.DbProviderFactory> 和 <xref:System.Data.Common.DbConnection> 之後，接著就可以使用命令和資料讀取器從資料來源擷取資料。  
  
## <a name="retrieving-data-example"></a>擷取資料範例  
 這個範例會使用 `DbConnection` 物件做為引數。 然後會建立 <xref:System.Data.Common.DbCommand>，並藉由設定 SQL SELECT 陳述式的 <xref:System.Data.Common.DbCommand.CommandText%2A>，從 Categories 資料表選擇資料。 程式碼假設 Categories 資料表位於資料來源。 接著會開啟連接，並使用 <xref:System.Data.Common.DbDataReader> 擷取資料。  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>執行命令範例  
 這個範例會使用 `DbConnection` 物件做為引數。 如果 `DbConnection` 有效，則連接會開啟，接著再建立及執行 <xref:System.Data.Common.DbCommand>。 <xref:System.Data.Common.DbCommand.CommandText%2A> 會設定為 SQL INSERT 陳述式，以對 Northwind 資料庫的 Categories 資料表執行插入作業。 程式碼會假設 Northwind 資料庫位於資料來源，而用於 INSERT 陳述式的 SQL 語法則對指定的提供者有效。 發生在資料來源的錯誤會由 <xref:System.Data.Common.DbException> 程式碼區塊處理，所有其他的例外則是在 <xref:System.Exception> 區塊中處理。  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>使用 DbException 處理資料錯誤  
 <xref:System.Data.Common.DbException> 類別是代表資料來源所擲回之所有例外狀況的基底類別 (Base Class)。 您可以將此類別運用於例外狀況處理程式碼中，如此可以處理由不同提供者所擲回的例外狀況，但不必參照特定的例外狀況類別。 下列程式碼片段示範如何使用 <xref:System.Data.Common.DbException>，顯示由資料來源藉由 <xref:System.Exception.GetType%2A>、<xref:System.Exception.Source%2A>、<xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> 和 <xref:System.Exception.Message%2A> 等屬性所傳回的錯誤資訊。 輸出中會顯示錯誤類別、代表提供者名稱的來源、錯誤碼以及與錯誤相關聯的訊息。  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [取得 DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [使用 DbDataAdapter 修改資料](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
