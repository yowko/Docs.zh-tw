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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d5f24d7415ff7ecceba6b0a5fbd3098d70dcd0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796015"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="9109b-102">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="9109b-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="9109b-103">描述的作業主機可以套用原則的動作集合。</span><span class="sxs-lookup"><span data-stu-id="9109b-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9109b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9109b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="9109b-105">成員</span><span class="sxs-lookup"><span data-stu-id="9109b-105">Members</span></span>  
  
|<span data-ttu-id="9109b-106">成員</span><span class="sxs-lookup"><span data-stu-id="9109b-106">Member</span></span>|<span data-ttu-id="9109b-107">描述</span><span class="sxs-lookup"><span data-stu-id="9109b-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="9109b-108">主機可以指定應執行時的原則動作<xref:System.AppDomain>卸載非依正常程序 （粗略） 的方式。</span><span class="sxs-lookup"><span data-stu-id="9109b-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="9109b-109">主機可以指定應執行時的原則動作<xref:System.AppDomain>卸載。</span><span class="sxs-lookup"><span data-stu-id="9109b-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="9109b-110">主機可以指定原則完成項執行時所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9109b-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="9109b-111">主機可以指定原則的處理序結束時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9109b-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="9109b-112">主機可以指定原則會在中止執行緒時所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9109b-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="9109b-113">主機可以指定原則在關鍵區域的程式碼中執行緒粗暴中止時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9109b-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="9109b-114">主機可以指定原則才會發生非關鍵的程式碼區域中的執行緒粗暴中止時的動作。</span><span class="sxs-lookup"><span data-stu-id="9109b-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9109b-115">備註</span><span class="sxs-lookup"><span data-stu-id="9109b-115">Remarks</span></span>  
 <span data-ttu-id="9109b-116">Common language runtime (CLR) 可靠性 infrastructure 區分中止和資源配置失敗的程式碼和發生非關鍵區域中的程式碼的關鍵區域中發生。</span><span class="sxs-lookup"><span data-stu-id="9109b-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="9109b-117">這項區別被設計來讓主機以設定不同的原則，根據程式碼中發生失敗。</span><span class="sxs-lookup"><span data-stu-id="9109b-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="9109b-118">A*的程式碼的重要區域*該中止工作或無法完成要求的資源將會影響目前的工作，CLR 中不能保證任何空間。</span><span class="sxs-lookup"><span data-stu-id="9109b-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="9109b-119">例如，如果工作會保留鎖定，並收到指出時進行記憶體配置要求失敗的 HRESULT，它不足，只是中止該工作，以確保穩定性<xref:System.AppDomain>，因為<xref:System.AppDomain>可能包含其他相同的鎖定所等候的工作。</span><span class="sxs-lookup"><span data-stu-id="9109b-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="9109b-120">要放棄目前的工作可能會使這些其他工作，來停止回應 （或停止回應） 無限期。</span><span class="sxs-lookup"><span data-stu-id="9109b-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="9109b-121">在此情況下，主機必須能夠卸載整個<xref:System.AppDomain>而不是風險潛在的不穩定。</span><span class="sxs-lookup"><span data-stu-id="9109b-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="9109b-122">A*非關鍵的程式碼區域*，相反地，是 CLR 可以保證 「 中止 」 或 「 失敗會影響只有工作時就會發生錯誤的區域。</span><span class="sxs-lookup"><span data-stu-id="9109b-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="9109b-123">CLR 也會區分非失誤性和非依正常程序 （粗略） 中止。</span><span class="sxs-lookup"><span data-stu-id="9109b-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="9109b-124">一般情況下，正常的中止會盡全力之前中止工作，而粗暴中止不提供任何這類保證執行例外狀況處理常式和完成項。</span><span class="sxs-lookup"><span data-stu-id="9109b-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9109b-125">需求</span><span class="sxs-lookup"><span data-stu-id="9109b-125">Requirements</span></span>  
 <span data-ttu-id="9109b-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9109b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9109b-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9109b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9109b-128">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9109b-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9109b-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9109b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9109b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9109b-130">See also</span></span>

- [<span data-ttu-id="9109b-131">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="9109b-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="9109b-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="9109b-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="9109b-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="9109b-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="9109b-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="9109b-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="9109b-135">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="9109b-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
