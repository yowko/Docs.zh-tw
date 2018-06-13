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
ms.openlocfilehash: bc3616b2cec0fa951df745e3c5f0468f74ab82bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435925"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="3bb0c-102">ICLRPolicyManager::SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="3bb0c-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="3bb0c-103">指定發生指定的失敗時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bb0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bb0c-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bb0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3bb0c-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="3bb0c-106">[in]其中一個[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值，表示要採取的動作失敗的類型。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="3bb0c-107">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示發生失敗時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="3bb0c-108">如需支援的值的清單，請參閱 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bb0c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3bb0c-109">Return Value</span></span>  
  
|<span data-ttu-id="3bb0c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3bb0c-110">HRESULT</span></span>|<span data-ttu-id="3bb0c-111">描述</span><span class="sxs-lookup"><span data-stu-id="3bb0c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bb0c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bb0c-112">S_OK</span></span>|<span data-ttu-id="3bb0c-113">`SetActionOnFailure` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="3bb0c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3bb0c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3bb0c-115">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3bb0c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3bb0c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3bb0c-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-117">The call timed out.</span></span>|  
|<span data-ttu-id="3bb0c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3bb0c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3bb0c-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3bb0c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3bb0c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3bb0c-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3bb0c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3bb0c-122">E_FAIL</span></span>|<span data-ttu-id="3bb0c-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3bb0c-124">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3bb0c-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3bb0c-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3bb0c-126">E_INVALIDARG</span></span>|<span data-ttu-id="3bb0c-127">無法為指定的作業，設定原則動作或作業指定了無效的原則。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bb0c-128">備註</span><span class="sxs-lookup"><span data-stu-id="3bb0c-128">Remarks</span></span>  
 <span data-ttu-id="3bb0c-129">根據預設，CLR 會在無法配置資源，例如記憶體時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="3bb0c-130">`SetActionOnFailure` 可讓主應用程式藉由指定原則来採取的動作失敗時覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="3bb0c-131">下表顯示的組合[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)和[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)支援的值。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="3bb0c-132">(FAIL_ 前置詞會省略[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值。)</span><span class="sxs-lookup"><span data-stu-id="3bb0c-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="3bb0c-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="3bb0c-133">NonCriticalResource</span></span>|<span data-ttu-id="3bb0c-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="3bb0c-134">CriticalResource</span></span>|<span data-ttu-id="3bb0c-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="3bb0c-135">FatalRuntime</span></span>|<span data-ttu-id="3bb0c-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="3bb0c-136">OrphanedLock</span></span>|<span data-ttu-id="3bb0c-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="3bb0c-137">StackOverflow</span></span>|<span data-ttu-id="3bb0c-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="3bb0c-138">AccessViolation</span></span>|<span data-ttu-id="3bb0c-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="3bb0c-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="3bb0c-140">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-140">X</span></span>|<span data-ttu-id="3bb0c-141">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-141">X</span></span>||||<span data-ttu-id="3bb0c-142">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-142">N/A</span></span>||  
|<span data-ttu-id="3bb0c-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="3bb0c-143">eThrowException</span></span>|<span data-ttu-id="3bb0c-144">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-144">X</span></span>|<span data-ttu-id="3bb0c-145">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-145">X</span></span>||||<span data-ttu-id="3bb0c-146">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="3bb0c-147">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-147">X</span></span>|<span data-ttu-id="3bb0c-148">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-148">X</span></span>||||<span data-ttu-id="3bb0c-149">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-149">N/A</span></span>|<span data-ttu-id="3bb0c-150">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="3bb0c-151">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-151">X</span></span>|<span data-ttu-id="3bb0c-152">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-152">X</span></span>||||<span data-ttu-id="3bb0c-153">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-153">N/A</span></span>|<span data-ttu-id="3bb0c-154">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="3bb0c-155">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-155">X</span></span>|<span data-ttu-id="3bb0c-156">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-156">X</span></span>||<span data-ttu-id="3bb0c-157">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-157">X</span></span>||<span data-ttu-id="3bb0c-158">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-158">N/A</span></span>|<span data-ttu-id="3bb0c-159">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="3bb0c-160">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-160">X</span></span>|<span data-ttu-id="3bb0c-161">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-161">X</span></span>||<span data-ttu-id="3bb0c-162">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-162">X</span></span>|<span data-ttu-id="3bb0c-163">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-163">X</span></span>|<span data-ttu-id="3bb0c-164">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-164">N/A</span></span>|<span data-ttu-id="3bb0c-165">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="3bb0c-166">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-166">X</span></span>|<span data-ttu-id="3bb0c-167">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-167">X</span></span>||<span data-ttu-id="3bb0c-168">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-168">X</span></span>|<span data-ttu-id="3bb0c-169">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-169">X</span></span>|<span data-ttu-id="3bb0c-170">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-170">N/A</span></span>|<span data-ttu-id="3bb0c-171">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-171">X</span></span>|  
|<span data-ttu-id="3bb0c-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3bb0c-172">eFastExitProcess</span></span>|<span data-ttu-id="3bb0c-173">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-173">X</span></span>|<span data-ttu-id="3bb0c-174">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-174">X</span></span>||<span data-ttu-id="3bb0c-175">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-175">X</span></span>|<span data-ttu-id="3bb0c-176">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-176">X</span></span>|<span data-ttu-id="3bb0c-177">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="3bb0c-178">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-178">X</span></span>|<span data-ttu-id="3bb0c-179">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-179">X</span></span>|<span data-ttu-id="3bb0c-180">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-180">X</span></span>|<span data-ttu-id="3bb0c-181">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-181">X</span></span>|<span data-ttu-id="3bb0c-182">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-182">X</span></span>|<span data-ttu-id="3bb0c-183">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="3bb0c-184">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-184">X</span></span>|<span data-ttu-id="3bb0c-185">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-185">X</span></span>|<span data-ttu-id="3bb0c-186">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-186">X</span></span>|<span data-ttu-id="3bb0c-187">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-187">X</span></span>|<span data-ttu-id="3bb0c-188">X</span><span class="sxs-lookup"><span data-stu-id="3bb0c-188">X</span></span>|<span data-ttu-id="3bb0c-189">N/A</span><span class="sxs-lookup"><span data-stu-id="3bb0c-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="3bb0c-190">需求</span><span class="sxs-lookup"><span data-stu-id="3bb0c-190">Requirements</span></span>  
 <span data-ttu-id="3bb0c-191">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb0c-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bb0c-192">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bb0c-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bb0c-193">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3bb0c-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bb0c-194">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bb0c-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb0c-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb0c-195">See Also</span></span>  
 [<span data-ttu-id="3bb0c-196">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="3bb0c-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="3bb0c-197">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="3bb0c-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="3bb0c-198">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="3bb0c-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3bb0c-199">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="3bb0c-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
