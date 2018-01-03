---
title: "將序列轉換為泛型 List"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4b1fa6895e015ab7123bf454aac435812e4a23da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="convert-a-sequence-to-a-generic-list"></a><span data-ttu-id="16185-102">將序列轉換為泛型 List</span><span class="sxs-lookup"><span data-stu-id="16185-102">Convert a Sequence to a Generic List</span></span>
<span data-ttu-id="16185-103">使用 <xref:System.Linq.Enumerable.ToList%2A> 從序列建立泛型清單。</span><span class="sxs-lookup"><span data-stu-id="16185-103">Use <xref:System.Linq.Enumerable.ToList%2A> to create a generic List from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16185-104">範例</span><span class="sxs-lookup"><span data-stu-id="16185-104">Example</span></span>  
 <span data-ttu-id="16185-105">下列範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 立即將查詢評估為泛型 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="16185-105">The following sample uses <xref:System.Linq.Enumerable.ToList%2A> to immediately evaluate a query into a generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="16185-106">請參閱</span><span class="sxs-lookup"><span data-stu-id="16185-106">See Also</span></span>  
 [<span data-ttu-id="16185-107">查詢範例</span><span class="sxs-lookup"><span data-stu-id="16185-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
