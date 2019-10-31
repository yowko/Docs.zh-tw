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
ms.openlocfilehash: 6becc44b061ff2baac63437b6a72375d1c3735b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131154"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="6a45e-102">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="6a45e-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="6a45e-103">描述主機可以套用原則動作的一組作業。</span><span class="sxs-lookup"><span data-stu-id="6a45e-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a45e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a45e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6a45e-105">Members</span><span class="sxs-lookup"><span data-stu-id="6a45e-105">Members</span></span>  
  
|<span data-ttu-id="6a45e-106">成員</span><span class="sxs-lookup"><span data-stu-id="6a45e-106">Member</span></span>|<span data-ttu-id="6a45e-107">描述</span><span class="sxs-lookup"><span data-stu-id="6a45e-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="6a45e-108">當以非正常（強制）方式卸載 <xref:System.AppDomain> 時，主機可以指定要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="6a45e-109">主機可以指定卸載 <xref:System.AppDomain> 時要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="6a45e-110">主機可以指定在完成項執行時要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="6a45e-111">主機可以指定在進程結束時要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="6a45e-112">主機可以指定要線上程中止時採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="6a45e-113">主機可以指定在程式碼的重要區域中發生強制執行緒中止時，所要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="6a45e-114">主機可以指定在非關鍵的程式碼區域中發生強制執行緒中止時，所要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a45e-115">備註</span><span class="sxs-lookup"><span data-stu-id="6a45e-115">Remarks</span></span>  
 <span data-ttu-id="6a45e-116">通用語言執行平臺（CLR）可靠性基礎結構可區分在關鍵程式碼區域中發生的中止和資源配置失敗，以及在非關鍵的程式碼區域中發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a45e-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="6a45e-117">這項區別的設計，是為了讓主機根據程式碼中發生失敗的位置來設定不同的原則。</span><span class="sxs-lookup"><span data-stu-id="6a45e-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="6a45e-118">程式*代碼的關鍵區域*是 CLR 無法保證中止工作或無法完成資源要求的任何空間，將只會影響目前的工作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="6a45e-119">例如，如果工作持有鎖定，並收到表示在建立記憶體配置要求時失敗的 HRESULT，則只是要中止該工作以確保 <xref:System.AppDomain>的穩定性，因為 <xref:System.AppDomain> 可能包含其他工作正在等候相同的鎖定。</span><span class="sxs-lookup"><span data-stu-id="6a45e-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="6a45e-120">若要放棄目前的工作，可能會導致這些其他工作停止回應。</span><span class="sxs-lookup"><span data-stu-id="6a45e-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="6a45e-121">在這種情況下，主機必須能夠卸載整個 <xref:System.AppDomain>，而不是風險潛在的不穩定。</span><span class="sxs-lookup"><span data-stu-id="6a45e-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="6a45e-122">另一方面，程式*代碼的非關鍵區域*是一個區域，其中 CLR 可以保證中止或失敗只會影響發生錯誤的工作。</span><span class="sxs-lookup"><span data-stu-id="6a45e-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="6a45e-123">CLR 也可以區別正常和非正常（強制性）中止。</span><span class="sxs-lookup"><span data-stu-id="6a45e-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="6a45e-124">一般來說，正常或正常的中止會在中止工作之前，讓每個工作執行例外狀況處理常式和完成項，而強制中止則不會進行這類保證。</span><span class="sxs-lookup"><span data-stu-id="6a45e-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a45e-125">需求</span><span class="sxs-lookup"><span data-stu-id="6a45e-125">Requirements</span></span>  
 <span data-ttu-id="6a45e-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a45e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a45e-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6a45e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a45e-128">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="6a45e-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a45e-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a45e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a45e-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="6a45e-130">See also</span></span>

- [<span data-ttu-id="6a45e-131">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="6a45e-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="6a45e-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="6a45e-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="6a45e-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="6a45e-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="6a45e-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="6a45e-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="6a45e-135">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="6a45e-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
