---
title: HOW TO：藉由保留資料庫值來解決衝突
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: 8440ffe61e254403357970d771aea207a6eb6092
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230105"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="99c47-102">HOW TO：藉由保留資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="99c47-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="99c47-103">若要先協調預期和實際資料庫值之間的差異再重新送出變更，可以使用 <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> 將找到的值保留在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="99c47-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="99c47-104">這樣會覆寫物件模型 (Object Model) 中的目前值。</span><span class="sxs-lookup"><span data-stu-id="99c47-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="99c47-105">如需詳細資訊，請參閱[開放式並行存取：概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="99c47-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99c47-106">在所有情況下，擷取資料庫中更新過的資料會先重新整理用戶端上的資料錄。</span><span class="sxs-lookup"><span data-stu-id="99c47-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="99c47-107">這個動作可確保下一次嘗試更新時，不會在相同的並行存取檢查時失敗。</span><span class="sxs-lookup"><span data-stu-id="99c47-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99c47-108">範例</span><span class="sxs-lookup"><span data-stu-id="99c47-108">Example</span></span>  
 <span data-ttu-id="99c47-109">在這個案例下，當 User1 嘗試送出變更時，因為 User2 同時變更了 Assistant 和 Department 資料行，所以會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99c47-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="99c47-110">下表顯示這個情況。</span><span class="sxs-lookup"><span data-stu-id="99c47-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="99c47-111">主管</span><span class="sxs-lookup"><span data-stu-id="99c47-111">Manager</span></span>|<span data-ttu-id="99c47-112">Assistant</span><span class="sxs-lookup"><span data-stu-id="99c47-112">Assistant</span></span>|<span data-ttu-id="99c47-113">部門</span><span class="sxs-lookup"><span data-stu-id="99c47-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="99c47-114">User1 和 User2 查詢時的原始資料庫狀態。</span><span class="sxs-lookup"><span data-stu-id="99c47-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="99c47-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="99c47-115">Alfreds</span></span>|<span data-ttu-id="99c47-116">Maria</span><span class="sxs-lookup"><span data-stu-id="99c47-116">Maria</span></span>|<span data-ttu-id="99c47-117">Sales</span><span class="sxs-lookup"><span data-stu-id="99c47-117">Sales</span></span>|  
|<span data-ttu-id="99c47-118">User1 準備送出這些變更。</span><span class="sxs-lookup"><span data-stu-id="99c47-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="99c47-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="99c47-119">Alfred</span></span>||<span data-ttu-id="99c47-120">行銷</span><span class="sxs-lookup"><span data-stu-id="99c47-120">Marketing</span></span>|  
|<span data-ttu-id="99c47-121">User2 已送出這些變更。</span><span class="sxs-lookup"><span data-stu-id="99c47-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="99c47-122">Mary</span><span class="sxs-lookup"><span data-stu-id="99c47-122">Mary</span></span>|<span data-ttu-id="99c47-123">服務</span><span class="sxs-lookup"><span data-stu-id="99c47-123">Service</span></span>|  
  
 <span data-ttu-id="99c47-124">User1 決定讓較新的資料庫值覆寫物件模型中的目前值，來解決這個衝突。</span><span class="sxs-lookup"><span data-stu-id="99c47-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="99c47-125">User1 使用 <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> 解決衝突時，資料庫中的結果會如同下表：</span><span class="sxs-lookup"><span data-stu-id="99c47-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="99c47-126">主管</span><span class="sxs-lookup"><span data-stu-id="99c47-126">Manager</span></span>|<span data-ttu-id="99c47-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="99c47-127">Assistant</span></span>|<span data-ttu-id="99c47-128">部門</span><span class="sxs-lookup"><span data-stu-id="99c47-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="99c47-129">解決衝突後的新狀態。</span><span class="sxs-lookup"><span data-stu-id="99c47-129">New state after conflict resolution.</span></span>|<span data-ttu-id="99c47-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="99c47-130">Alfreds</span></span><br /><br /> <span data-ttu-id="99c47-131">(原始)</span><span class="sxs-lookup"><span data-stu-id="99c47-131">(original)</span></span>|<span data-ttu-id="99c47-132">Mary</span><span class="sxs-lookup"><span data-stu-id="99c47-132">Mary</span></span><br /><br /> <span data-ttu-id="99c47-133">(來自 User2)</span><span class="sxs-lookup"><span data-stu-id="99c47-133">(from User2)</span></span>|<span data-ttu-id="99c47-134">服務</span><span class="sxs-lookup"><span data-stu-id="99c47-134">Service</span></span><br /><br /> <span data-ttu-id="99c47-135">(來自 User2)</span><span class="sxs-lookup"><span data-stu-id="99c47-135">(from User2)</span></span>|  
  
 <span data-ttu-id="99c47-136">下列範例程式碼顯示如何使用資料庫值來覆寫物件模型中的目前值 </span><span class="sxs-lookup"><span data-stu-id="99c47-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="99c47-137">(但不會對個別成員衝突進行任何檢查或自訂處理)。</span><span class="sxs-lookup"><span data-stu-id="99c47-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="99c47-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99c47-138">See also</span></span>

- [<span data-ttu-id="99c47-139">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="99c47-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
