---
title: "HOW TO：傳回資料列集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：傳回資料列集
這個範例會從資料庫傳回資料列集 \(Rowset\)，並且包含用以篩選結果的輸入參數。  
  
 當您執行可傳回資料列集的預存程序 \(Stored Procedure\) 時，您會使用「*結果*」\(Result\) 類別來儲存從預存程序傳回的資料。  如需詳細資訊，請參閱[分析 LINQ to SQL 原始程式碼](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md)。  
  
## 範例  
 下列範例表示一個預存程序，該程序會傳回客戶資料列並使用輸入參數，以便只傳回將 "London" 列為客戶所在城市的那些資料列。  此範例假設了一個可列舉的 `CustomersByCityResult` 類別。  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## 請參閱  
 [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)   
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)