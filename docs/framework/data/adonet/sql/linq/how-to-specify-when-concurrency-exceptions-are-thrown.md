---
title: HOW TO：指定並行例外狀況的擲回時機
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 30dd83c68472ecd3244cfc87b6df97b948b9a84f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182984"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="d17f2-102">HOW TO：指定並行例外狀況的擲回時機</span><span class="sxs-lookup"><span data-stu-id="d17f2-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="d17f2-103">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，因為開放式並行存取 (Optimistic Concurrency) 衝突而未更新物件時，會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="d17f2-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="d17f2-104">如需詳細資訊，請參閱[開放式並行存取：概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d17f2-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="d17f2-105">將變更提交至資料庫之前，您可以指定何時應擲出並行例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d17f2-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="d17f2-106">在第一次失敗時擲出例外狀況 (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>)。</span><span class="sxs-lookup"><span data-stu-id="d17f2-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="d17f2-107">完成所有更新嘗試、累積所有失敗，並且在例外狀況中報告所累積的失敗 (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>)。</span><span class="sxs-lookup"><span data-stu-id="d17f2-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="d17f2-108">擲出後，<xref:System.Data.Linq.ChangeConflictException> 例外狀況會提供 <xref:System.Data.Linq.ChangeConflictCollection> 集合的存取權。</span><span class="sxs-lookup"><span data-stu-id="d17f2-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="d17f2-109">此集合會提供每個衝突的詳細資訊 (對應至失敗的單一更新嘗試)，其中包含 <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> 集合的存取權。</span><span class="sxs-lookup"><span data-stu-id="d17f2-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="d17f2-110">每個成員衝突都會對應至未通過並行存取檢查之更新中的單一成員。</span><span class="sxs-lookup"><span data-stu-id="d17f2-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d17f2-111">範例</span><span class="sxs-lookup"><span data-stu-id="d17f2-111">Example</span></span>  
 <span data-ttu-id="d17f2-112">下列程式碼會顯示有兩個值的範例。</span><span class="sxs-lookup"><span data-stu-id="d17f2-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d17f2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d17f2-113">See also</span></span>

- [<span data-ttu-id="d17f2-114">HOW TO：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="d17f2-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="d17f2-115">變更資料和提交</span><span class="sxs-lookup"><span data-stu-id="d17f2-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
