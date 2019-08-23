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
ms.openlocfilehash: 120dbfdc463a7441cce8ca7d87561998a8e28eda
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916958"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="95e5f-102">ICLRPolicyManager::SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="95e5f-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="95e5f-103">設定指定之作業的超時值, 並指定當作業發生時, common language runtime (CLR) 應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="95e5f-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="95e5f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95e5f-105">參數</span><span class="sxs-lookup"><span data-stu-id="95e5f-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="95e5f-106">在其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值, 表示要設定其超時和原則`action`的作業。</span><span class="sxs-lookup"><span data-stu-id="95e5f-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="95e5f-107">支援下列值:</span><span class="sxs-lookup"><span data-stu-id="95e5f-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="95e5f-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="95e5f-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="95e5f-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="95e5f-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="95e5f-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="95e5f-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="95e5f-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="95e5f-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="95e5f-112">在新的超時值 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="95e5f-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="95e5f-113">無限值會導致`operation`永遠不會超時。</span><span class="sxs-lookup"><span data-stu-id="95e5f-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="95e5f-114">在其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值, 表示 CLR 在發生時`operation`應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="95e5f-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95e5f-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="95e5f-115">Return Value</span></span>  
  
|<span data-ttu-id="95e5f-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95e5f-116">HRESULT</span></span>|<span data-ttu-id="95e5f-117">說明</span><span class="sxs-lookup"><span data-stu-id="95e5f-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95e5f-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="95e5f-118">S_OK</span></span>|<span data-ttu-id="95e5f-119">`SetTimeoutAndAction`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="95e5f-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="95e5f-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95e5f-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95e5f-121">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="95e5f-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95e5f-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95e5f-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95e5f-123">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="95e5f-123">The call timed out.</span></span>|  
|<span data-ttu-id="95e5f-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95e5f-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95e5f-125">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="95e5f-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95e5f-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95e5f-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95e5f-127">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="95e5f-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95e5f-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95e5f-128">E_FAIL</span></span>|<span data-ttu-id="95e5f-129">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="95e5f-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95e5f-130">在方法傳回 E_FAIL 之後, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="95e5f-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95e5f-131">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="95e5f-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95e5f-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="95e5f-132">E_INVALIDARG</span></span>|<span data-ttu-id="95e5f-133">無法為指定`operation`的設定超時, 或為`action`提供了不正確值。</span><span class="sxs-lookup"><span data-stu-id="95e5f-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95e5f-134">備註</span><span class="sxs-lookup"><span data-stu-id="95e5f-134">Remarks</span></span>  
 <span data-ttu-id="95e5f-135">`SetTimeoutAndAction`封裝[ICLRPolicyManager:: SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)和[ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法的功能, 而且可以呼叫這兩個方法的連續呼叫來取代。</span><span class="sxs-lookup"><span data-stu-id="95e5f-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="95e5f-136">並非所有的原則動作值都可以指定為 CLR 作業的超時行為。</span><span class="sxs-lookup"><span data-stu-id="95e5f-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="95e5f-137">如需有效值的這兩個方法, 請參閱主題的「備註」小節。</span><span class="sxs-lookup"><span data-stu-id="95e5f-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95e5f-138">需求</span><span class="sxs-lookup"><span data-stu-id="95e5f-138">Requirements</span></span>  
 <span data-ttu-id="95e5f-139">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95e5f-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e5f-140">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95e5f-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95e5f-141">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95e5f-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95e5f-142">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e5f-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e5f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e5f-143">See also</span></span>

- [<span data-ttu-id="95e5f-144">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="95e5f-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="95e5f-145">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="95e5f-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="95e5f-146">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="95e5f-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="95e5f-147">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="95e5f-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="95e5f-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="95e5f-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
