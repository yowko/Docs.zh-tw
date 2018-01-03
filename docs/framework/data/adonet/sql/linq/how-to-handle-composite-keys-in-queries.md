---
title: "如何：在查詢中處理複合索引鍵"
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
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2b0954d4659d1cc39cead0658fbd21dcd6dd12e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="b3fc0-102">如何：在查詢中處理複合索引鍵</span><span class="sxs-lookup"><span data-stu-id="b3fc0-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="b3fc0-103">有些運算子只能取用一個引數。</span><span class="sxs-lookup"><span data-stu-id="b3fc0-103">Some operators can take only one argument.</span></span> <span data-ttu-id="b3fc0-104">如果引數必須包括資料庫中的多個資料行，則必須建立匿名型別來表示此項組合。</span><span class="sxs-lookup"><span data-stu-id="b3fc0-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3fc0-105">範例</span><span class="sxs-lookup"><span data-stu-id="b3fc0-105">Example</span></span>  
 <span data-ttu-id="b3fc0-106">下列範例顯示叫用 (Invoke) `GroupBy` 運算子的查詢，這個運算子只可以取用一個 `key` 引數。</span><span class="sxs-lookup"><span data-stu-id="b3fc0-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="b3fc0-107">範例</span><span class="sxs-lookup"><span data-stu-id="b3fc0-107">Example</span></span>  
 <span data-ttu-id="b3fc0-108">聯結 (Join) 的情況也相同，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b3fc0-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b3fc0-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3fc0-109">See Also</span></span>  
 [<span data-ttu-id="b3fc0-110">查詢概念</span><span class="sxs-lookup"><span data-stu-id="b3fc0-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
