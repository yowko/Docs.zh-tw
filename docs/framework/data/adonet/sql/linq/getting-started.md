---
title: "使用者入門 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 使用者入門
藉由使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您就可以使用 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 技術來存取 SQL 資料庫，就如同存取記憶體中的集合一樣。  
  
 例如，下列程式碼會建立 `nw` 物件來表示 `Northwind` 資料庫、目標是設定為 `Customers` 資料表、篩選來自 `London` 的 `Customers` 的資料列，以及選取 `CompanyName` 的字串進行擷取。  
  
 執行迴圈 \(Loop\) 時，會擷取 `CompanyName` 值的集合。  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## 後續步驟  
 如需某些其他範例 \(含插入和更新\)，請參閱 [LINQ to SQL 的功能](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md)。  
  
 接下來，請嘗試一些逐步解說和教學課程，以獲取使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的實務經驗。  請參閱 [從逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。  
  
 最後，閱讀[使用 LINQ to SQL 的一般步驟](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)，學習如何開始您自己的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案。  
  
## 請參閱  
 [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md)   
 [Introduction to LINQ](../../../../../../ocs/visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)