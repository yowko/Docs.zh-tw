---
title: 作法：關閉延後載入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: b2193e7e8bda396451274d2da96e7cb86774fd03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196958"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="61554-102">作法：關閉延後載入</span><span class="sxs-lookup"><span data-stu-id="61554-102">How to: Turn Off Deferred Loading</span></span>

<span data-ttu-id="61554-103">您可以將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。</span><span class="sxs-lookup"><span data-stu-id="61554-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="61554-104">如需詳細資訊，請參閱 [延後和立即載入](deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="61554-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61554-105">關閉物件追蹤時，也會隱含地關閉延後載入。</span><span class="sxs-lookup"><span data-stu-id="61554-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="61554-106">如需詳細資訊，請參閱 [如何：以唯讀形式取出資訊](how-to-retrieve-information-as-read-only.md)。</span><span class="sxs-lookup"><span data-stu-id="61554-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61554-107">範例</span><span class="sxs-lookup"><span data-stu-id="61554-107">Example</span></span>  

 <span data-ttu-id="61554-108">下列範例顯示如何將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。</span><span class="sxs-lookup"><span data-stu-id="61554-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="61554-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61554-109">See also</span></span>

- [<span data-ttu-id="61554-110">查詢概念</span><span class="sxs-lookup"><span data-stu-id="61554-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="61554-111">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="61554-111">Querying the Database</span></span>](querying-the-database.md)
