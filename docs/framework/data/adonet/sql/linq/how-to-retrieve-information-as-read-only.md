---
title: 作法：以唯讀形式擷取資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 0a6853ef5d0b67e5efb95731adb5a106e8701e0f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155831"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="e3e66-102">作法：以唯讀形式擷取資訊</span><span class="sxs-lookup"><span data-stu-id="e3e66-102">How to: Retrieve Information As Read-Only</span></span>

<span data-ttu-id="e3e66-103">不想要變更資料時，可以搜尋唯讀結果以增加查詢效能。</span><span class="sxs-lookup"><span data-stu-id="e3e66-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="e3e66-104">將 <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 `false`，即可實作唯讀處理。</span><span class="sxs-lookup"><span data-stu-id="e3e66-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3e66-105"><xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 `false` 時，<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 會隱含地設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e3e66-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3e66-106">範例</span><span class="sxs-lookup"><span data-stu-id="e3e66-106">Example</span></span>  

 <span data-ttu-id="e3e66-107">下列程式碼會擷取員工雇用日期的唯讀集合。</span><span class="sxs-lookup"><span data-stu-id="e3e66-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e3e66-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3e66-108">See also</span></span>

- [<span data-ttu-id="e3e66-109">查詢概念</span><span class="sxs-lookup"><span data-stu-id="e3e66-109">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="e3e66-110">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="e3e66-110">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="e3e66-111">延後和立即載入的比較</span><span class="sxs-lookup"><span data-stu-id="e3e66-111">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
