---
title: 傳回兩個序列的集合聯集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 058856243b2a8daaecd653a9b5999013de5407a8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182520"
---
# <a name="return-the-set-union-of-two-sequences"></a>傳回兩個序列的集合聯集
使用 <xref:System.Linq.Queryable.Union%2A> 運算子傳回兩個序列的集合聯集。  
  
## <a name="example"></a>範例  
 這個範例<xref:System.Linq.Queryable.Union%2A> `Employees`會使用來傳回所有國家/地區的序列，其中其中有或。`Customers`  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中[，會`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql)將多重集的運算子定義為多重集的未排序串連（實際上是SQL中的子句結果）。<xref:System.Linq.Queryable.Union%2A>

如需詳細資訊和範例， <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>請參閱。
  
## <a name="see-also"></a>另請參閱

- [查詢範例](query-examples.md)
- [標準查詢運算子轉譯](standard-query-operator-translation.md)
