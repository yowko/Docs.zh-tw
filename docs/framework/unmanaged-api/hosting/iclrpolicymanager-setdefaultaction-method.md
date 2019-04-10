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
ms.openlocfilehash: 3d339fbadc3260d20fac848ad7f1a9031c3443aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154657"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="28ce7-102">ICLRPolicyManager::SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="28ce7-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="28ce7-103">指定 common language runtime (CLR) 在指定的作業，就會發生時，所應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="28ce7-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ce7-104">語法</span><span class="sxs-lookup"><span data-stu-id="28ce7-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28ce7-105">參數</span><span class="sxs-lookup"><span data-stu-id="28ce7-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="28ce7-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，指出哪一個 clr 您應該自訂行為的動作。</span><span class="sxs-lookup"><span data-stu-id="28ce7-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="28ce7-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示原則動作 CLR 應該時採取`operation`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="28ce7-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28ce7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="28ce7-108">Return Value</span></span>  
  
|<span data-ttu-id="28ce7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28ce7-109">HRESULT</span></span>|<span data-ttu-id="28ce7-110">描述</span><span class="sxs-lookup"><span data-stu-id="28ce7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28ce7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="28ce7-111">S_OK</span></span>|`SetDefaultAction` <span data-ttu-id="28ce7-112">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="28ce7-112">returned successfully.</span></span>|  
|<span data-ttu-id="28ce7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28ce7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28ce7-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="28ce7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28ce7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28ce7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28ce7-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="28ce7-116">The call timed out.</span></span>|  
|<span data-ttu-id="28ce7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28ce7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28ce7-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="28ce7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28ce7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28ce7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28ce7-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="28ce7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28ce7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28ce7-121">E_FAIL</span></span>|<span data-ttu-id="28ce7-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="28ce7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28ce7-123">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="28ce7-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28ce7-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="28ce7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="28ce7-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="28ce7-125">E_INVALIDARG</span></span>|<span data-ttu-id="28ce7-126">無效`action`所指定`operation`，或為無效的值提供`operation`。</span><span class="sxs-lookup"><span data-stu-id="28ce7-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28ce7-127">備註</span><span class="sxs-lookup"><span data-stu-id="28ce7-127">Remarks</span></span>  
 <span data-ttu-id="28ce7-128">並非所有的原則動作值可以指定為 CLR 作業的預設行為。</span><span class="sxs-lookup"><span data-stu-id="28ce7-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> `SetDefaultAction` <span data-ttu-id="28ce7-129">通常可以用僅來擴大的行為。</span><span class="sxs-lookup"><span data-stu-id="28ce7-129">can typically be used only to escalate behavior.</span></span> <span data-ttu-id="28ce7-130">比方說，主機可以指定成粗略開啟執行緒中止的執行緒中止，但不能指定相反。</span><span class="sxs-lookup"><span data-stu-id="28ce7-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="28ce7-131">下表描述的有效`action`每個可能的值`operation`值。</span><span class="sxs-lookup"><span data-stu-id="28ce7-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="28ce7-132">值</span><span class="sxs-lookup"><span data-stu-id="28ce7-132">Value for</span></span> `operation`|<span data-ttu-id="28ce7-133">有效值</span><span class="sxs-lookup"><span data-stu-id="28ce7-133">Valid values for</span></span> `action`|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="28ce7-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="28ce7-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="28ce7-135">-   eAbortThread</span><span class="sxs-lookup"><span data-stu-id="28ce7-135">-   eAbortThread</span></span><br /><span data-ttu-id="28ce7-136">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="28ce7-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="28ce7-137">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-138">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-139">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-139">-   eExitProcess</span></span><br /><span data-ttu-id="28ce7-140">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="28ce7-141">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="28ce7-142">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="28ce7-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="28ce7-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="28ce7-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="28ce7-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="28ce7-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="28ce7-145">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="28ce7-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="28ce7-146">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-147">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-148">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-148">-   eExitProcess</span></span><br /><span data-ttu-id="28ce7-149">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="28ce7-150">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="28ce7-151">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="28ce7-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="28ce7-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="28ce7-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="28ce7-153">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-154">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-155">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-155">-   eExitProcess</span></span><br /><span data-ttu-id="28ce7-156">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="28ce7-157">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="28ce7-158">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="28ce7-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="28ce7-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="28ce7-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="28ce7-160">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-161">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-161">-   eExitProcess</span></span><br /><span data-ttu-id="28ce7-162">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="28ce7-163">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="28ce7-164">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="28ce7-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="28ce7-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="28ce7-165">OPR_ProcessExit</span></span>|<span data-ttu-id="28ce7-166">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-166">-   eExitProcess</span></span><br /><span data-ttu-id="28ce7-167">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="28ce7-168">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="28ce7-169">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="28ce7-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="28ce7-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="28ce7-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="28ce7-171">-   eNoAction</span><span class="sxs-lookup"><span data-stu-id="28ce7-171">-   eNoAction</span></span><br /><span data-ttu-id="28ce7-172">-   eAbortThread</span><span class="sxs-lookup"><span data-stu-id="28ce7-172">-   eAbortThread</span></span><br /><span data-ttu-id="28ce7-173">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="28ce7-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="28ce7-174">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-175">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="28ce7-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="28ce7-176">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-176">-   eExitProcess</span></span><br /><span data-ttu-id="28ce7-177">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="28ce7-178">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="28ce7-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="28ce7-179">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="28ce7-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28ce7-180">需求</span><span class="sxs-lookup"><span data-stu-id="28ce7-180">Requirements</span></span>  
 <span data-ttu-id="28ce7-181">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28ce7-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ce7-182">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28ce7-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28ce7-183">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="28ce7-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="28ce7-184">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="28ce7-184">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="28ce7-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28ce7-185">See also</span></span>

- [<span data-ttu-id="28ce7-186">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="28ce7-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="28ce7-187">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="28ce7-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="28ce7-188">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="28ce7-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
