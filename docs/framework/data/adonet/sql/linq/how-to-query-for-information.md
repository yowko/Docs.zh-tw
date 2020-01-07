---
title: 如何：查詢資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 3380b486da33a5dc083ed51f6705e666978df197
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634647"
---
# <a name="how-to-query-for-information"></a>如何：查詢資訊
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的查詢使用與 LINQ 中的查詢相同的語法。 唯一的差別在於 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢中參考的物件會對應至資料庫中的元素。 如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您撰寫的查詢轉譯為對等 SQL 查詢，並將它們傳送給伺服器進行處理。  
  
 LINQ 查詢的某些功能在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中可能需要特別注意。 如需詳細資訊，請參閱[查詢概念](query-concepts.md)。  
  
## <a name="example"></a>範例  
 下列查詢會要求來自倫敦 (London) 的客戶名單。 在這個範例中，`Customers` 是 Northwind 範例資料庫中的資料表。  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>請參閱

- [建立物件模型](creating-the-object-model.md)
- [下載範例資料庫](downloading-sample-databases.md)
- [查詢資料庫](querying-the-database.md)
