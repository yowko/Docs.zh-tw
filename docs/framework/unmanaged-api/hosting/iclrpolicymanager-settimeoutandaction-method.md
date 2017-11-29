---
title: "ICLRPolicyManager::SetTimeoutAndAction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeoutAndAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a15454e1cea29e3c0025797633f22e9e18554347
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="29674-102">ICLRPolicyManager::SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="29674-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="29674-103">設定指定的作業的逾時值，並指定發生作業時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="29674-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29674-104">語法</span><span class="sxs-lookup"><span data-stu-id="29674-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29674-105">參數</span><span class="sxs-lookup"><span data-stu-id="29674-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="29674-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示要設定的逾時和原則作業`action`。</span><span class="sxs-lookup"><span data-stu-id="29674-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="29674-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="29674-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="29674-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="29674-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="29674-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="29674-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="29674-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="29674-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="29674-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="29674-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="29674-112">[in]新的逾時值，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="29674-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="29674-113">值為無限原因`operation`永遠不會以逾時。</span><span class="sxs-lookup"><span data-stu-id="29674-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="29674-114">[in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，表示 CLR 應該時採取的原則動作`operation`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="29674-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29674-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="29674-115">Return Value</span></span>  
  
|<span data-ttu-id="29674-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29674-116">HRESULT</span></span>|<span data-ttu-id="29674-117">描述</span><span class="sxs-lookup"><span data-stu-id="29674-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29674-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="29674-118">S_OK</span></span>|<span data-ttu-id="29674-119">`SetTimeoutAndAction`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="29674-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="29674-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29674-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29674-121">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="29674-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29674-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29674-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29674-123">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="29674-123">The call timed out.</span></span>|  
|<span data-ttu-id="29674-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29674-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29674-125">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="29674-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29674-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29674-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29674-127">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="29674-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29674-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29674-128">E_FAIL</span></span>|<span data-ttu-id="29674-129">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="29674-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29674-130">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="29674-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29674-131">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="29674-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="29674-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="29674-132">E_INVALIDARG</span></span>|<span data-ttu-id="29674-133">無法設定逾時指定`operation`，提供無效的值或`action`。</span><span class="sxs-lookup"><span data-stu-id="29674-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29674-134">備註</span><span class="sxs-lookup"><span data-stu-id="29674-134">Remarks</span></span>  
 <span data-ttu-id="29674-135">`SetTimeoutAndAction`封裝的功能[iclrpolicymanager:: Settimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)和[iclrpolicymanager:: Setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法，而且可以取代循序呼叫這兩個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="29674-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29674-136">並非所有的原則動作值可以指定為 CLR 作業的逾時行為。</span><span class="sxs-lookup"><span data-stu-id="29674-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="29674-137">請參閱有效值這兩種方法的主題的 < 備註 > 章節。</span><span class="sxs-lookup"><span data-stu-id="29674-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29674-138">需求</span><span class="sxs-lookup"><span data-stu-id="29674-138">Requirements</span></span>  
 <span data-ttu-id="29674-139">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29674-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29674-140">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29674-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29674-141">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="29674-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29674-142">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29674-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29674-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29674-143">See Also</span></span>  
 [<span data-ttu-id="29674-144">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="29674-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="29674-145">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="29674-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="29674-146">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="29674-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="29674-147">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="29674-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)  
 [<span data-ttu-id="29674-148">Iclrpolicymanager:: Settimeoutandaction</span><span class="sxs-lookup"><span data-stu-id="29674-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
