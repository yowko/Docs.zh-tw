---
title: 將序列轉換為泛型 List
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
ms.openlocfilehash: 326b4360323f306d07a3b47df506c6427a980a32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630784"
---
# <a name="convert-a-sequence-to-a-generic-list"></a><span data-ttu-id="c6e5f-102">將序列轉換為泛型 List</span><span class="sxs-lookup"><span data-stu-id="c6e5f-102">Convert a Sequence to a Generic List</span></span>
<span data-ttu-id="c6e5f-103">使用 <xref:System.Linq.Enumerable.ToList%2A> 從序列建立泛型清單。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-103">Use <xref:System.Linq.Enumerable.ToList%2A> to create a generic List from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6e5f-104">範例</span><span class="sxs-lookup"><span data-stu-id="c6e5f-104">Example</span></span>  
 <span data-ttu-id="c6e5f-105">下列範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 立即將查詢評估為泛型 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-105">The following sample uses <xref:System.Linq.Enumerable.ToList%2A> to immediately evaluate a query into a generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="c6e5f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6e5f-106">See also</span></span>
- [<span data-ttu-id="c6e5f-107">查詢範例</span><span class="sxs-lookup"><span data-stu-id="c6e5f-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
