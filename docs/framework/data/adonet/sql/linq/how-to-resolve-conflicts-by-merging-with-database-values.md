---
title: 如何：藉由與資料庫值合併來解決衝突
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: a263afb7daceccecf7153c6e9bcfc68e10638c30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360985"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="8abce-102">如何：藉由與資料庫值合併來解決衝突</span><span class="sxs-lookup"><span data-stu-id="8abce-102">How to: Resolve Conflicts by Merging with Database Values</span></span>
<span data-ttu-id="8abce-103">若要先協調預期和實際資料庫值之間的差異再重新送出變更，可以使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 來合併資料庫值與目前用戶端成員值。</span><span class="sxs-lookup"><span data-stu-id="8abce-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="8abce-104">如需詳細資訊，請參閱[開放式並行存取： 概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8abce-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8abce-105">在所有情況下，擷取資料庫中更新過的資料會先重新整理用戶端上的資料錄。</span><span class="sxs-lookup"><span data-stu-id="8abce-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="8abce-106">這個動作可確保下一次嘗試更新時，不會在相同的並行存取檢查時失敗。</span><span class="sxs-lookup"><span data-stu-id="8abce-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8abce-107">範例</span><span class="sxs-lookup"><span data-stu-id="8abce-107">Example</span></span>  
 <span data-ttu-id="8abce-108">在這個案例下，當 User1 嘗試送出變更時，因為 User2 同時變更了 Assistant 和 Department 資料行，所以會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8abce-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="8abce-109">下表顯示這個情況。</span><span class="sxs-lookup"><span data-stu-id="8abce-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="8abce-110">Manager</span><span class="sxs-lookup"><span data-stu-id="8abce-110">Manager</span></span>|<span data-ttu-id="8abce-111">Assistant</span><span class="sxs-lookup"><span data-stu-id="8abce-111">Assistant</span></span>|<span data-ttu-id="8abce-112">Department</span><span class="sxs-lookup"><span data-stu-id="8abce-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="8abce-113">User1 和 User2 查詢時的原始資料庫狀態。</span><span class="sxs-lookup"><span data-stu-id="8abce-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="8abce-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="8abce-114">Alfreds</span></span>|<span data-ttu-id="8abce-115">Maria</span><span class="sxs-lookup"><span data-stu-id="8abce-115">Maria</span></span>|<span data-ttu-id="8abce-116">Sales</span><span class="sxs-lookup"><span data-stu-id="8abce-116">Sales</span></span>|  
|<span data-ttu-id="8abce-117">User1 準備送出這些變更。</span><span class="sxs-lookup"><span data-stu-id="8abce-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="8abce-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="8abce-118">Alfred</span></span>||<span data-ttu-id="8abce-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="8abce-119">Marketing</span></span>|  
|<span data-ttu-id="8abce-120">User2 已送出這些變更。</span><span class="sxs-lookup"><span data-stu-id="8abce-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="8abce-121">Mary</span><span class="sxs-lookup"><span data-stu-id="8abce-121">Mary</span></span>|<span data-ttu-id="8abce-122">服務</span><span class="sxs-lookup"><span data-stu-id="8abce-122">Service</span></span>|  
  
 <span data-ttu-id="8abce-123">User1 決定合併資料庫值與目前用戶端成員值，來解決這個衝突。</span><span class="sxs-lookup"><span data-stu-id="8abce-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="8abce-124">這樣只有在目前變更集也修改該值時，才會覆寫資料庫值。</span><span class="sxs-lookup"><span data-stu-id="8abce-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="8abce-125">User1 使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 解決衝突時，資料庫中的結果會如同下表：</span><span class="sxs-lookup"><span data-stu-id="8abce-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="8abce-126">Manager</span><span class="sxs-lookup"><span data-stu-id="8abce-126">Manager</span></span>|<span data-ttu-id="8abce-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="8abce-127">Assistant</span></span>|<span data-ttu-id="8abce-128">Department</span><span class="sxs-lookup"><span data-stu-id="8abce-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="8abce-129">解決衝突後的新狀態。</span><span class="sxs-lookup"><span data-stu-id="8abce-129">New state after conflict resolution.</span></span>|<span data-ttu-id="8abce-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="8abce-130">Alfred</span></span><br /><br /> <span data-ttu-id="8abce-131">(來自 User1)</span><span class="sxs-lookup"><span data-stu-id="8abce-131">(from User1)</span></span>|<span data-ttu-id="8abce-132">Mary</span><span class="sxs-lookup"><span data-stu-id="8abce-132">Mary</span></span><br /><br /> <span data-ttu-id="8abce-133">(來自 User2)</span><span class="sxs-lookup"><span data-stu-id="8abce-133">(from User2)</span></span>|<span data-ttu-id="8abce-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="8abce-134">Marketing</span></span><br /><br /> <span data-ttu-id="8abce-135">(來自 User1)</span><span class="sxs-lookup"><span data-stu-id="8abce-135">(from User1)</span></span>|  
  
 <span data-ttu-id="8abce-136">下列範例顯示如何合併資料庫值與目前用戶端成員值 (除非用戶端也變更該值)。</span><span class="sxs-lookup"><span data-stu-id="8abce-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="8abce-137">但不會對個別成員衝突進行任何檢查或自訂處理。</span><span class="sxs-lookup"><span data-stu-id="8abce-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8abce-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8abce-138">See Also</span></span>  
 [<span data-ttu-id="8abce-139">如何：藉由覆寫資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="8abce-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [<span data-ttu-id="8abce-140">如何：藉由保留資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="8abce-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [<span data-ttu-id="8abce-141">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="8abce-141">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
