---
title: "ICLRPolicyManager::SetDefaultAction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetDefaultAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ecc2e35433a1021e230b45adddf3bede055d3dfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="acc47-102">ICLRPolicyManager::SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="acc47-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="acc47-103">指定發生指定的作業時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="acc47-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acc47-104">語法</span><span class="sxs-lookup"><span data-stu-id="acc47-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acc47-105">參數</span><span class="sxs-lookup"><span data-stu-id="acc47-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="acc47-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示應該用於哪些 CLR 自訂行為的動作。</span><span class="sxs-lookup"><span data-stu-id="acc47-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="acc47-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示原則 CLR 動作應該何時`operation`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="acc47-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acc47-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="acc47-108">Return Value</span></span>  
  
|<span data-ttu-id="acc47-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="acc47-109">HRESULT</span></span>|<span data-ttu-id="acc47-110">描述</span><span class="sxs-lookup"><span data-stu-id="acc47-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="acc47-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="acc47-111">S_OK</span></span>|<span data-ttu-id="acc47-112">`SetDefaultAction`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="acc47-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="acc47-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="acc47-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="acc47-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="acc47-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="acc47-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="acc47-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="acc47-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="acc47-116">The call timed out.</span></span>|  
|<span data-ttu-id="acc47-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="acc47-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="acc47-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="acc47-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="acc47-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="acc47-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="acc47-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="acc47-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="acc47-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="acc47-121">E_FAIL</span></span>|<span data-ttu-id="acc47-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="acc47-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="acc47-123">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="acc47-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="acc47-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="acc47-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="acc47-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="acc47-125">E_INVALIDARG</span></span>|<span data-ttu-id="acc47-126">無效的`action`指定`operation`，提供無效的值或`operation`。</span><span class="sxs-lookup"><span data-stu-id="acc47-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acc47-127">備註</span><span class="sxs-lookup"><span data-stu-id="acc47-127">Remarks</span></span>  
 <span data-ttu-id="acc47-128">並非所有的原則動作值可以指定為 CLR 作業的預設行為。</span><span class="sxs-lookup"><span data-stu-id="acc47-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="acc47-129">`SetDefaultAction`通常只以呈報問題使用。</span><span class="sxs-lookup"><span data-stu-id="acc47-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="acc47-130">例如，主機可以指定成粗略開啟執行緒中止的執行緒中止，但是不能指定相反。</span><span class="sxs-lookup"><span data-stu-id="acc47-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="acc47-131">下表描述有效`action`每個可能的值`operation`值。</span><span class="sxs-lookup"><span data-stu-id="acc47-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="acc47-132">值`operation`</span><span class="sxs-lookup"><span data-stu-id="acc47-132">Value for `operation`</span></span>|<span data-ttu-id="acc47-133">有效的值`action`</span><span class="sxs-lookup"><span data-stu-id="acc47-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="acc47-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="acc47-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="acc47-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="acc47-135">-   eAbortThread</span></span><br /><span data-ttu-id="acc47-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="acc47-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="acc47-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-139">-   eExitProcess</span></span><br /><span data-ttu-id="acc47-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="acc47-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="acc47-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="acc47-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="acc47-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="acc47-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="acc47-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="acc47-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="acc47-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="acc47-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="acc47-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-148">-   eExitProcess</span></span><br /><span data-ttu-id="acc47-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="acc47-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="acc47-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="acc47-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="acc47-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="acc47-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="acc47-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-155">-   eExitProcess</span></span><br /><span data-ttu-id="acc47-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="acc47-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="acc47-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="acc47-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="acc47-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="acc47-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="acc47-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-161">-   eExitProcess</span></span><br /><span data-ttu-id="acc47-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="acc47-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="acc47-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="acc47-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="acc47-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="acc47-165">OPR_ProcessExit</span></span>|<span data-ttu-id="acc47-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-166">-   eExitProcess</span></span><br /><span data-ttu-id="acc47-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="acc47-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="acc47-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="acc47-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="acc47-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="acc47-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="acc47-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="acc47-171">-   eNoAction</span></span><br /><span data-ttu-id="acc47-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="acc47-172">-   eAbortThread</span></span><br /><span data-ttu-id="acc47-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="acc47-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="acc47-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="acc47-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="acc47-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-176">-   eExitProcess</span></span><br /><span data-ttu-id="acc47-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="acc47-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="acc47-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="acc47-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="acc47-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="acc47-180">需求</span><span class="sxs-lookup"><span data-stu-id="acc47-180">Requirements</span></span>  
 <span data-ttu-id="acc47-181">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="acc47-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acc47-182">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="acc47-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="acc47-183">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="acc47-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acc47-184">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acc47-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc47-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acc47-185">See Also</span></span>  
 [<span data-ttu-id="acc47-186">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="acc47-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="acc47-187">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="acc47-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="acc47-188">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="acc47-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
