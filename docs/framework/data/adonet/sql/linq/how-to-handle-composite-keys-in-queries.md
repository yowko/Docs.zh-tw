---
title: HOW TO：處理查詢中的複合索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 0ee0bda8c3ee46cb6e08ee415def68a4a9832617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523477"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="be1b6-102">HOW TO：處理查詢中的複合索引鍵</span><span class="sxs-lookup"><span data-stu-id="be1b6-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="be1b6-103">有些運算子只能取用一個引數。</span><span class="sxs-lookup"><span data-stu-id="be1b6-103">Some operators can take only one argument.</span></span> <span data-ttu-id="be1b6-104">如果引數必須包括資料庫中的多個資料行，則必須建立匿名型別來表示此項組合。</span><span class="sxs-lookup"><span data-stu-id="be1b6-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be1b6-105">範例</span><span class="sxs-lookup"><span data-stu-id="be1b6-105">Example</span></span>  
 <span data-ttu-id="be1b6-106">下列範例顯示叫用 (Invoke) `GroupBy` 運算子的查詢，這個運算子只可以取用一個 `key` 引數。</span><span class="sxs-lookup"><span data-stu-id="be1b6-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="be1b6-107">範例</span><span class="sxs-lookup"><span data-stu-id="be1b6-107">Example</span></span>  
 <span data-ttu-id="be1b6-108">聯結 (Join) 的情況也相同，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="be1b6-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="be1b6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be1b6-109">See also</span></span>
- [<span data-ttu-id="be1b6-110">查詢概念</span><span class="sxs-lookup"><span data-stu-id="be1b6-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
