---
title: 串連兩個序列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: c0a6dde667c4f858d8177dc80a726619f463f3a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354049"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="15803-102">串連兩個序列</span><span class="sxs-lookup"><span data-stu-id="15803-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="15803-103">使用 <xref:System.Linq.Queryable.Concat%2A> 運算子可串連兩個序列。</span><span class="sxs-lookup"><span data-stu-id="15803-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="15803-104"><xref:System.Linq.Queryable.Concat%2A> 運算子是針對已排序的多重集 (Multiset) 所定義，其中接收者和引數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="15803-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="15803-105">產生結果前的最後一個步驟就是在 SQL 中進行排序。</span><span class="sxs-lookup"><span data-stu-id="15803-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="15803-106">基於這個理由，會使用 <xref:System.Linq.Queryable.Concat%2A> 實作 `UNION ALL` 運算子，但不保留其引數的順序。</span><span class="sxs-lookup"><span data-stu-id="15803-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="15803-107">若要確保結果的排序正確無誤，請務必明確地將結果排序。</span><span class="sxs-lookup"><span data-stu-id="15803-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15803-108">範例</span><span class="sxs-lookup"><span data-stu-id="15803-108">Example</span></span>  
 <span data-ttu-id="15803-109">這個範例會使用 <xref:System.Linq.Queryable.Concat%2A> 傳回所有 `Customer` 和 `Employee` 電話及傳真號碼的序列。</span><span class="sxs-lookup"><span data-stu-id="15803-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="15803-110">範例</span><span class="sxs-lookup"><span data-stu-id="15803-110">Example</span></span>  
 <span data-ttu-id="15803-111">這個範例會使用 <xref:System.Linq.Queryable.Concat%2A> 傳回所有 `Customer` 和 `Employee` 姓名及電話號碼對應的序列。</span><span class="sxs-lookup"><span data-stu-id="15803-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="15803-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15803-112">See Also</span></span>  
 [<span data-ttu-id="15803-113">查詢範例</span><span class="sxs-lookup"><span data-stu-id="15803-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="15803-114">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="15803-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
