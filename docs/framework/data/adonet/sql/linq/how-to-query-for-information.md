---
title: 作法：查詢資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166400"
---
# <a name="how-to-query-for-information"></a>作法：查詢資訊

中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的查詢使用的語法與 LINQ 中的查詢相同。 唯一的差別在於查詢中參考的物件 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會對應至資料庫中的元素。 如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。  
  
 LINQ 查詢的某些功能在應用程式中可能需要特別注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。 如需詳細資訊，請參閱 [查詢概念](query-concepts.md)。  
  
## <a name="example"></a>範例  

 下列查詢會要求來自倫敦 (London) 的客戶名單。 在這個範例中，`Customers` 是 Northwind 範例資料庫中的資料表。  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [建立物件模型](creating-the-object-model.md)
- [下載範例資料庫](downloading-sample-databases.md)
- [查詢資料庫](querying-the-database.md)
