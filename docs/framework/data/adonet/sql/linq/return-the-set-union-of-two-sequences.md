---
title: 傳回兩個序列的集合聯集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 13e5e821f68e839039569b4ac8a993a20c45ab27
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403943"
---
# <a name="return-the-set-union-of-two-sequences"></a>傳回兩個序列的集合聯集
使用 <xref:System.Linq.Queryable.Union%2A> 運算子傳回兩個序列的集合聯集。  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Linq.Queryable.Union%2A> 傳回 `Customers` 或 `Employees` 所在的所有國家/地區序列。  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，則<xref:System.Linq.Queryable.Union%2A>運算子指 （semantics） 的未排序串連 (有效的結果[ `UNION ALL` ](https://docs.microsoft.com/en-us/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) SQL 中的子句)。  
  
## <a name="see-also"></a>另請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
