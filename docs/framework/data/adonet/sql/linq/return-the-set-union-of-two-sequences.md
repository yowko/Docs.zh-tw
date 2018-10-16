---
title: 傳回兩個序列的集合聯集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: c7d7a267df13cfa54d682ab9b65953f2c0a85a27
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347542"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="b6824-102">傳回兩個序列的集合聯集</span><span class="sxs-lookup"><span data-stu-id="b6824-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="b6824-103">使用 <xref:System.Linq.Queryable.Union%2A> 運算子傳回兩個序列的集合聯集。</span><span class="sxs-lookup"><span data-stu-id="b6824-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6824-104">範例</span><span class="sxs-lookup"><span data-stu-id="b6824-104">Example</span></span>  
 <span data-ttu-id="b6824-105">這個範例會使用 <xref:System.Linq.Queryable.Union%2A> 傳回 `Customers` 或 `Employees` 所在的所有國家/地區序列。</span><span class="sxs-lookup"><span data-stu-id="b6824-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="b6824-106">在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，則<xref:System.Linq.Queryable.Union%2A>運算子指 （semantics） 的未排序串連 (有效的結果[ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) SQL 中的子句)。</span><span class="sxs-lookup"><span data-stu-id="b6824-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6824-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6824-107">See Also</span></span>  
 [<span data-ttu-id="b6824-108">查詢範例</span><span class="sxs-lookup"><span data-stu-id="b6824-108">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="b6824-109">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="b6824-109">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
