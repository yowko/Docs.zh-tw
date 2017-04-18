---
title: "HOW TO：以內嵌方式呼叫使用者定義函式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：以內嵌方式呼叫使用者定義函式
雖然您可以用內嵌 \(Inline\) 方式呼叫使用者定義的函式，但是在執行查詢之前，並不會執行已延後執行的查詢中所含的函式。  如需詳細資訊，請參閱[Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)。  
  
 在查詢外部呼叫相同的函式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會透過方法呼叫運算式來建立簡單的查詢。  下列是 SQL 語法 \(參數 `@p0` 會繫結至傳入的常數\)：  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會建立下列項目：  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## 範例  
 在下列 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢中，您可以看到所產生之使用者定義函式方法 `ReverseCustName` 的內嵌呼叫。  因為延後查詢執行，所以不會立即執行函式。  針對這個查詢建置的 SQL，會轉譯為對資料庫中使用者定義函式的呼叫 \(請參閱查詢後面的 SQL 程式碼\)。  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## 請參閱  
 [使用者定義函式](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)