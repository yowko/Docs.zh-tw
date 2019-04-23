---
title: 將序列轉換為泛型 List
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
ms.openlocfilehash: 2c83a744e26fabb6f3e6ddd0a31c7cdd0c7139a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140591"
---
# <a name="convert-a-sequence-to-a-generic-list"></a><span data-ttu-id="24a6f-102">將序列轉換為泛型 List</span><span class="sxs-lookup"><span data-stu-id="24a6f-102">Convert a Sequence to a Generic List</span></span>
<span data-ttu-id="24a6f-103">使用 <xref:System.Linq.Enumerable.ToList%2A> 從序列建立泛型清單。</span><span class="sxs-lookup"><span data-stu-id="24a6f-103">Use <xref:System.Linq.Enumerable.ToList%2A> to create a generic List from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24a6f-104">範例</span><span class="sxs-lookup"><span data-stu-id="24a6f-104">Example</span></span>  
 <span data-ttu-id="24a6f-105">下列範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 立即將查詢評估為泛型 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="24a6f-105">The following sample uses <xref:System.Linq.Enumerable.ToList%2A> to immediately evaluate a query into a generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="24a6f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24a6f-106">See also</span></span>

- [<span data-ttu-id="24a6f-107">查詢範例</span><span class="sxs-lookup"><span data-stu-id="24a6f-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
