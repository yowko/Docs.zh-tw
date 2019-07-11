---
title: ICLRPolicyManager::SetActionOnFailure 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76f064d1683615ef8f665cf1facaa31d61b294a5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759591"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="22668-102">ICLRPolicyManager::SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="22668-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="22668-103">指定在發生指定的失敗時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="22668-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22668-104">語法</span><span class="sxs-lookup"><span data-stu-id="22668-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22668-105">參數</span><span class="sxs-lookup"><span data-stu-id="22668-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="22668-106">[in]其中一個[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值，表示要採取的動作失敗的類型。</span><span class="sxs-lookup"><span data-stu-id="22668-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="22668-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出發生失敗時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="22668-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="22668-108">如需支援的值的清單，請參閱 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="22668-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22668-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="22668-109">Return Value</span></span>  
  
|<span data-ttu-id="22668-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22668-110">HRESULT</span></span>|<span data-ttu-id="22668-111">描述</span><span class="sxs-lookup"><span data-stu-id="22668-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22668-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="22668-112">S_OK</span></span>|<span data-ttu-id="22668-113">`SetActionOnFailure` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="22668-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="22668-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22668-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22668-115">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="22668-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22668-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22668-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22668-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="22668-117">The call timed out.</span></span>|  
|<span data-ttu-id="22668-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22668-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22668-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="22668-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22668-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22668-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22668-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="22668-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22668-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22668-122">E_FAIL</span></span>|<span data-ttu-id="22668-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="22668-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22668-124">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="22668-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22668-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="22668-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="22668-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="22668-126">E_INVALIDARG</span></span>|<span data-ttu-id="22668-127">無法為指定的作業，設定原則動作或作業已指定無效的原則動作。</span><span class="sxs-lookup"><span data-stu-id="22668-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22668-128">備註</span><span class="sxs-lookup"><span data-stu-id="22668-128">Remarks</span></span>  
 <span data-ttu-id="22668-129">根據預設，CLR 會配置的資源，例如記憶體失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="22668-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="22668-130">`SetActionOnFailure` 可讓主機覆寫這個行為，藉由指定原則来採取的動作時失敗。</span><span class="sxs-lookup"><span data-stu-id="22668-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="22668-131">下表顯示的組合[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)並[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)所支援的值。</span><span class="sxs-lookup"><span data-stu-id="22668-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="22668-132">(FAIL_ 前置詞會略過[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值。)</span><span class="sxs-lookup"><span data-stu-id="22668-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="22668-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="22668-133">NonCriticalResource</span></span>|<span data-ttu-id="22668-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="22668-134">CriticalResource</span></span>|<span data-ttu-id="22668-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="22668-135">FatalRuntime</span></span>|<span data-ttu-id="22668-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="22668-136">OrphanedLock</span></span>|<span data-ttu-id="22668-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="22668-137">StackOverflow</span></span>|<span data-ttu-id="22668-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="22668-138">AccessViolation</span></span>|<span data-ttu-id="22668-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="22668-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="22668-140">X</span><span class="sxs-lookup"><span data-stu-id="22668-140">X</span></span>|<span data-ttu-id="22668-141">X</span><span class="sxs-lookup"><span data-stu-id="22668-141">X</span></span>||||<span data-ttu-id="22668-142">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-142">N/A</span></span>||  
|<span data-ttu-id="22668-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="22668-143">eThrowException</span></span>|<span data-ttu-id="22668-144">X</span><span class="sxs-lookup"><span data-stu-id="22668-144">X</span></span>|<span data-ttu-id="22668-145">X</span><span class="sxs-lookup"><span data-stu-id="22668-145">X</span></span>||||<span data-ttu-id="22668-146">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="22668-147">X</span><span class="sxs-lookup"><span data-stu-id="22668-147">X</span></span>|<span data-ttu-id="22668-148">X</span><span class="sxs-lookup"><span data-stu-id="22668-148">X</span></span>||||<span data-ttu-id="22668-149">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-149">N/A</span></span>|<span data-ttu-id="22668-150">X</span><span class="sxs-lookup"><span data-stu-id="22668-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="22668-151">X</span><span class="sxs-lookup"><span data-stu-id="22668-151">X</span></span>|<span data-ttu-id="22668-152">X</span><span class="sxs-lookup"><span data-stu-id="22668-152">X</span></span>||||<span data-ttu-id="22668-153">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-153">N/A</span></span>|<span data-ttu-id="22668-154">X</span><span class="sxs-lookup"><span data-stu-id="22668-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="22668-155">X</span><span class="sxs-lookup"><span data-stu-id="22668-155">X</span></span>|<span data-ttu-id="22668-156">X</span><span class="sxs-lookup"><span data-stu-id="22668-156">X</span></span>||<span data-ttu-id="22668-157">X</span><span class="sxs-lookup"><span data-stu-id="22668-157">X</span></span>||<span data-ttu-id="22668-158">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-158">N/A</span></span>|<span data-ttu-id="22668-159">X</span><span class="sxs-lookup"><span data-stu-id="22668-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="22668-160">X</span><span class="sxs-lookup"><span data-stu-id="22668-160">X</span></span>|<span data-ttu-id="22668-161">X</span><span class="sxs-lookup"><span data-stu-id="22668-161">X</span></span>||<span data-ttu-id="22668-162">X</span><span class="sxs-lookup"><span data-stu-id="22668-162">X</span></span>|<span data-ttu-id="22668-163">X</span><span class="sxs-lookup"><span data-stu-id="22668-163">X</span></span>|<span data-ttu-id="22668-164">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-164">N/A</span></span>|<span data-ttu-id="22668-165">X</span><span class="sxs-lookup"><span data-stu-id="22668-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="22668-166">X</span><span class="sxs-lookup"><span data-stu-id="22668-166">X</span></span>|<span data-ttu-id="22668-167">X</span><span class="sxs-lookup"><span data-stu-id="22668-167">X</span></span>||<span data-ttu-id="22668-168">X</span><span class="sxs-lookup"><span data-stu-id="22668-168">X</span></span>|<span data-ttu-id="22668-169">X</span><span class="sxs-lookup"><span data-stu-id="22668-169">X</span></span>|<span data-ttu-id="22668-170">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-170">N/A</span></span>|<span data-ttu-id="22668-171">X</span><span class="sxs-lookup"><span data-stu-id="22668-171">X</span></span>|  
|<span data-ttu-id="22668-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="22668-172">eFastExitProcess</span></span>|<span data-ttu-id="22668-173">X</span><span class="sxs-lookup"><span data-stu-id="22668-173">X</span></span>|<span data-ttu-id="22668-174">X</span><span class="sxs-lookup"><span data-stu-id="22668-174">X</span></span>||<span data-ttu-id="22668-175">X</span><span class="sxs-lookup"><span data-stu-id="22668-175">X</span></span>|<span data-ttu-id="22668-176">X</span><span class="sxs-lookup"><span data-stu-id="22668-176">X</span></span>|<span data-ttu-id="22668-177">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="22668-178">X</span><span class="sxs-lookup"><span data-stu-id="22668-178">X</span></span>|<span data-ttu-id="22668-179">X</span><span class="sxs-lookup"><span data-stu-id="22668-179">X</span></span>|<span data-ttu-id="22668-180">X</span><span class="sxs-lookup"><span data-stu-id="22668-180">X</span></span>|<span data-ttu-id="22668-181">X</span><span class="sxs-lookup"><span data-stu-id="22668-181">X</span></span>|<span data-ttu-id="22668-182">X</span><span class="sxs-lookup"><span data-stu-id="22668-182">X</span></span>|<span data-ttu-id="22668-183">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="22668-184">X</span><span class="sxs-lookup"><span data-stu-id="22668-184">X</span></span>|<span data-ttu-id="22668-185">X</span><span class="sxs-lookup"><span data-stu-id="22668-185">X</span></span>|<span data-ttu-id="22668-186">X</span><span class="sxs-lookup"><span data-stu-id="22668-186">X</span></span>|<span data-ttu-id="22668-187">X</span><span class="sxs-lookup"><span data-stu-id="22668-187">X</span></span>|<span data-ttu-id="22668-188">X</span><span class="sxs-lookup"><span data-stu-id="22668-188">X</span></span>|<span data-ttu-id="22668-189">N/A</span><span class="sxs-lookup"><span data-stu-id="22668-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="22668-190">需求</span><span class="sxs-lookup"><span data-stu-id="22668-190">Requirements</span></span>  
 <span data-ttu-id="22668-191">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22668-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22668-192">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22668-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22668-193">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="22668-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22668-194">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22668-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22668-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22668-195">See also</span></span>

- [<span data-ttu-id="22668-196">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="22668-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="22668-197">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="22668-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="22668-198">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="22668-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="22668-199">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="22668-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
