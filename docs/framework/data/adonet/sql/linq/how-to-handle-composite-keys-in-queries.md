---
title: 如何：在查詢中處理複合索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 26c281445b84d3b3f85980de6ae4076411bb4fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354235"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="4ea5e-102">如何：在查詢中處理複合索引鍵</span><span class="sxs-lookup"><span data-stu-id="4ea5e-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="4ea5e-103">有些運算子只能取用一個引數。</span><span class="sxs-lookup"><span data-stu-id="4ea5e-103">Some operators can take only one argument.</span></span> <span data-ttu-id="4ea5e-104">如果引數必須包括資料庫中的多個資料行，則必須建立匿名型別來表示此項組合。</span><span class="sxs-lookup"><span data-stu-id="4ea5e-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea5e-105">範例</span><span class="sxs-lookup"><span data-stu-id="4ea5e-105">Example</span></span>  
 <span data-ttu-id="4ea5e-106">下列範例顯示叫用 (Invoke) `GroupBy` 運算子的查詢，這個運算子只可以取用一個 `key` 引數。</span><span class="sxs-lookup"><span data-stu-id="4ea5e-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="4ea5e-107">範例</span><span class="sxs-lookup"><span data-stu-id="4ea5e-107">Example</span></span>  
 <span data-ttu-id="4ea5e-108">聯結 (Join) 的情況也相同，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4ea5e-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4ea5e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ea5e-109">See Also</span></span>  
 [<span data-ttu-id="4ea5e-110">查詢概念</span><span class="sxs-lookup"><span data-stu-id="4ea5e-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
