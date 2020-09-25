---
title: 傳回兩個序列的集合交集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 421ec544345e41f910bf80c855a3a6b4de1c46a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200221"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="4fe26-102">傳回兩個序列的集合交集</span><span class="sxs-lookup"><span data-stu-id="4fe26-102">Return the Set Intersection of Two Sequences</span></span>

<span data-ttu-id="4fe26-103">使用 <xref:System.Linq.Queryable.Intersect%2A> 運算子可傳回兩個序列的集合交集。</span><span class="sxs-lookup"><span data-stu-id="4fe26-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe26-104">範例</span><span class="sxs-lookup"><span data-stu-id="4fe26-104">Example</span></span>  

 <span data-ttu-id="4fe26-105">這則範例會使用 <xref:System.Linq.Queryable.Intersect%2A> 來傳回所有國家/地區的序列，而這些國家/地區都是 `Customers` 和 `Employees` 現場。</span><span class="sxs-lookup"><span data-stu-id="4fe26-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="4fe26-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Intersect%2A> 作業僅妥善定義於集合上。</span><span class="sxs-lookup"><span data-stu-id="4fe26-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="4fe26-107">尚未定義多重集 (Multiset) 的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="4fe26-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe26-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe26-108">See also</span></span>

- [<span data-ttu-id="4fe26-109">查詢範例</span><span class="sxs-lookup"><span data-stu-id="4fe26-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="4fe26-110">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="4fe26-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
