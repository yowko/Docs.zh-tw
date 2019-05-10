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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d99f4f0615e7d25991b37030b7cb609985192f
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910675"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="3d336-102">ICLRPolicyManager::SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="3d336-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="3d336-103">指定當指定的作業逾時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="3d336-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d336-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d336-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d336-105">參數</span><span class="sxs-lookup"><span data-stu-id="3d336-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="3d336-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示用來指定逾時動作的作業。</span><span class="sxs-lookup"><span data-stu-id="3d336-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="3d336-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="3d336-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="3d336-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3d336-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="3d336-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3d336-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="3d336-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3d336-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="3d336-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3d336-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="3d336-112">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示原則所要採取動作的作業逾時。</span><span class="sxs-lookup"><span data-stu-id="3d336-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d336-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="3d336-113">Return Value</span></span>  
  
|<span data-ttu-id="3d336-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d336-114">HRESULT</span></span>|<span data-ttu-id="3d336-115">描述</span><span class="sxs-lookup"><span data-stu-id="3d336-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d336-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d336-116">S_OK</span></span>|<span data-ttu-id="3d336-117">`SetActionOnTimeout` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3d336-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="3d336-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d336-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d336-119">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3d336-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d336-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d336-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d336-121">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3d336-121">The call timed out.</span></span>|  
|<span data-ttu-id="3d336-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d336-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d336-123">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3d336-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d336-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d336-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d336-125">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3d336-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d336-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d336-126">E_FAIL</span></span>|<span data-ttu-id="3d336-127">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d336-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d336-128">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="3d336-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d336-129">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3d336-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3d336-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3d336-130">E_INVALIDARG</span></span>|<span data-ttu-id="3d336-131">無法設定逾時指定`operation`，或為無效的值提供`operation`。</span><span class="sxs-lookup"><span data-stu-id="3d336-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d336-132">備註</span><span class="sxs-lookup"><span data-stu-id="3d336-132">Remarks</span></span>  
 <span data-ttu-id="3d336-133">設定由 CLR 的預設逾時或由主機呼叫中指定的值，可以是逾時值[iclrpolicymanager:: Settimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3d336-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="3d336-134">並非所有的原則動作值可以指定為 CLR 作業的逾時行為。</span><span class="sxs-lookup"><span data-stu-id="3d336-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="3d336-135">`SetActionOnTimeout` 通常只會用於擴大的行為。</span><span class="sxs-lookup"><span data-stu-id="3d336-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="3d336-136">比方說，主機可以指定成粗略開啟執行緒中止的執行緒中止，但不能指定相反。</span><span class="sxs-lookup"><span data-stu-id="3d336-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="3d336-137">下表描述的有效`action`的值有效`operation`值。</span><span class="sxs-lookup"><span data-stu-id="3d336-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="3d336-138">值 `operation`</span><span class="sxs-lookup"><span data-stu-id="3d336-138">Value for `operation`</span></span>|<span data-ttu-id="3d336-139">有效值 `action`</span><span class="sxs-lookup"><span data-stu-id="3d336-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="3d336-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3d336-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="3d336-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3d336-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="3d336-142">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="3d336-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="3d336-143">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3d336-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3d336-144">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3d336-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3d336-145">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-145">-   eExitProcess</span></span><br /><span data-ttu-id="3d336-146">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="3d336-147">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3d336-148">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3d336-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3d336-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3d336-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="3d336-150">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3d336-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3d336-151">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3d336-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3d336-152">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-152">-   eExitProcess</span></span><br /><span data-ttu-id="3d336-153">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="3d336-154">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3d336-155">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3d336-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3d336-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3d336-156">OPR_ProcessExit</span></span>|<span data-ttu-id="3d336-157">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-157">-   eExitProcess</span></span><br /><span data-ttu-id="3d336-158">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="3d336-159">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3d336-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3d336-160">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3d336-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d336-161">需求</span><span class="sxs-lookup"><span data-stu-id="3d336-161">Requirements</span></span>  
 <span data-ttu-id="3d336-162">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d336-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d336-163">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d336-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d336-164">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3d336-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d336-165">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d336-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d336-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d336-166">See also</span></span>

- [<span data-ttu-id="3d336-167">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="3d336-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="3d336-168">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="3d336-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="3d336-169">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="3d336-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3d336-170">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="3d336-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
