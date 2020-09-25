---
title: 傳回兩個序列之間的集合差異
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 49a8d22377ef1f7d0fde16880a82002754e1bbc4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200325"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="5529e-102">傳回兩個序列之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="5529e-102">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="5529e-103">使用 <xref:System.Linq.Queryable.Except%2A> 運算子傳回兩個序列之間的集合差異。</span><span class="sxs-lookup"><span data-stu-id="5529e-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5529e-104">範例</span><span class="sxs-lookup"><span data-stu-id="5529e-104">Example</span></span>  

 <span data-ttu-id="5529e-105">這個範例會使用 <xref:System.Linq.Queryable.Except%2A> 來傳回 `Customers` 即時但不存在的所有國家/地區的序列 `Employees` 。</span><span class="sxs-lookup"><span data-stu-id="5529e-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="5529e-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Except%2A> 作業僅妥善定義於集合上。</span><span class="sxs-lookup"><span data-stu-id="5529e-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="5529e-107">尚未定義多重集 (Multiset) 的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="5529e-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5529e-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5529e-108">See also</span></span>

- [<span data-ttu-id="5529e-109">查詢範例</span><span class="sxs-lookup"><span data-stu-id="5529e-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="5529e-110">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="5529e-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
