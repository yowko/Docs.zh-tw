---
title: 作法：在查詢中處理複合索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: bc16dde89f67572b03102b1c091993ed163b443c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203523"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="237a8-102">作法：在查詢中處理複合索引鍵</span><span class="sxs-lookup"><span data-stu-id="237a8-102">How to: Handle Composite Keys in Queries</span></span>

<span data-ttu-id="237a8-103">有些運算子只能取用一個引數。</span><span class="sxs-lookup"><span data-stu-id="237a8-103">Some operators can take only one argument.</span></span> <span data-ttu-id="237a8-104">如果引數必須包括資料庫中的多個資料行，則必須建立匿名型別來表示此項組合。</span><span class="sxs-lookup"><span data-stu-id="237a8-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="237a8-105">範例</span><span class="sxs-lookup"><span data-stu-id="237a8-105">Example</span></span>  

 <span data-ttu-id="237a8-106">下列範例顯示叫用 (Invoke) `GroupBy` 運算子的查詢，這個運算子只可以取用一個 `key` 引數。</span><span class="sxs-lookup"><span data-stu-id="237a8-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="237a8-107">範例</span><span class="sxs-lookup"><span data-stu-id="237a8-107">Example</span></span>  

 <span data-ttu-id="237a8-108">聯結 (Join) 的情況也相同，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="237a8-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="237a8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="237a8-109">See also</span></span>

- [<span data-ttu-id="237a8-110">查詢概念</span><span class="sxs-lookup"><span data-stu-id="237a8-110">Query Concepts</span></span>](query-concepts.md)
