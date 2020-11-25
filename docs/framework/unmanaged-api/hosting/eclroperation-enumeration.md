---
title: EClrOperation 列舉
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: c24e4557695d26666682ee385131abaab707a24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720707"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="94736-102">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="94736-102">EClrOperation Enumeration</span></span>

<span data-ttu-id="94736-103">描述主機可以套用原則動作的作業集合。</span><span class="sxs-lookup"><span data-stu-id="94736-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94736-104">語法</span><span class="sxs-lookup"><span data-stu-id="94736-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="94736-105">成員</span><span class="sxs-lookup"><span data-stu-id="94736-105">Members</span></span>  
  
|<span data-ttu-id="94736-106">member</span><span class="sxs-lookup"><span data-stu-id="94736-106">Member</span></span>|<span data-ttu-id="94736-107">描述</span><span class="sxs-lookup"><span data-stu-id="94736-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="94736-108">當 <xref:System.AppDomain> 以非正常的 (的) 方式卸載時，主機可以指定要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="94736-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="94736-109">主機可以指定卸載時要採取的原則動作 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="94736-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="94736-110">主機可以指定完成項執行時要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="94736-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="94736-111">主機可以指定進程結束時要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="94736-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="94736-112">主機可以指定當執行緒中止時要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="94736-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="94736-113">主機可以指定在程式碼的關鍵區域中發生強制執行緒中止時，所要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="94736-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="94736-114">當在非關鍵性的程式碼區域中發生強制執行緒中止時，主機可以指定要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="94736-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94736-115">備註</span><span class="sxs-lookup"><span data-stu-id="94736-115">Remarks</span></span>  

 <span data-ttu-id="94736-116">Common language runtime (CLR) 可靠性基礎結構可區分在程式碼的重要區域中發生的中止和資源配置失敗，以及在非關鍵性的程式碼區域中發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="94736-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="94736-117">這項區別的設計目的是要讓主機根據程式碼中發生失敗的位置來設定不同的原則。</span><span class="sxs-lookup"><span data-stu-id="94736-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="94736-118">程式 *代碼的關鍵區域* 是 CLR 無法保證中止工作或無法完成資源要求的任何空間，只會影響目前的工作。</span><span class="sxs-lookup"><span data-stu-id="94736-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="94736-119">例如，如果工作正在持有鎖定，並收到表示在進行記憶體配置要求時失敗的 HRESULT，則只是要中止該工作以確保的穩定性， <xref:System.AppDomain> 因為 <xref:System.AppDomain> 可能包含其他等候相同鎖定的工作。</span><span class="sxs-lookup"><span data-stu-id="94736-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="94736-120">若要放棄目前的工作，可能會導致這些其他工作停止回應。</span><span class="sxs-lookup"><span data-stu-id="94736-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="94736-121">在這種情況下，主機必須能夠卸載整個， <xref:System.AppDomain> 而不是風險潛在的不穩定。</span><span class="sxs-lookup"><span data-stu-id="94736-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="94736-122">另一方面， *非關鍵性的程式碼區域* 是一個區域，CLR 可以保證中止或失敗只會影響發生錯誤的工作。</span><span class="sxs-lookup"><span data-stu-id="94736-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="94736-123">CLR 也會區分正常和非正常的 () 中止。</span><span class="sxs-lookup"><span data-stu-id="94736-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="94736-124">一般來說，正常或無錯誤的中止會讓每個工作在中止工作之前執行例外狀況處理常式和完成項，而強制性中止則不會造成這類保證。</span><span class="sxs-lookup"><span data-stu-id="94736-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94736-125">需求</span><span class="sxs-lookup"><span data-stu-id="94736-125">Requirements</span></span>  

 <span data-ttu-id="94736-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94736-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94736-127">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="94736-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94736-128">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94736-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94736-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94736-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94736-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94736-130">See also</span></span>

- [<span data-ttu-id="94736-131">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="94736-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="94736-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="94736-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="94736-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="94736-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="94736-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="94736-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="94736-135">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="94736-135">Hosting Enumerations</span></span>](hosting-enumerations.md)
