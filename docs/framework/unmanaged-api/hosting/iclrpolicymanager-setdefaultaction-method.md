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
ms.openlocfilehash: c0d8b66c8b85710b0365bfc410188c81431720ff
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703445"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="7b290-102">ICLRPolicyManager::SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="7b290-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="7b290-103">指定當發生指定的作業時，common language runtime （CLR）應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="7b290-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b290-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b290-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b290-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b290-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="7b290-106">在其中一個[EClrOperation](eclroperation-enumeration.md)值，表示應自訂 CLR 行為的動作。</span><span class="sxs-lookup"><span data-stu-id="7b290-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="7b290-107">在其中一個[EPolicyAction](epolicyaction-enumeration.md)值，表示 CLR 在發生時應採取的原則動作 `operation` 。</span><span class="sxs-lookup"><span data-stu-id="7b290-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b290-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7b290-108">Return Value</span></span>  
  
|<span data-ttu-id="7b290-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b290-109">HRESULT</span></span>|<span data-ttu-id="7b290-110">說明</span><span class="sxs-lookup"><span data-stu-id="7b290-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b290-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b290-111">S_OK</span></span>|<span data-ttu-id="7b290-112">`SetDefaultAction`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7b290-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="7b290-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b290-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b290-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7b290-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b290-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b290-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b290-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="7b290-116">The call timed out.</span></span>|  
|<span data-ttu-id="7b290-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b290-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b290-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7b290-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b290-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b290-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b290-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="7b290-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b290-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b290-121">E_FAIL</span></span>|<span data-ttu-id="7b290-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7b290-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b290-123">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="7b290-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b290-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7b290-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7b290-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7b290-125">E_INVALIDARG</span></span>|<span data-ttu-id="7b290-126">`action`為指定了不正確 `operation` ，或為提供了不正確值 `operation` 。</span><span class="sxs-lookup"><span data-stu-id="7b290-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b290-127">備註</span><span class="sxs-lookup"><span data-stu-id="7b290-127">Remarks</span></span>  
 <span data-ttu-id="7b290-128">並非所有的原則動作值都可以指定為 CLR 作業的預設行為。</span><span class="sxs-lookup"><span data-stu-id="7b290-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="7b290-129">`SetDefaultAction`通常只能用來呈報行為。</span><span class="sxs-lookup"><span data-stu-id="7b290-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="7b290-130">例如，主機可以指定執行緒中止會變成強制執行緒中止，但無法指定相反的。</span><span class="sxs-lookup"><span data-stu-id="7b290-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="7b290-131">下表描述 `action` 每個可能值的有效值 `operation` 。</span><span class="sxs-lookup"><span data-stu-id="7b290-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="7b290-132">的值`operation`</span><span class="sxs-lookup"><span data-stu-id="7b290-132">Value for `operation`</span></span>|<span data-ttu-id="7b290-133">有效的值`action`</span><span class="sxs-lookup"><span data-stu-id="7b290-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="7b290-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="7b290-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="7b290-135">- eAbortThread</span><span class="sxs-lookup"><span data-stu-id="7b290-135">-   eAbortThread</span></span><br /><span data-ttu-id="7b290-136">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="7b290-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="7b290-137">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-138">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-139">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-139">-   eExitProcess</span></span><br /><span data-ttu-id="7b290-140">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="7b290-141">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7b290-142">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7b290-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7b290-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7b290-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="7b290-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7b290-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="7b290-145">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="7b290-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="7b290-146">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-147">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-148">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-148">-   eExitProcess</span></span><br /><span data-ttu-id="7b290-149">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="7b290-150">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7b290-151">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7b290-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7b290-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="7b290-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="7b290-153">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-154">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-155">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-155">-   eExitProcess</span></span><br /><span data-ttu-id="7b290-156">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="7b290-157">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7b290-158">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7b290-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7b290-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="7b290-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="7b290-160">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-161">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-161">-   eExitProcess</span></span><br /><span data-ttu-id="7b290-162">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="7b290-163">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7b290-164">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7b290-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7b290-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="7b290-165">OPR_ProcessExit</span></span>|<span data-ttu-id="7b290-166">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-166">-   eExitProcess</span></span><br /><span data-ttu-id="7b290-167">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="7b290-168">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7b290-169">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7b290-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="7b290-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="7b290-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="7b290-171">- eNoAction</span><span class="sxs-lookup"><span data-stu-id="7b290-171">-   eNoAction</span></span><br /><span data-ttu-id="7b290-172">- eAbortThread</span><span class="sxs-lookup"><span data-stu-id="7b290-172">-   eAbortThread</span></span><br /><span data-ttu-id="7b290-173">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="7b290-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="7b290-174">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-175">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="7b290-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="7b290-176">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-176">-   eExitProcess</span></span><br /><span data-ttu-id="7b290-177">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="7b290-178">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="7b290-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="7b290-179">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="7b290-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b290-180">需求</span><span class="sxs-lookup"><span data-stu-id="7b290-180">Requirements</span></span>  
 <span data-ttu-id="7b290-181">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b290-181">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b290-182">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7b290-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b290-183">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7b290-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b290-184">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b290-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b290-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b290-185">See also</span></span>

- [<span data-ttu-id="7b290-186">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="7b290-186">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="7b290-187">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="7b290-187">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="7b290-188">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="7b290-188">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
