---
title: "快速入門"
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
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6cea3468732367a7c179528601327f0110c0e38c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="getting-started"></a>快速入門
使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您可以使用[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]技術來存取 SQL 資料庫，就如同存取記憶體中的集合。  
  
 例如，下列程式碼會建立 `nw` 物件來表示 `Northwind` 資料庫、目標是設定為 `Customers` 資料表、篩選來自 `Customers` 的 `London` 的資料列，以及選取 `CompanyName` 的字串進行擷取。  
  
 執行迴圈 (Loop) 時，會擷取 `CompanyName` 值的集合。  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>後續步驟  
 如插入及更新，包括一些其他範例，請參閱[什麼您可以不要使用 LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md)。  
  
 接下來，請嘗試一些逐步解說和教學課程，以獲取使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的實務經驗。 請參閱[依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。  
  
 最後，了解如何開始使用您自己[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]專案藉由讀取[使用 LINQ to SQL 的一般步驟](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)。  
  
## <a name="see-also"></a>請參閱  
 [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ 簡介](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
