---
title: 如何：關閉延後載入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 279317f10211271fad812068215b08a93e30fbdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358636"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="f9b3a-102">如何：關閉延後載入</span><span class="sxs-lookup"><span data-stu-id="f9b3a-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="f9b3a-103">您可以將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。</span><span class="sxs-lookup"><span data-stu-id="f9b3a-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="f9b3a-104">如需詳細資訊，請參閱[延後執行與立即載入](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="f9b3a-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9b3a-105">關閉物件追蹤時，也會隱含地關閉延後載入。</span><span class="sxs-lookup"><span data-stu-id="f9b3a-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="f9b3a-106">如需詳細資訊，請參閱[How to： 擷取資訊為唯讀](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)。</span><span class="sxs-lookup"><span data-stu-id="f9b3a-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b3a-107">範例</span><span class="sxs-lookup"><span data-stu-id="f9b3a-107">Example</span></span>  
 <span data-ttu-id="f9b3a-108">下列範例顯示如何將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。</span><span class="sxs-lookup"><span data-stu-id="f9b3a-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f9b3a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9b3a-109">See Also</span></span>  
 [<span data-ttu-id="f9b3a-110">查詢概念</span><span class="sxs-lookup"><span data-stu-id="f9b3a-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="f9b3a-111">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="f9b3a-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
