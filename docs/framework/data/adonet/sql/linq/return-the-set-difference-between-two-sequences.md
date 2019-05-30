---
title: 傳回兩個序列之間的集合差異
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 5bb7d797ad2adc4374f7a10c11d66be69feeb7a1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380054"
---
# <a name="return-the-set-difference-between-two-sequences"></a>傳回兩個序列之間的集合差異
使用 <xref:System.Linq.Queryable.Except%2A> 運算子傳回兩個序列之間的集合差異。  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Linq.Queryable.Except%2A>以在其中傳回的所有國家/地區序列`Customers`即時但無`Employees`live。  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Except%2A> 作業僅妥善定義於集合上。 尚未定義多重集 (Multiset) 的語意 (Semantics)。  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
