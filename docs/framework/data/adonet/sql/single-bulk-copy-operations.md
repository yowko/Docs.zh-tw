---
title: "單一大量複製作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 單一大量複製作業
執行 SQL Server 大量複製作業的最簡單方法是：針對資料庫執行單一作業。  根據預設，會以隔離作業執行大量複製作業：複製作業會以非交易性方式執行，且沒有復原的機會。  
  
> [!NOTE]
>  如果需要在發生錯誤時，復原全部或部分大量複製，您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 管理的交易，或在現有交易內執行大量複製作業。  如果將連接 \(以隱含或明確的方式\) 登記到 **System.Transactions** 交易中，則 **SqlBulkCopy** 也會使用 <xref:System.Transactions>。  
>   
>  如需詳細資訊，請參閱[交易和大量複製作業](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)。  
  
 執行大量複製作業的一般步驟如下：  
  
1.  連接至來源伺服器，並取得要複製的資料。  如果可從 <xref:System.Data.IDataReader> 或 <xref:System.Data.DataTable> 物件擷取資料，則資料也可來自其他來源。  
  
2.  連接至目的伺服器 \(除非您要讓 **SqlBulkCopy** 建立連接\)。  
  
3.  建立 <xref:System.Data.SqlClient.SqlBulkCopy> 物件，設定所有必要的屬性。  
  
4.  設定 **DestinationTableName** 屬性，以表示用於大量插入作業的目標資料表。  
  
5.  呼叫其中一個 **WriteToServer** 方法。  
  
6.  視需要，選擇性地更新屬性，並重新呼叫 **WriteToServer**。  
  
7.  呼叫 <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>，或將大量複製作業包裝至 `Using` 陳述式內。  
  
> [!CAUTION]
>  建議來源與目標資料行的資料型別相符。  如果資料型別不相符，則 **SqlBulkCopy** 會嘗試使用 <xref:System.Data.SqlClient.SqlParameter.Value%2A> 所使用的規則，將每個來源值轉換為目標資料型別。  轉換可能會影響效能，亦可能導致意外的錯誤。  例如，`Double` 資料型別通常可轉換為 `Decimal` 資料型別，但並非始終如此。  
  
## 範例  
 下列主控台應用程式示範如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別來載入資料。  在這個範例中，<xref:System.Data.SqlClient.SqlDataReader> 用於從 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] **AdventureWorks** 資料庫的 **Production.Product** 資料表，將資料複製到同一資料庫中的類似資料表中。  
  
> [!IMPORTANT]
>  除非您已依照[大量複製範例設定](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)所述來建立工作資料表，否則此範例將無法執行。  這個程式碼僅是為了示範使用 **SqlBulkCopy** 的語法而提供。  如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact\-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## 使用 Transact\-SQL 及命令類別來執行大量複製作業  
 下列範例說明如何使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法執行 BULK INSERT 陳述式。  
  
> [!NOTE]
>  資料來源的檔案路徑是與伺服器相對的。  伺服器處理序必須存取該路徑，才能順利完成大量複製作業。  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## 請參閱  
 [SQL Server 中的大量複製作業](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)