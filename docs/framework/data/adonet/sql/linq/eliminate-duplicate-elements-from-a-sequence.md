---
title: 從序列排除重複項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 49138e9b130b1a2137b5e9e779875d6107972578
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211526"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a><span data-ttu-id="9cbdb-102">從序列排除重複項目</span><span class="sxs-lookup"><span data-stu-id="9cbdb-102">Eliminate Duplicate Elements from a Sequence</span></span>
<span data-ttu-id="9cbdb-103">使用 <xref:System.Linq.Queryable.Distinct%2A> 運算子去除序列中重複的項目。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-103">Use the <xref:System.Linq.Queryable.Distinct%2A> operator to eliminate duplicate elements from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cbdb-104">範例</span><span class="sxs-lookup"><span data-stu-id="9cbdb-104">Example</span></span>  
 <span data-ttu-id="9cbdb-105">下列範例使用 <xref:System.Linq.Queryable.Distinct%2A> 來選取一連串具有客戶的唯一城市。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-105">The following example uses <xref:System.Linq.Queryable.Distinct%2A> to select a sequence of the unique cities that have customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a><span data-ttu-id="9cbdb-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cbdb-106">See also</span></span>

- [<span data-ttu-id="9cbdb-107">查詢範例</span><span class="sxs-lookup"><span data-stu-id="9cbdb-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
