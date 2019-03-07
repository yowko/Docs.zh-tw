---
title: ICLRPolicyManager::SetDefaultAction 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 502d6298ec7046dcce2b413d6bfaa3ef27529e49
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484338"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="89fbf-102">ICLRPolicyManager::SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="89fbf-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="89fbf-103">指定 common language runtime (CLR) 在指定的作業，就會發生時，所應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="89fbf-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89fbf-104">語法</span><span class="sxs-lookup"><span data-stu-id="89fbf-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89fbf-105">參數</span><span class="sxs-lookup"><span data-stu-id="89fbf-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="89fbf-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，指出哪一個 clr 您應該自訂行為的動作。</span><span class="sxs-lookup"><span data-stu-id="89fbf-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="89fbf-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示原則動作 CLR 應該時採取`operation`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="89fbf-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89fbf-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="89fbf-108">Return Value</span></span>  
  
|<span data-ttu-id="89fbf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89fbf-109">HRESULT</span></span>|<span data-ttu-id="89fbf-110">描述</span><span class="sxs-lookup"><span data-stu-id="89fbf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89fbf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="89fbf-111">S_OK</span></span>|<span data-ttu-id="89fbf-112">`SetDefaultAction` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="89fbf-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="89fbf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="89fbf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="89fbf-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="89fbf-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="89fbf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="89fbf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="89fbf-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="89fbf-116">The call timed out.</span></span>|  
|<span data-ttu-id="89fbf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="89fbf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="89fbf-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="89fbf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="89fbf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="89fbf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="89fbf-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="89fbf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="89fbf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="89fbf-121">E_FAIL</span></span>|<span data-ttu-id="89fbf-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="89fbf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="89fbf-123">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="89fbf-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="89fbf-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="89fbf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="89fbf-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="89fbf-125">E_INVALIDARG</span></span>|<span data-ttu-id="89fbf-126">無效`action`所指定`operation`，或為無效的值提供`operation`。</span><span class="sxs-lookup"><span data-stu-id="89fbf-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89fbf-127">備註</span><span class="sxs-lookup"><span data-stu-id="89fbf-127">Remarks</span></span>  
 <span data-ttu-id="89fbf-128">並非所有的原則動作值可以指定為 CLR 作業的預設行為。</span><span class="sxs-lookup"><span data-stu-id="89fbf-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="89fbf-129">`SetDefaultAction` 通常可以用僅來擴大的行為。</span><span class="sxs-lookup"><span data-stu-id="89fbf-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="89fbf-130">比方說，主機可以指定成粗略開啟執行緒中止的執行緒中止，但不能指定相反。</span><span class="sxs-lookup"><span data-stu-id="89fbf-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="89fbf-131">下表描述的有效`action`每個可能的值`operation`值。</span><span class="sxs-lookup"><span data-stu-id="89fbf-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="89fbf-132">值 `operation`</span><span class="sxs-lookup"><span data-stu-id="89fbf-132">Value for `operation`</span></span>|<span data-ttu-id="89fbf-133">有效值 `action`</span><span class="sxs-lookup"><span data-stu-id="89fbf-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="89fbf-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="89fbf-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="89fbf-135">-   eAbortThread</span><span class="sxs-lookup"><span data-stu-id="89fbf-135">-   eAbortThread</span></span><br /><span data-ttu-id="89fbf-136">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="89fbf-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="89fbf-137">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-138">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-139">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-139">-   eExitProcess</span></span><br /><span data-ttu-id="89fbf-140">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="89fbf-141">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="89fbf-142">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="89fbf-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="89fbf-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="89fbf-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="89fbf-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="89fbf-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="89fbf-145">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="89fbf-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="89fbf-146">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-147">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-148">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-148">-   eExitProcess</span></span><br /><span data-ttu-id="89fbf-149">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="89fbf-150">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="89fbf-151">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="89fbf-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="89fbf-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="89fbf-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="89fbf-153">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-154">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-155">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-155">-   eExitProcess</span></span><br /><span data-ttu-id="89fbf-156">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="89fbf-157">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="89fbf-158">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="89fbf-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="89fbf-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="89fbf-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="89fbf-160">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-161">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-161">-   eExitProcess</span></span><br /><span data-ttu-id="89fbf-162">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="89fbf-163">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="89fbf-164">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="89fbf-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="89fbf-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="89fbf-165">OPR_ProcessExit</span></span>|<span data-ttu-id="89fbf-166">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-166">-   eExitProcess</span></span><br /><span data-ttu-id="89fbf-167">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="89fbf-168">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="89fbf-169">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="89fbf-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="89fbf-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="89fbf-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="89fbf-171">-   eNoAction</span><span class="sxs-lookup"><span data-stu-id="89fbf-171">-   eNoAction</span></span><br /><span data-ttu-id="89fbf-172">-   eAbortThread</span><span class="sxs-lookup"><span data-stu-id="89fbf-172">-   eAbortThread</span></span><br /><span data-ttu-id="89fbf-173">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="89fbf-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="89fbf-174">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-175">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="89fbf-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="89fbf-176">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-176">-   eExitProcess</span></span><br /><span data-ttu-id="89fbf-177">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="89fbf-178">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="89fbf-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="89fbf-179">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="89fbf-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89fbf-180">需求</span><span class="sxs-lookup"><span data-stu-id="89fbf-180">Requirements</span></span>  
 <span data-ttu-id="89fbf-181">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89fbf-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89fbf-182">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89fbf-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89fbf-183">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="89fbf-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89fbf-184">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89fbf-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89fbf-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89fbf-185">See also</span></span>
- [<span data-ttu-id="89fbf-186">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="89fbf-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="89fbf-187">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="89fbf-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="89fbf-188">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="89fbf-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
