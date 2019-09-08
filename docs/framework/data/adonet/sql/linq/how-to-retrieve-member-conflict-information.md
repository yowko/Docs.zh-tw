---
title: 作法：擷取成員衝突資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 40caa07488cb40ca8e9e3eb3a570c325b92de491
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793301"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="97063-102">作法：擷取成員衝突資訊</span><span class="sxs-lookup"><span data-stu-id="97063-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="97063-103">您可以使用 <xref:System.Data.Linq.MemberChangeConflict> 類別來擷取衝突中各個成員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="97063-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="97063-104">在此相同狀況下，您可以替任何成員做好自訂處理衝突的準備。</span><span class="sxs-lookup"><span data-stu-id="97063-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="97063-105">如需詳細資訊， [請參閱開放式平行存取：總覽](optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="97063-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97063-106">範例</span><span class="sxs-lookup"><span data-stu-id="97063-106">Example</span></span>  
 <span data-ttu-id="97063-107">下列程式碼會逐一查看 <xref:System.Data.Linq.ObjectChangeConflict> 物件。</span><span class="sxs-lookup"><span data-stu-id="97063-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="97063-108">對於每個物件，它會接著逐一查看 <xref:System.Data.Linq.MemberChangeConflict> 物件。</span><span class="sxs-lookup"><span data-stu-id="97063-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97063-109">納入 <xref:System.Reflection>，以便提供 <xref:System.Data.Linq.MemberChangeConflict.Member%2A> 資訊。</span><span class="sxs-lookup"><span data-stu-id="97063-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97063-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97063-110">See also</span></span>

- [<span data-ttu-id="97063-111">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="97063-111">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
