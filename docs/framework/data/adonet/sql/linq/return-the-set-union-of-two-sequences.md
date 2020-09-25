---
title: 傳回兩個序列的集合聯集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 0fe32d8c3c37e99a50ca03262dc6184337b4450e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200195"
---
# <a name="return-the-set-union-of-two-sequences"></a>傳回兩個序列的集合聯集

使用 <xref:System.Linq.Queryable.Union%2A> 運算子傳回兩個序列的集合聯集。  
  
## <a name="example"></a>範例  

 這個範例 <xref:System.Linq.Queryable.Union%2A> 會使用來傳回所有國家/地區的序列，其中有 `Customers` 或 `Employees` 。  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 在中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ， <xref:System.Linq.Queryable.Union%2A> 運算子是針對多重集的未排序串連而定義， (在 [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) SQL) 中有效的子句結果。

如需詳細資訊和範例，請參閱 <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> 。
  
## <a name="see-also"></a>另請參閱

- [查詢範例](query-examples.md)
- [標準查詢運算子轉譯](standard-query-operator-translation.md)
