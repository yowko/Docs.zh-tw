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
ms.openlocfilehash: 143052febe136e969987c35bc06f6c3b3356aedf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140776"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="eaf29-102">ICLRPolicyManager::SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="eaf29-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="eaf29-103">指定當發生指定的失敗時，common language runtime （CLR）應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="eaf29-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf29-104">語法</span><span class="sxs-lookup"><span data-stu-id="eaf29-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaf29-105">參數</span><span class="sxs-lookup"><span data-stu-id="eaf29-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="eaf29-106">在其中一個[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值，表示要採取動作的失敗類型。</span><span class="sxs-lookup"><span data-stu-id="eaf29-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="eaf29-107">在其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示發生失敗時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="eaf29-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="eaf29-108">如需支援值的清單，請參閱備註一節。</span><span class="sxs-lookup"><span data-stu-id="eaf29-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaf29-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="eaf29-109">Return Value</span></span>  
  
|<span data-ttu-id="eaf29-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eaf29-110">HRESULT</span></span>|<span data-ttu-id="eaf29-111">描述</span><span class="sxs-lookup"><span data-stu-id="eaf29-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eaf29-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="eaf29-112">S_OK</span></span>|<span data-ttu-id="eaf29-113">已成功傳回 `SetActionOnFailure`。</span><span class="sxs-lookup"><span data-stu-id="eaf29-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="eaf29-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eaf29-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eaf29-115">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eaf29-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eaf29-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eaf29-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eaf29-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="eaf29-117">The call timed out.</span></span>|  
|<span data-ttu-id="eaf29-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eaf29-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eaf29-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eaf29-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eaf29-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eaf29-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eaf29-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="eaf29-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eaf29-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eaf29-122">E_FAIL</span></span>|<span data-ttu-id="eaf29-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eaf29-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eaf29-124">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="eaf29-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eaf29-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eaf29-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eaf29-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="eaf29-126">E_INVALIDARG</span></span>|<span data-ttu-id="eaf29-127">無法為指定的作業設定原則動作，或為操作指定了不正確原則動作。</span><span class="sxs-lookup"><span data-stu-id="eaf29-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaf29-128">備註</span><span class="sxs-lookup"><span data-stu-id="eaf29-128">Remarks</span></span>  
 <span data-ttu-id="eaf29-129">根據預設，CLR 會在無法配置資源（例如記憶體）時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eaf29-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="eaf29-130">`SetActionOnFailure` 可讓主機藉由指定失敗時所要採取的原則動作來覆寫此行為。</span><span class="sxs-lookup"><span data-stu-id="eaf29-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="eaf29-131">下表顯示支援的[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)和[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值組合。</span><span class="sxs-lookup"><span data-stu-id="eaf29-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="eaf29-132">（ [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值中會省略 FAIL_ 前置詞）。</span><span class="sxs-lookup"><span data-stu-id="eaf29-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="eaf29-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="eaf29-133">NonCriticalResource</span></span>|<span data-ttu-id="eaf29-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="eaf29-134">CriticalResource</span></span>|<span data-ttu-id="eaf29-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="eaf29-135">FatalRuntime</span></span>|<span data-ttu-id="eaf29-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="eaf29-136">OrphanedLock</span></span>|<span data-ttu-id="eaf29-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="eaf29-137">StackOverflow</span></span>|<span data-ttu-id="eaf29-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="eaf29-138">AccessViolation</span></span>|<span data-ttu-id="eaf29-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="eaf29-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="eaf29-140">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-140">X</span></span>|<span data-ttu-id="eaf29-141">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-141">X</span></span>||||<span data-ttu-id="eaf29-142">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-142">N/A</span></span>||  
|<span data-ttu-id="eaf29-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="eaf29-143">eThrowException</span></span>|<span data-ttu-id="eaf29-144">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-144">X</span></span>|<span data-ttu-id="eaf29-145">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-145">X</span></span>||||<span data-ttu-id="eaf29-146">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="eaf29-147">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-147">X</span></span>|<span data-ttu-id="eaf29-148">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-148">X</span></span>||||<span data-ttu-id="eaf29-149">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-149">N/A</span></span>|<span data-ttu-id="eaf29-150">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="eaf29-151">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-151">X</span></span>|<span data-ttu-id="eaf29-152">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-152">X</span></span>||||<span data-ttu-id="eaf29-153">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-153">N/A</span></span>|<span data-ttu-id="eaf29-154">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="eaf29-155">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-155">X</span></span>|<span data-ttu-id="eaf29-156">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-156">X</span></span>||<span data-ttu-id="eaf29-157">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-157">X</span></span>||<span data-ttu-id="eaf29-158">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-158">N/A</span></span>|<span data-ttu-id="eaf29-159">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="eaf29-160">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-160">X</span></span>|<span data-ttu-id="eaf29-161">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-161">X</span></span>||<span data-ttu-id="eaf29-162">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-162">X</span></span>|<span data-ttu-id="eaf29-163">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-163">X</span></span>|<span data-ttu-id="eaf29-164">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-164">N/A</span></span>|<span data-ttu-id="eaf29-165">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="eaf29-166">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-166">X</span></span>|<span data-ttu-id="eaf29-167">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-167">X</span></span>||<span data-ttu-id="eaf29-168">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-168">X</span></span>|<span data-ttu-id="eaf29-169">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-169">X</span></span>|<span data-ttu-id="eaf29-170">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-170">N/A</span></span>|<span data-ttu-id="eaf29-171">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-171">X</span></span>|  
|<span data-ttu-id="eaf29-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="eaf29-172">eFastExitProcess</span></span>|<span data-ttu-id="eaf29-173">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-173">X</span></span>|<span data-ttu-id="eaf29-174">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-174">X</span></span>||<span data-ttu-id="eaf29-175">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-175">X</span></span>|<span data-ttu-id="eaf29-176">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-176">X</span></span>|<span data-ttu-id="eaf29-177">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="eaf29-178">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-178">X</span></span>|<span data-ttu-id="eaf29-179">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-179">X</span></span>|<span data-ttu-id="eaf29-180">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-180">X</span></span>|<span data-ttu-id="eaf29-181">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-181">X</span></span>|<span data-ttu-id="eaf29-182">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-182">X</span></span>|<span data-ttu-id="eaf29-183">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="eaf29-184">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-184">X</span></span>|<span data-ttu-id="eaf29-185">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-185">X</span></span>|<span data-ttu-id="eaf29-186">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-186">X</span></span>|<span data-ttu-id="eaf29-187">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-187">X</span></span>|<span data-ttu-id="eaf29-188">x</span><span class="sxs-lookup"><span data-stu-id="eaf29-188">X</span></span>|<span data-ttu-id="eaf29-189">N/A</span><span class="sxs-lookup"><span data-stu-id="eaf29-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="eaf29-190">需求</span><span class="sxs-lookup"><span data-stu-id="eaf29-190">Requirements</span></span>  
 <span data-ttu-id="eaf29-191">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eaf29-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf29-192">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="eaf29-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eaf29-193">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eaf29-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaf29-194">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf29-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf29-195">請參閱</span><span class="sxs-lookup"><span data-stu-id="eaf29-195">See also</span></span>

- [<span data-ttu-id="eaf29-196">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="eaf29-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="eaf29-197">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="eaf29-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="eaf29-198">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="eaf29-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="eaf29-199">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="eaf29-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
