---
title: "ICLRPolicyManager::SetActionOnFailure 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4440b36485ed900b5e64adcead2525dbb7d5206e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="0130f-102">ICLRPolicyManager::SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="0130f-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="0130f-103">指定發生指定的失敗時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="0130f-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0130f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0130f-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0130f-105">參數</span><span class="sxs-lookup"><span data-stu-id="0130f-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="0130f-106">[in]其中一個[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值，表示要採取的動作失敗的類型。</span><span class="sxs-lookup"><span data-stu-id="0130f-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="0130f-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示發生失敗時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="0130f-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="0130f-108">如需支援的值的清單，請參閱 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="0130f-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0130f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0130f-109">Return Value</span></span>  
  
|<span data-ttu-id="0130f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0130f-110">HRESULT</span></span>|<span data-ttu-id="0130f-111">描述</span><span class="sxs-lookup"><span data-stu-id="0130f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0130f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0130f-112">S_OK</span></span>|<span data-ttu-id="0130f-113">`SetActionOnFailure`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0130f-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="0130f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0130f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0130f-115">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0130f-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0130f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0130f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0130f-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0130f-117">The call timed out.</span></span>|  
|<span data-ttu-id="0130f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0130f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0130f-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0130f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0130f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0130f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0130f-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0130f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0130f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0130f-122">E_FAIL</span></span>|<span data-ttu-id="0130f-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0130f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0130f-124">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="0130f-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0130f-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0130f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0130f-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0130f-126">E_INVALIDARG</span></span>|<span data-ttu-id="0130f-127">無法為指定的作業，設定原則動作或作業指定了無效的原則。</span><span class="sxs-lookup"><span data-stu-id="0130f-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0130f-128">備註</span><span class="sxs-lookup"><span data-stu-id="0130f-128">Remarks</span></span>  
 <span data-ttu-id="0130f-129">根據預設，CLR 會在無法配置資源，例如記憶體時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0130f-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="0130f-130">`SetActionOnFailure`可讓主應用程式藉由指定原則来採取的動作失敗時覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="0130f-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="0130f-131">下表顯示的組合[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)和[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)支援的值。</span><span class="sxs-lookup"><span data-stu-id="0130f-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="0130f-132">(FAIL_ 前置詞會省略[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值。)</span><span class="sxs-lookup"><span data-stu-id="0130f-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="0130f-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="0130f-133">NonCriticalResource</span></span>|<span data-ttu-id="0130f-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="0130f-134">CriticalResource</span></span>|<span data-ttu-id="0130f-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="0130f-135">FatalRuntime</span></span>|<span data-ttu-id="0130f-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="0130f-136">OrphanedLock</span></span>|<span data-ttu-id="0130f-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="0130f-137">StackOverflow</span></span>|<span data-ttu-id="0130f-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="0130f-138">AccessViolation</span></span>|<span data-ttu-id="0130f-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="0130f-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="0130f-140">X</span><span class="sxs-lookup"><span data-stu-id="0130f-140">X</span></span>|<span data-ttu-id="0130f-141">X</span><span class="sxs-lookup"><span data-stu-id="0130f-141">X</span></span>||||<span data-ttu-id="0130f-142">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-142">N/A</span></span>||  
|<span data-ttu-id="0130f-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="0130f-143">eThrowException</span></span>|<span data-ttu-id="0130f-144">X</span><span class="sxs-lookup"><span data-stu-id="0130f-144">X</span></span>|<span data-ttu-id="0130f-145">X</span><span class="sxs-lookup"><span data-stu-id="0130f-145">X</span></span>||||<span data-ttu-id="0130f-146">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="0130f-147">X</span><span class="sxs-lookup"><span data-stu-id="0130f-147">X</span></span>|<span data-ttu-id="0130f-148">X</span><span class="sxs-lookup"><span data-stu-id="0130f-148">X</span></span>||||<span data-ttu-id="0130f-149">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-149">N/A</span></span>|<span data-ttu-id="0130f-150">X</span><span class="sxs-lookup"><span data-stu-id="0130f-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="0130f-151">X</span><span class="sxs-lookup"><span data-stu-id="0130f-151">X</span></span>|<span data-ttu-id="0130f-152">X</span><span class="sxs-lookup"><span data-stu-id="0130f-152">X</span></span>||||<span data-ttu-id="0130f-153">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-153">N/A</span></span>|<span data-ttu-id="0130f-154">X</span><span class="sxs-lookup"><span data-stu-id="0130f-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="0130f-155">X</span><span class="sxs-lookup"><span data-stu-id="0130f-155">X</span></span>|<span data-ttu-id="0130f-156">X</span><span class="sxs-lookup"><span data-stu-id="0130f-156">X</span></span>||<span data-ttu-id="0130f-157">X</span><span class="sxs-lookup"><span data-stu-id="0130f-157">X</span></span>||<span data-ttu-id="0130f-158">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-158">N/A</span></span>|<span data-ttu-id="0130f-159">X</span><span class="sxs-lookup"><span data-stu-id="0130f-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="0130f-160">X</span><span class="sxs-lookup"><span data-stu-id="0130f-160">X</span></span>|<span data-ttu-id="0130f-161">X</span><span class="sxs-lookup"><span data-stu-id="0130f-161">X</span></span>||<span data-ttu-id="0130f-162">X</span><span class="sxs-lookup"><span data-stu-id="0130f-162">X</span></span>|<span data-ttu-id="0130f-163">X</span><span class="sxs-lookup"><span data-stu-id="0130f-163">X</span></span>|<span data-ttu-id="0130f-164">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-164">N/A</span></span>|<span data-ttu-id="0130f-165">X</span><span class="sxs-lookup"><span data-stu-id="0130f-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="0130f-166">X</span><span class="sxs-lookup"><span data-stu-id="0130f-166">X</span></span>|<span data-ttu-id="0130f-167">X</span><span class="sxs-lookup"><span data-stu-id="0130f-167">X</span></span>||<span data-ttu-id="0130f-168">X</span><span class="sxs-lookup"><span data-stu-id="0130f-168">X</span></span>|<span data-ttu-id="0130f-169">X</span><span class="sxs-lookup"><span data-stu-id="0130f-169">X</span></span>|<span data-ttu-id="0130f-170">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-170">N/A</span></span>|<span data-ttu-id="0130f-171">X</span><span class="sxs-lookup"><span data-stu-id="0130f-171">X</span></span>|  
|<span data-ttu-id="0130f-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="0130f-172">eFastExitProcess</span></span>|<span data-ttu-id="0130f-173">X</span><span class="sxs-lookup"><span data-stu-id="0130f-173">X</span></span>|<span data-ttu-id="0130f-174">X</span><span class="sxs-lookup"><span data-stu-id="0130f-174">X</span></span>||<span data-ttu-id="0130f-175">X</span><span class="sxs-lookup"><span data-stu-id="0130f-175">X</span></span>|<span data-ttu-id="0130f-176">X</span><span class="sxs-lookup"><span data-stu-id="0130f-176">X</span></span>|<span data-ttu-id="0130f-177">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="0130f-178">X</span><span class="sxs-lookup"><span data-stu-id="0130f-178">X</span></span>|<span data-ttu-id="0130f-179">X</span><span class="sxs-lookup"><span data-stu-id="0130f-179">X</span></span>|<span data-ttu-id="0130f-180">X</span><span class="sxs-lookup"><span data-stu-id="0130f-180">X</span></span>|<span data-ttu-id="0130f-181">X</span><span class="sxs-lookup"><span data-stu-id="0130f-181">X</span></span>|<span data-ttu-id="0130f-182">X</span><span class="sxs-lookup"><span data-stu-id="0130f-182">X</span></span>|<span data-ttu-id="0130f-183">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="0130f-184">X</span><span class="sxs-lookup"><span data-stu-id="0130f-184">X</span></span>|<span data-ttu-id="0130f-185">X</span><span class="sxs-lookup"><span data-stu-id="0130f-185">X</span></span>|<span data-ttu-id="0130f-186">X</span><span class="sxs-lookup"><span data-stu-id="0130f-186">X</span></span>|<span data-ttu-id="0130f-187">X</span><span class="sxs-lookup"><span data-stu-id="0130f-187">X</span></span>|<span data-ttu-id="0130f-188">X</span><span class="sxs-lookup"><span data-stu-id="0130f-188">X</span></span>|<span data-ttu-id="0130f-189">N/A</span><span class="sxs-lookup"><span data-stu-id="0130f-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="0130f-190">需求</span><span class="sxs-lookup"><span data-stu-id="0130f-190">Requirements</span></span>  
 <span data-ttu-id="0130f-191">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0130f-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0130f-192">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0130f-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0130f-193">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0130f-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0130f-194">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0130f-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0130f-195">請參閱</span><span class="sxs-lookup"><span data-stu-id="0130f-195">See Also</span></span>  
 [<span data-ttu-id="0130f-196">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="0130f-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="0130f-197">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="0130f-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="0130f-198">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="0130f-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="0130f-199">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0130f-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
