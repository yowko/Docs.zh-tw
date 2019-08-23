---
title: 傳回序列的第一個項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 39cf9270b08fce64590fef418bb428c5a781b0e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963802"
---
# <a name="return-the-first-element-in-a-sequence"></a>傳回序列的第一個項目
使用 <xref:System.Linq.Enumerable.First%2A> 運算子傳回序列中的第一個項目。 使用 <xref:System.Linq.Enumerable.First%2A> 的查詢會立即執行。  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援 <xref:System.Linq.Enumerable.Last%2A> 運算子。  
  
## <a name="example"></a>範例  
 下列程式碼會尋找資料表中的第一個 `Shipper`：  
  
 如果您對 Northwind 範例資料庫執行這個查詢，則結果為：  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>範例  
 下列程式碼會尋找具有 `Customer` BONAP 的單一 `CustomerID`。  
  
 如果您對 Northwind 範例資料庫執行這個查詢，則結果為 `ID = BONAP, Contact = Laurence Lebihan`。  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
