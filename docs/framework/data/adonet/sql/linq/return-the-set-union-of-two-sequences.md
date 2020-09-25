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
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="123ad-102">傳回兩個序列的集合聯集</span><span class="sxs-lookup"><span data-stu-id="123ad-102">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="123ad-103">使用 <xref:System.Linq.Queryable.Union%2A> 運算子傳回兩個序列的集合聯集。</span><span class="sxs-lookup"><span data-stu-id="123ad-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="123ad-104">範例</span><span class="sxs-lookup"><span data-stu-id="123ad-104">Example</span></span>  

 <span data-ttu-id="123ad-105">這個範例 <xref:System.Linq.Queryable.Union%2A> 會使用來傳回所有國家/地區的序列，其中有 `Customers` 或 `Employees` 。</span><span class="sxs-lookup"><span data-stu-id="123ad-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="123ad-106">在中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ， <xref:System.Linq.Queryable.Union%2A> 運算子是針對多重集的未排序串連而定義， (在 [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) SQL) 中有效的子句結果。</span><span class="sxs-lookup"><span data-stu-id="123ad-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="123ad-107">如需詳細資訊和範例，請參閱 <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="123ad-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="123ad-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="123ad-108">See also</span></span>

- [<span data-ttu-id="123ad-109">查詢範例</span><span class="sxs-lookup"><span data-stu-id="123ad-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="123ad-110">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="123ad-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
