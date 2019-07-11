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
ms.openlocfilehash: 63398902071b4cfa1964f77b5641baa6e6239eb5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757365"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="fd3c3-102">ICLRPolicyManager::SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="fd3c3-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="fd3c3-103">指定 common language runtime (CLR) 在指定的作業，就會發生時，所應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd3c3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd3c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd3c3-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="fd3c3-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，指出哪一個 clr 您應該自訂行為的動作。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="fd3c3-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示原則動作 CLR 應該時採取`operation`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd3c3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd3c3-108">Return Value</span></span>  
  
|<span data-ttu-id="fd3c3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd3c3-109">HRESULT</span></span>|<span data-ttu-id="fd3c3-110">描述</span><span class="sxs-lookup"><span data-stu-id="fd3c3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd3c3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd3c3-111">S_OK</span></span>|<span data-ttu-id="fd3c3-112">`SetDefaultAction` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="fd3c3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd3c3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd3c3-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd3c3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd3c3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd3c3-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-116">The call timed out.</span></span>|  
|<span data-ttu-id="fd3c3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd3c3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd3c3-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd3c3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd3c3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd3c3-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd3c3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd3c3-121">E_FAIL</span></span>|<span data-ttu-id="fd3c3-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd3c3-123">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd3c3-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fd3c3-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fd3c3-125">E_INVALIDARG</span></span>|<span data-ttu-id="fd3c3-126">無效`action`所指定`operation`，或為無效的值提供`operation`。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd3c3-127">備註</span><span class="sxs-lookup"><span data-stu-id="fd3c3-127">Remarks</span></span>  
 <span data-ttu-id="fd3c3-128">並非所有的原則動作值可以指定為 CLR 作業的預設行為。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="fd3c3-129">`SetDefaultAction` 通常可以用僅來擴大的行為。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="fd3c3-130">比方說，主機可以指定成粗略開啟執行緒中止的執行緒中止，但不能指定相反。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="fd3c3-131">下表描述的有效`action`每個可能的值`operation`值。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="fd3c3-132">值 `operation`</span><span class="sxs-lookup"><span data-stu-id="fd3c3-132">Value for `operation`</span></span>|<span data-ttu-id="fd3c3-133">有效值 `action`</span><span class="sxs-lookup"><span data-stu-id="fd3c3-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="fd3c3-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="fd3c3-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="fd3c3-135">-   eAbortThread</span><span class="sxs-lookup"><span data-stu-id="fd3c3-135">-   eAbortThread</span></span><br /><span data-ttu-id="fd3c3-136">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="fd3c3-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="fd3c3-137">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-138">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-139">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-139">-   eExitProcess</span></span><br /><span data-ttu-id="fd3c3-140">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="fd3c3-141">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fd3c3-142">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="fd3c3-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="fd3c3-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="fd3c3-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="fd3c3-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="fd3c3-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="fd3c3-145">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="fd3c3-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="fd3c3-146">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-147">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-148">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-148">-   eExitProcess</span></span><br /><span data-ttu-id="fd3c3-149">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="fd3c3-150">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fd3c3-151">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="fd3c3-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="fd3c3-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="fd3c3-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="fd3c3-153">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-154">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-155">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-155">-   eExitProcess</span></span><br /><span data-ttu-id="fd3c3-156">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="fd3c3-157">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fd3c3-158">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="fd3c3-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="fd3c3-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="fd3c3-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="fd3c3-160">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-161">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-161">-   eExitProcess</span></span><br /><span data-ttu-id="fd3c3-162">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="fd3c3-163">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fd3c3-164">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="fd3c3-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="fd3c3-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="fd3c3-165">OPR_ProcessExit</span></span>|<span data-ttu-id="fd3c3-166">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-166">-   eExitProcess</span></span><br /><span data-ttu-id="fd3c3-167">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="fd3c3-168">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fd3c3-169">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="fd3c3-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="fd3c3-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="fd3c3-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="fd3c3-171">-   eNoAction</span><span class="sxs-lookup"><span data-stu-id="fd3c3-171">-   eNoAction</span></span><br /><span data-ttu-id="fd3c3-172">-   eAbortThread</span><span class="sxs-lookup"><span data-stu-id="fd3c3-172">-   eAbortThread</span></span><br /><span data-ttu-id="fd3c3-173">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="fd3c3-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="fd3c3-174">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-175">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fd3c3-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="fd3c3-176">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-176">-   eExitProcess</span></span><br /><span data-ttu-id="fd3c3-177">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="fd3c3-178">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="fd3c3-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fd3c3-179">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="fd3c3-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd3c3-180">需求</span><span class="sxs-lookup"><span data-stu-id="fd3c3-180">Requirements</span></span>  
 <span data-ttu-id="fd3c3-181">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd3c3-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd3c3-182">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd3c3-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd3c3-183">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fd3c3-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd3c3-184">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd3c3-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3c3-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd3c3-185">See also</span></span>

- [<span data-ttu-id="fd3c3-186">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="fd3c3-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="fd3c3-187">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="fd3c3-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="fd3c3-188">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="fd3c3-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
