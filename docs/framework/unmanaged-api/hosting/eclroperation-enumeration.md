---
title: "EClrOperation 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="a8c64-102">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="a8c64-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="a8c64-103">描述一組作業，主機可以套用原則的動作。</span><span class="sxs-lookup"><span data-stu-id="a8c64-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c64-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8c64-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a8c64-105">成員</span><span class="sxs-lookup"><span data-stu-id="a8c64-105">Members</span></span>  
  
|<span data-ttu-id="a8c64-106">成員</span><span class="sxs-lookup"><span data-stu-id="a8c64-106">Member</span></span>|<span data-ttu-id="a8c64-107">描述</span><span class="sxs-lookup"><span data-stu-id="a8c64-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="a8c64-108">主機可以指定時採取的動作原則<xref:System.AppDomain>卸載非正常程序 （粗略） 的方式。</span><span class="sxs-lookup"><span data-stu-id="a8c64-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="a8c64-109">主機可以指定時採取的動作原則<xref:System.AppDomain>卸載。</span><span class="sxs-lookup"><span data-stu-id="a8c64-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="a8c64-110">主機可以指定原則完成執行時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a8c64-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="a8c64-111">主機可以指定原則的處理序結束時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a8c64-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="a8c64-112">主機可以指定原則會在中止執行緒時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a8c64-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="a8c64-113">主機可以指定原則的程式碼的重要區域中的粗略的執行緒中止發生時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a8c64-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="a8c64-114">主機可以指定原則粗略的執行緒中止發生非關鍵的程式碼區域中時可採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a8c64-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8c64-115">備註</span><span class="sxs-lookup"><span data-stu-id="a8c64-115">Remarks</span></span>  
 <span data-ttu-id="a8c64-116">Common language runtime (CLR) 可靠性基礎結構以區別中止而資源會發生在程式碼和發生非關鍵的程式碼區域中的關鍵區域的配置失敗。</span><span class="sxs-lookup"><span data-stu-id="a8c64-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="a8c64-117">這個差別被為了讓主應用程式設定不同的原則，根據程式碼中發生失敗。</span><span class="sxs-lookup"><span data-stu-id="a8c64-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="a8c64-118">A*的程式碼的重要區域*當該中止工作或無法完成要求的資源將會影響目前的工作不能保證 CLR 任何空間。</span><span class="sxs-lookup"><span data-stu-id="a8c64-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="a8c64-119">比方說，如果工作會保留鎖定，並收到指出時進行記憶體配置要求失敗的 HRESULT，是不足，無法只是終止該工作，以確保穩定性<xref:System.AppDomain>，因為<xref:System.AppDomain>可能包含其他針對相同鎖定等候的工作。</span><span class="sxs-lookup"><span data-stu-id="a8c64-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="a8c64-120">要放棄目前的工作可能會使這些其他工作，來停止回應 （或擱置） 無限期。</span><span class="sxs-lookup"><span data-stu-id="a8c64-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="a8c64-121">在這種情況下，主機必須能卸載整個<xref:System.AppDomain>而不是風險潛在的不穩定。</span><span class="sxs-lookup"><span data-stu-id="a8c64-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="a8c64-122">A*非關鍵的程式碼區域*，相反地，是 CLR 可保證 「 中止 」 或 「 失敗將會影響只有工作錯誤發生所在的區域。</span><span class="sxs-lookup"><span data-stu-id="a8c64-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="a8c64-123">CLR 也區分非失誤性和非正常程序 （粗略） 中止。</span><span class="sxs-lookup"><span data-stu-id="a8c64-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="a8c64-124">一般情況下，正常的中止會盡全力之前中止工作，而粗略中止可不讓任何這類保證執行例外狀況處理常式和完成項。</span><span class="sxs-lookup"><span data-stu-id="a8c64-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8c64-125">需求</span><span class="sxs-lookup"><span data-stu-id="a8c64-125">Requirements</span></span>  
 <span data-ttu-id="a8c64-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8c64-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8c64-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a8c64-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8c64-128">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8c64-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8c64-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c64-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c64-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8c64-130">See Also</span></span>  
 [<span data-ttu-id="a8c64-131">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="a8c64-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="a8c64-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="a8c64-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="a8c64-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="a8c64-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="a8c64-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="a8c64-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="a8c64-135">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="a8c64-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
