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
ms.openlocfilehash: 8f44247ca7904a40f5ebc092d95c2e08b6048438
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725569"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="95c96-102">ICLRPolicyManager::SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="95c96-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>

<span data-ttu-id="95c96-103">指定當指定的失敗發生時，common language runtime (CLR) 應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="95c96-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c96-104">語法</span><span class="sxs-lookup"><span data-stu-id="95c96-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95c96-105">參數</span><span class="sxs-lookup"><span data-stu-id="95c96-105">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="95c96-106">在其中一個 [EClrFailure](eclrfailure-enumeration.md) 值，表示要對其採取動作的失敗類型。</span><span class="sxs-lookup"><span data-stu-id="95c96-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="95c96-107">在其中一個 [EPolicyAction](epolicyaction-enumeration.md) 值，指出發生失敗時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="95c96-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="95c96-108">如需支援值的清單，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="95c96-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95c96-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="95c96-109">Return Value</span></span>  
  
|<span data-ttu-id="95c96-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95c96-110">HRESULT</span></span>|<span data-ttu-id="95c96-111">描述</span><span class="sxs-lookup"><span data-stu-id="95c96-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95c96-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="95c96-112">S_OK</span></span>|<span data-ttu-id="95c96-113">`SetActionOnFailure` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="95c96-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="95c96-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95c96-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95c96-115">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="95c96-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95c96-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95c96-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95c96-117">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="95c96-117">The call timed out.</span></span>|  
|<span data-ttu-id="95c96-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95c96-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95c96-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="95c96-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95c96-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95c96-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95c96-121">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="95c96-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95c96-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95c96-122">E_FAIL</span></span>|<span data-ttu-id="95c96-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="95c96-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95c96-124">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="95c96-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95c96-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="95c96-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95c96-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="95c96-126">E_INVALIDARG</span></span>|<span data-ttu-id="95c96-127">無法為指定的作業設定原則動作，或為作業指定了不正確原則動作。</span><span class="sxs-lookup"><span data-stu-id="95c96-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95c96-128">備註</span><span class="sxs-lookup"><span data-stu-id="95c96-128">Remarks</span></span>  

 <span data-ttu-id="95c96-129">根據預設，CLR 會在無法配置資源（例如記憶體）時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="95c96-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="95c96-130">`SetActionOnFailure` 藉由指定失敗時要採取的原則動作，讓主機覆寫此行為。</span><span class="sxs-lookup"><span data-stu-id="95c96-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="95c96-131">下表顯示支援的 [EClrFailure](eclrfailure-enumeration.md) 和 [EPolicyAction](epolicyaction-enumeration.md) 值的組合。</span><span class="sxs-lookup"><span data-stu-id="95c96-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="95c96-132"> (從 [EClrFailure](eclrfailure-enumeration.md) 值省略 FAIL_ 前置詞。 ) </span><span class="sxs-lookup"><span data-stu-id="95c96-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="95c96-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="95c96-133">NonCriticalResource</span></span>|<span data-ttu-id="95c96-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="95c96-134">CriticalResource</span></span>|<span data-ttu-id="95c96-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="95c96-135">FatalRuntime</span></span>|<span data-ttu-id="95c96-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="95c96-136">OrphanedLock</span></span>|<span data-ttu-id="95c96-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="95c96-137">StackOverflow</span></span>|<span data-ttu-id="95c96-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="95c96-138">AccessViolation</span></span>|<span data-ttu-id="95c96-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="95c96-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="95c96-140">X</span><span class="sxs-lookup"><span data-stu-id="95c96-140">X</span></span>|<span data-ttu-id="95c96-141">X</span><span class="sxs-lookup"><span data-stu-id="95c96-141">X</span></span>||||<span data-ttu-id="95c96-142">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-142">N/A</span></span>||  
|<span data-ttu-id="95c96-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="95c96-143">eThrowException</span></span>|<span data-ttu-id="95c96-144">X</span><span class="sxs-lookup"><span data-stu-id="95c96-144">X</span></span>|<span data-ttu-id="95c96-145">X</span><span class="sxs-lookup"><span data-stu-id="95c96-145">X</span></span>||||<span data-ttu-id="95c96-146">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="95c96-147">X</span><span class="sxs-lookup"><span data-stu-id="95c96-147">X</span></span>|<span data-ttu-id="95c96-148">X</span><span class="sxs-lookup"><span data-stu-id="95c96-148">X</span></span>||||<span data-ttu-id="95c96-149">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-149">N/A</span></span>|<span data-ttu-id="95c96-150">X</span><span class="sxs-lookup"><span data-stu-id="95c96-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="95c96-151">X</span><span class="sxs-lookup"><span data-stu-id="95c96-151">X</span></span>|<span data-ttu-id="95c96-152">X</span><span class="sxs-lookup"><span data-stu-id="95c96-152">X</span></span>||||<span data-ttu-id="95c96-153">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-153">N/A</span></span>|<span data-ttu-id="95c96-154">X</span><span class="sxs-lookup"><span data-stu-id="95c96-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="95c96-155">X</span><span class="sxs-lookup"><span data-stu-id="95c96-155">X</span></span>|<span data-ttu-id="95c96-156">X</span><span class="sxs-lookup"><span data-stu-id="95c96-156">X</span></span>||<span data-ttu-id="95c96-157">X</span><span class="sxs-lookup"><span data-stu-id="95c96-157">X</span></span>||<span data-ttu-id="95c96-158">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-158">N/A</span></span>|<span data-ttu-id="95c96-159">X</span><span class="sxs-lookup"><span data-stu-id="95c96-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="95c96-160">X</span><span class="sxs-lookup"><span data-stu-id="95c96-160">X</span></span>|<span data-ttu-id="95c96-161">X</span><span class="sxs-lookup"><span data-stu-id="95c96-161">X</span></span>||<span data-ttu-id="95c96-162">X</span><span class="sxs-lookup"><span data-stu-id="95c96-162">X</span></span>|<span data-ttu-id="95c96-163">X</span><span class="sxs-lookup"><span data-stu-id="95c96-163">X</span></span>|<span data-ttu-id="95c96-164">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-164">N/A</span></span>|<span data-ttu-id="95c96-165">X</span><span class="sxs-lookup"><span data-stu-id="95c96-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="95c96-166">X</span><span class="sxs-lookup"><span data-stu-id="95c96-166">X</span></span>|<span data-ttu-id="95c96-167">X</span><span class="sxs-lookup"><span data-stu-id="95c96-167">X</span></span>||<span data-ttu-id="95c96-168">X</span><span class="sxs-lookup"><span data-stu-id="95c96-168">X</span></span>|<span data-ttu-id="95c96-169">X</span><span class="sxs-lookup"><span data-stu-id="95c96-169">X</span></span>|<span data-ttu-id="95c96-170">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-170">N/A</span></span>|<span data-ttu-id="95c96-171">X</span><span class="sxs-lookup"><span data-stu-id="95c96-171">X</span></span>|  
|<span data-ttu-id="95c96-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="95c96-172">eFastExitProcess</span></span>|<span data-ttu-id="95c96-173">X</span><span class="sxs-lookup"><span data-stu-id="95c96-173">X</span></span>|<span data-ttu-id="95c96-174">X</span><span class="sxs-lookup"><span data-stu-id="95c96-174">X</span></span>||<span data-ttu-id="95c96-175">X</span><span class="sxs-lookup"><span data-stu-id="95c96-175">X</span></span>|<span data-ttu-id="95c96-176">X</span><span class="sxs-lookup"><span data-stu-id="95c96-176">X</span></span>|<span data-ttu-id="95c96-177">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="95c96-178">X</span><span class="sxs-lookup"><span data-stu-id="95c96-178">X</span></span>|<span data-ttu-id="95c96-179">X</span><span class="sxs-lookup"><span data-stu-id="95c96-179">X</span></span>|<span data-ttu-id="95c96-180">X</span><span class="sxs-lookup"><span data-stu-id="95c96-180">X</span></span>|<span data-ttu-id="95c96-181">X</span><span class="sxs-lookup"><span data-stu-id="95c96-181">X</span></span>|<span data-ttu-id="95c96-182">X</span><span class="sxs-lookup"><span data-stu-id="95c96-182">X</span></span>|<span data-ttu-id="95c96-183">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="95c96-184">X</span><span class="sxs-lookup"><span data-stu-id="95c96-184">X</span></span>|<span data-ttu-id="95c96-185">X</span><span class="sxs-lookup"><span data-stu-id="95c96-185">X</span></span>|<span data-ttu-id="95c96-186">X</span><span class="sxs-lookup"><span data-stu-id="95c96-186">X</span></span>|<span data-ttu-id="95c96-187">X</span><span class="sxs-lookup"><span data-stu-id="95c96-187">X</span></span>|<span data-ttu-id="95c96-188">X</span><span class="sxs-lookup"><span data-stu-id="95c96-188">X</span></span>|<span data-ttu-id="95c96-189">N/A</span><span class="sxs-lookup"><span data-stu-id="95c96-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="95c96-190">需求</span><span class="sxs-lookup"><span data-stu-id="95c96-190">Requirements</span></span>  

 <span data-ttu-id="95c96-191">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95c96-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c96-192">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="95c96-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95c96-193">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="95c96-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95c96-194">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c96-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c96-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95c96-195">See also</span></span>

- [<span data-ttu-id="95c96-196">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="95c96-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="95c96-197">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="95c96-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="95c96-198">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="95c96-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="95c96-199">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="95c96-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
