---
title: 開始使用
description: 使用此範例程式碼，開始使用 LINQ to SQL 來使用 LINQ 技術來存取 SQL 資料庫，就如同存取記憶體中的集合一樣。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: a46c42e917bdab0d32ee594bbcd604ee9e3d26bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286413"
---
# <a name="getting-started"></a>開始使用
藉由使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ，您可以使用 LINQ 技術來存取 SQL 資料庫，就如同存取記憶體中的集合一樣。  
  
 例如，下列程式碼會建立 `nw` 物件來表示 `Northwind` 資料庫、目標是設定為 `Customers` 資料表、篩選來自 `Customers` 的 `London` 的資料列，以及選取 `CompanyName` 的字串進行擷取。  
  
 執行迴圈 (Loop) 時，會擷取 `CompanyName` 值的集合。  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>後續步驟  
 如需其他範例，包括插入和更新，請參閱[您可以如何使用 LINQ to SQL](what-you-can-do-with-linq-to-sql.md)。  
  
 接下來，請嘗試一些逐步解說和教學課程，以獲取使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的實務經驗。 請參閱[依逐步解說學習](learning-by-walkthroughs.md)。  
  
 最後， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 閱讀[使用 LINQ to SQL 的一般步驟](typical-steps-for-using-linq-to-sql.md)，瞭解如何開始著手您自己的專案。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL](index.md)
- [LINQ 簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ 簡介 (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
