---
title: 傳回兩個序列的集合交集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 9fd2a5dc435829d08594ea3c2f1c129328386250
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358780"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="5037f-102">傳回兩個序列的集合交集</span><span class="sxs-lookup"><span data-stu-id="5037f-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="5037f-103">使用 <xref:System.Linq.Queryable.Intersect%2A> 運算子可傳回兩個序列的集合交集。</span><span class="sxs-lookup"><span data-stu-id="5037f-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5037f-104">範例</span><span class="sxs-lookup"><span data-stu-id="5037f-104">Example</span></span>  
 <span data-ttu-id="5037f-105">這個範例使用 <xref:System.Linq.Queryable.Intersect%2A> 傳回同時有 `Customers` 和 `Employees` 居住的所有國家 (地區) 序列。</span><span class="sxs-lookup"><span data-stu-id="5037f-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="5037f-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Intersect%2A> 作業僅妥善定義於集合上。</span><span class="sxs-lookup"><span data-stu-id="5037f-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="5037f-107">尚未定義多重集 (Multiset) 的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="5037f-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5037f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5037f-108">See Also</span></span>  
 [<span data-ttu-id="5037f-109">查詢範例</span><span class="sxs-lookup"><span data-stu-id="5037f-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="5037f-110">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="5037f-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
