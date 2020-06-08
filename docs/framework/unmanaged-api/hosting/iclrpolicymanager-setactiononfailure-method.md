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
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504104"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="8c8e6-102">ICLRPolicyManager::SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="8c8e6-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="8c8e6-103">指定當發生指定的失敗時，common language runtime （CLR）應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c8e6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c8e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c8e6-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="8c8e6-106">在其中一個[EClrFailure](eclrfailure-enumeration.md)值，表示要採取動作的失敗類型。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="8c8e6-107">在其中一個[EPolicyAction](epolicyaction-enumeration.md)值，表示發生失敗時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="8c8e6-108">如需支援值的清單，請參閱備註一節。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c8e6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8c8e6-109">Return Value</span></span>  
  
|<span data-ttu-id="8c8e6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c8e6-110">HRESULT</span></span>|<span data-ttu-id="8c8e6-111">說明</span><span class="sxs-lookup"><span data-stu-id="8c8e6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c8e6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c8e6-112">S_OK</span></span>|<span data-ttu-id="8c8e6-113">`SetActionOnFailure`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="8c8e6-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c8e6-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c8e6-115">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c8e6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c8e6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c8e6-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-117">The call timed out.</span></span>|  
|<span data-ttu-id="8c8e6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c8e6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c8e6-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c8e6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c8e6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c8e6-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c8e6-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c8e6-122">E_FAIL</span></span>|<span data-ttu-id="8c8e6-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c8e6-124">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c8e6-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8c8e6-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8c8e6-126">E_INVALIDARG</span></span>|<span data-ttu-id="8c8e6-127">無法為指定的作業設定原則動作，或為操作指定了不正確原則動作。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c8e6-128">備註</span><span class="sxs-lookup"><span data-stu-id="8c8e6-128">Remarks</span></span>  
 <span data-ttu-id="8c8e6-129">根據預設，CLR 會在無法配置資源（例如記憶體）時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="8c8e6-130">`SetActionOnFailure`允許主機藉由指定失敗時所要採取的原則動作來覆寫此行為。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="8c8e6-131">下表顯示支援的[EClrFailure](eclrfailure-enumeration.md)和[EPolicyAction](epolicyaction-enumeration.md)值組合。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="8c8e6-132">（ [EClrFailure](eclrfailure-enumeration.md)值中會省略 FAIL_ 前置詞）。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="8c8e6-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="8c8e6-133">NonCriticalResource</span></span>|<span data-ttu-id="8c8e6-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="8c8e6-134">CriticalResource</span></span>|<span data-ttu-id="8c8e6-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="8c8e6-135">FatalRuntime</span></span>|<span data-ttu-id="8c8e6-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="8c8e6-136">OrphanedLock</span></span>|<span data-ttu-id="8c8e6-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="8c8e6-137">StackOverflow</span></span>|<span data-ttu-id="8c8e6-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="8c8e6-138">AccessViolation</span></span>|<span data-ttu-id="8c8e6-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="8c8e6-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="8c8e6-140">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-140">X</span></span>|<span data-ttu-id="8c8e6-141">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-141">X</span></span>||||<span data-ttu-id="8c8e6-142">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-142">N/A</span></span>||  
|<span data-ttu-id="8c8e6-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="8c8e6-143">eThrowException</span></span>|<span data-ttu-id="8c8e6-144">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-144">X</span></span>|<span data-ttu-id="8c8e6-145">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-145">X</span></span>||||<span data-ttu-id="8c8e6-146">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="8c8e6-147">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-147">X</span></span>|<span data-ttu-id="8c8e6-148">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-148">X</span></span>||||<span data-ttu-id="8c8e6-149">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-149">N/A</span></span>|<span data-ttu-id="8c8e6-150">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="8c8e6-151">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-151">X</span></span>|<span data-ttu-id="8c8e6-152">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-152">X</span></span>||||<span data-ttu-id="8c8e6-153">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-153">N/A</span></span>|<span data-ttu-id="8c8e6-154">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="8c8e6-155">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-155">X</span></span>|<span data-ttu-id="8c8e6-156">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-156">X</span></span>||<span data-ttu-id="8c8e6-157">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-157">X</span></span>||<span data-ttu-id="8c8e6-158">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-158">N/A</span></span>|<span data-ttu-id="8c8e6-159">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="8c8e6-160">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-160">X</span></span>|<span data-ttu-id="8c8e6-161">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-161">X</span></span>||<span data-ttu-id="8c8e6-162">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-162">X</span></span>|<span data-ttu-id="8c8e6-163">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-163">X</span></span>|<span data-ttu-id="8c8e6-164">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-164">N/A</span></span>|<span data-ttu-id="8c8e6-165">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="8c8e6-166">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-166">X</span></span>|<span data-ttu-id="8c8e6-167">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-167">X</span></span>||<span data-ttu-id="8c8e6-168">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-168">X</span></span>|<span data-ttu-id="8c8e6-169">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-169">X</span></span>|<span data-ttu-id="8c8e6-170">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-170">N/A</span></span>|<span data-ttu-id="8c8e6-171">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-171">X</span></span>|  
|<span data-ttu-id="8c8e6-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="8c8e6-172">eFastExitProcess</span></span>|<span data-ttu-id="8c8e6-173">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-173">X</span></span>|<span data-ttu-id="8c8e6-174">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-174">X</span></span>||<span data-ttu-id="8c8e6-175">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-175">X</span></span>|<span data-ttu-id="8c8e6-176">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-176">X</span></span>|<span data-ttu-id="8c8e6-177">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="8c8e6-178">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-178">X</span></span>|<span data-ttu-id="8c8e6-179">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-179">X</span></span>|<span data-ttu-id="8c8e6-180">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-180">X</span></span>|<span data-ttu-id="8c8e6-181">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-181">X</span></span>|<span data-ttu-id="8c8e6-182">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-182">X</span></span>|<span data-ttu-id="8c8e6-183">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="8c8e6-184">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-184">X</span></span>|<span data-ttu-id="8c8e6-185">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-185">X</span></span>|<span data-ttu-id="8c8e6-186">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-186">X</span></span>|<span data-ttu-id="8c8e6-187">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-187">X</span></span>|<span data-ttu-id="8c8e6-188">X</span><span class="sxs-lookup"><span data-stu-id="8c8e6-188">X</span></span>|<span data-ttu-id="8c8e6-189">N/A</span><span class="sxs-lookup"><span data-stu-id="8c8e6-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="8c8e6-190">規格需求</span><span class="sxs-lookup"><span data-stu-id="8c8e6-190">Requirements</span></span>  
 <span data-ttu-id="8c8e6-191">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c8e6-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c8e6-192">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8c8e6-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c8e6-193">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8c8e6-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c8e6-194">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8e6-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8e6-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c8e6-195">See also</span></span>

- [<span data-ttu-id="8c8e6-196">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="8c8e6-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="8c8e6-197">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="8c8e6-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8c8e6-198">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="8c8e6-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8c8e6-199">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8c8e6-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
