---
title: HOW TO：在 DataContext 層級篩選
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 343cffa9b1c034068e5abcc652e936f89ee6a992
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084579"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="f443f-102">HOW TO：在 DataContext 層級篩選</span><span class="sxs-lookup"><span data-stu-id="f443f-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="f443f-103">您可以在 `EntitySets` 層級篩選 `DataContext`。</span><span class="sxs-lookup"><span data-stu-id="f443f-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="f443f-104">這類篩選會套用至所有使用該 <xref:System.Data.Linq.DataContext> 執行個體的查詢。</span><span class="sxs-lookup"><span data-stu-id="f443f-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f443f-105">範例</span><span class="sxs-lookup"><span data-stu-id="f443f-105">Example</span></span>  
 <span data-ttu-id="f443f-106">在下列範例中，會使用 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> 以根據 `ShippedDate` 來篩選客戶的預先載入訂單。</span><span class="sxs-lookup"><span data-stu-id="f443f-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="f443f-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f443f-107">See also</span></span>

- [<span data-ttu-id="f443f-108">查詢概念</span><span class="sxs-lookup"><span data-stu-id="f443f-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
