---
title: "使用預存程序修改資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 使用預存程序修改資料
預存程序 \(Stored Procedure\) 可以接受資料做為輸入參數，也可以將資料以輸出參數、結果集 \(Result Set\) 或傳回值的形式傳回。  下列範例說明 ADO.NET 如何傳送及接收輸入參數、輸出參數和傳回值。  此範例會將新記錄插入資料表 \(該資料表的主索引鍵資料行是 SQL Server 資料庫中的識別欄位\)。  
  
> [!NOTE]
>  如果您要使用 SQL Server 預存程序搭配 <xref:System.Data.SqlClient.SqlDataAdapter> 來編輯或刪除資料，請務必不要在預存程序定義中使用 SET NOCOUNT ON。  因為這樣會讓傳回的受影響資料列計數成為零，而 `DataAdapter` 會將它解譯為並行衝突。  在此事件中，系統會擲回 <xref:System.Data.DBConcurrencyException>。  
  
## 範例  
 此範例使用下列的預存程序將新類別插入至 **Northwind** 的 **Categories** 資料表。  此預存程序使用 **CategoryName** 資料行中的值做為輸入參數，然後使用 SCOPE\_IDENTITY\(\) 函式來擷取識別欄位 **CategoryID** 的新值，並以輸出參數加以傳回。  RETURN 陳述式使用 @@ROWCOUNT 函式傳回插入的資料列數。  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 下列程式碼範例使用以上所示的 `InsertCategory` 預存程序做為 <xref:System.Data.SqlClient.SqlDataAdapter> 的 <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 的來源。  在呼叫 <xref:System.Data.SqlClient.SqlDataAdapter> 的 `Update` 方法而將記錄插入至資料庫之後，`@Identity` 輸出參數將反映在 <xref:System.Data.DataSet> 中。  程式碼也會擷取傳回值。  
  
> [!NOTE]
>  使用 <xref:System.Data.OleDb.OleDbDataAdapter> 時，必須在其他參數前指定 <xref:System.Data.ParameterDirection> 為 **ReturnValue** 的參數。  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## 請參閱  
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [執行命令](../../../../docs/framework/data/adonet/executing-a-command.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)