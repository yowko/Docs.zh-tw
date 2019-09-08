---
title: 傳回兩個序列之間的集合差異
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 92513ed33e2afb785edbdd462ba7bc14923aa6b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781152"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="014c2-102">傳回兩個序列之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="014c2-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="014c2-103">使用 <xref:System.Linq.Queryable.Except%2A> 運算子傳回兩個序列之間的集合差異。</span><span class="sxs-lookup"><span data-stu-id="014c2-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="014c2-104">範例</span><span class="sxs-lookup"><span data-stu-id="014c2-104">Example</span></span>  
 <span data-ttu-id="014c2-105">這個範例會<xref:System.Linq.Queryable.Except%2A>使用來傳回`Customers` live 但不存在`Employees`的所有國家/地區序列。</span><span class="sxs-lookup"><span data-stu-id="014c2-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="014c2-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Except%2A> 作業僅妥善定義於集合上。</span><span class="sxs-lookup"><span data-stu-id="014c2-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="014c2-107">尚未定義多重集 (Multiset) 的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="014c2-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014c2-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="014c2-108">See also</span></span>

- [<span data-ttu-id="014c2-109">查詢範例</span><span class="sxs-lookup"><span data-stu-id="014c2-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="014c2-110">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="014c2-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
