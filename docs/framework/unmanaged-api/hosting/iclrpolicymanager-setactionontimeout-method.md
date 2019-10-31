---
title: ICLRPolicyManager::SetActionOnTimeout 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 9ef906ed5e8a6985c084741bf06b683da79c546e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140798"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="a95e7-102">ICLRPolicyManager::SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="a95e7-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="a95e7-103">指定當指定的作業超時時，common language runtime （CLR）應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="a95e7-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="a95e7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a95e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="a95e7-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a95e7-106">在其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示要指定其超時動作的作業。</span><span class="sxs-lookup"><span data-stu-id="a95e7-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="a95e7-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="a95e7-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="a95e7-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a95e7-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="a95e7-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a95e7-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="a95e7-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a95e7-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="a95e7-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a95e7-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="a95e7-112">在其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示作業超時時要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="a95e7-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a95e7-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="a95e7-113">Return Value</span></span>  
  
|<span data-ttu-id="a95e7-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a95e7-114">HRESULT</span></span>|<span data-ttu-id="a95e7-115">描述</span><span class="sxs-lookup"><span data-stu-id="a95e7-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a95e7-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a95e7-116">S_OK</span></span>|<span data-ttu-id="a95e7-117">已成功傳回 `SetActionOnTimeout`。</span><span class="sxs-lookup"><span data-stu-id="a95e7-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="a95e7-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a95e7-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a95e7-119">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a95e7-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a95e7-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a95e7-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a95e7-121">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a95e7-121">The call timed out.</span></span>|  
|<span data-ttu-id="a95e7-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a95e7-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a95e7-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a95e7-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a95e7-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a95e7-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a95e7-125">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a95e7-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a95e7-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a95e7-126">E_FAIL</span></span>|<span data-ttu-id="a95e7-127">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a95e7-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a95e7-128">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="a95e7-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a95e7-129">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a95e7-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a95e7-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a95e7-130">E_INVALIDARG</span></span>|<span data-ttu-id="a95e7-131">無法為指定的 `operation`設定超時，或為 `operation`提供了不正確值。</span><span class="sxs-lookup"><span data-stu-id="a95e7-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a95e7-132">備註</span><span class="sxs-lookup"><span data-stu-id="a95e7-132">Remarks</span></span>  
 <span data-ttu-id="a95e7-133">Timeout 值可以是 CLR 所設定的預設超時時間，或是由主機在[ICLRPolicyManager：： SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)方法的呼叫中所指定的值。</span><span class="sxs-lookup"><span data-stu-id="a95e7-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="a95e7-134">並非所有的原則動作值都可以指定為 CLR 作業的超時行為。</span><span class="sxs-lookup"><span data-stu-id="a95e7-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="a95e7-135">`SetActionOnTimeout` 通常僅用於呈報行為。</span><span class="sxs-lookup"><span data-stu-id="a95e7-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="a95e7-136">例如，主機可以指定執行緒中止會變成強制執行緒中止，但無法指定相反的。</span><span class="sxs-lookup"><span data-stu-id="a95e7-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="a95e7-137">下表描述有效 `operation` 值的有效 `action` 值。</span><span class="sxs-lookup"><span data-stu-id="a95e7-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="a95e7-138">`operation` 的值</span><span class="sxs-lookup"><span data-stu-id="a95e7-138">Value for `operation`</span></span>|<span data-ttu-id="a95e7-139">`action` 的有效值</span><span class="sxs-lookup"><span data-stu-id="a95e7-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="a95e7-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a95e7-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="a95e7-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a95e7-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="a95e7-142">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="a95e7-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="a95e7-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a95e7-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a95e7-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a95e7-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a95e7-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-145">-   eExitProcess</span></span><br /><span data-ttu-id="a95e7-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="a95e7-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a95e7-148">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a95e7-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a95e7-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a95e7-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="a95e7-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a95e7-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a95e7-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a95e7-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a95e7-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-152">-   eExitProcess</span></span><br /><span data-ttu-id="a95e7-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="a95e7-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a95e7-155">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a95e7-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a95e7-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a95e7-156">OPR_ProcessExit</span></span>|<span data-ttu-id="a95e7-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-157">-   eExitProcess</span></span><br /><span data-ttu-id="a95e7-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="a95e7-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a95e7-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a95e7-160">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a95e7-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a95e7-161">需求</span><span class="sxs-lookup"><span data-stu-id="a95e7-161">Requirements</span></span>  
 <span data-ttu-id="a95e7-162">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a95e7-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a95e7-163">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a95e7-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a95e7-164">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a95e7-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a95e7-165">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a95e7-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95e7-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="a95e7-166">See also</span></span>

- [<span data-ttu-id="a95e7-167">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="a95e7-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="a95e7-168">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="a95e7-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="a95e7-169">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="a95e7-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a95e7-170">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="a95e7-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
