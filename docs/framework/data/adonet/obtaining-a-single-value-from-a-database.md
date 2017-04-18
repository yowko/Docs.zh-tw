---
title: "從資料庫取得單一數值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 從資料庫取得單一數值
或許您需要以單一數值傳回資料庫資訊，而非以資料表或資料流的形式。  例如，您或許要傳回彙總函式 \(例如 COUNT\(\*\)、SUM\(Price\) 或 AVG\(Quantity\)\) 的結果。  **Command** 物件可讓您以 **ExecuteScalar** 方法傳回單一數值。  **ExecuteScalar** 方法會將結果集第一個資料列之第一資料行的值當做純量值傳回。  
  
 下列程式碼範例會使用 <xref:System.Data.SqlClient.SqlCommand>，在資料庫中插入新的值。  <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法是用來傳回所插入資料錄的識別資料行值。  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## 請參閱  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [執行命令](../../../../docs/framework/data/adonet/executing-a-command.md)   
 [DbConnection、DbCommand 和 DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)