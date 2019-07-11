---
title: ICLRPolicyManager::SetTimeoutAndAction 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58c14dbc11272a40de01140db72ac3605bfbc67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757254"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="198ee-102">ICLRPolicyManager::SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="198ee-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="198ee-103">設定指定之作業的逾時值，並指定發生作業時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="198ee-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="198ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="198ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="198ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="198ee-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="198ee-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示要設定的逾時和原則作業`action`。</span><span class="sxs-lookup"><span data-stu-id="198ee-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="198ee-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="198ee-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="198ee-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="198ee-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="198ee-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="198ee-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="198ee-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="198ee-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="198ee-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="198ee-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="198ee-112">[in]新逾時值，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="198ee-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="198ee-113">值是無限的可能原因`operation`永遠不會以逾時。</span><span class="sxs-lookup"><span data-stu-id="198ee-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="198ee-114">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示 CLR 應該時採取的原則動作`operation`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="198ee-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="198ee-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="198ee-115">Return Value</span></span>  
  
|<span data-ttu-id="198ee-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="198ee-116">HRESULT</span></span>|<span data-ttu-id="198ee-117">說明</span><span class="sxs-lookup"><span data-stu-id="198ee-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="198ee-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="198ee-118">S_OK</span></span>|<span data-ttu-id="198ee-119">`SetTimeoutAndAction` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="198ee-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="198ee-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="198ee-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="198ee-121">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="198ee-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="198ee-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="198ee-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="198ee-123">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="198ee-123">The call timed out.</span></span>|  
|<span data-ttu-id="198ee-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="198ee-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="198ee-125">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="198ee-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="198ee-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="198ee-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="198ee-127">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="198ee-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="198ee-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="198ee-128">E_FAIL</span></span>|<span data-ttu-id="198ee-129">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="198ee-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="198ee-130">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="198ee-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="198ee-131">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="198ee-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="198ee-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="198ee-132">E_INVALIDARG</span></span>|<span data-ttu-id="198ee-133">無法設定逾時指定`operation`，或為無效的值提供`action`。</span><span class="sxs-lookup"><span data-stu-id="198ee-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="198ee-134">備註</span><span class="sxs-lookup"><span data-stu-id="198ee-134">Remarks</span></span>  
 <span data-ttu-id="198ee-135">`SetTimeoutAndAction` 封裝的功能[iclrpolicymanager:: Settimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)並[iclrpolicymanager:: Setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法，並可取代循序呼叫這兩個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="198ee-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="198ee-136">並非所有的原則動作值可以指定為 CLR 作業的逾時行為。</span><span class="sxs-lookup"><span data-stu-id="198ee-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="198ee-137">請參閱 < 備註 > 一節，有效值這兩種方法的主題。</span><span class="sxs-lookup"><span data-stu-id="198ee-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="198ee-138">需求</span><span class="sxs-lookup"><span data-stu-id="198ee-138">Requirements</span></span>  
 <span data-ttu-id="198ee-139">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="198ee-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="198ee-140">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="198ee-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="198ee-141">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="198ee-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="198ee-142">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="198ee-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198ee-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="198ee-143">See also</span></span>

- [<span data-ttu-id="198ee-144">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="198ee-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="198ee-145">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="198ee-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="198ee-146">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="198ee-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="198ee-147">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="198ee-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="198ee-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="198ee-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
