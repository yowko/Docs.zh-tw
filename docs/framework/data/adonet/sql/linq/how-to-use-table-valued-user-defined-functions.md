---
title: "HOW TO：使用資料表值使用者定義函式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：使用資料表值使用者定義函式
資料表值函式會傳回單一資料列集 \(Rowset\)，而不像預存程序 \(Stored Procedure\) 會傳回多個結果圖案。  因為資料表值函式的傳回型別為 `Table`，所以在可使用資料表的 SQL 中，您可以在任意處使用資料表值函式。  您也可以如同處理資料表一樣來處理資料表值函式。  
  
## 範例  
 下列 SQL 函式明確地指出它傳回 `TABLE`。  因此，會以隱含的方式定義傳回的資料列集結構。  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會依照下列方式對應函式：  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## 範例  
 下列 SQL 程式碼顯示您可以聯結 \(Join\) 至函式所傳回的資料表，否則就如同處理其他資料表一樣地處理該資料表：  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，查詢會依照下列方式轉譯：  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## 請參閱  
 [使用者定義函式](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)