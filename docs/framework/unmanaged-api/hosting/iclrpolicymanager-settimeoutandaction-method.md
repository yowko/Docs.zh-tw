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
ms.openlocfilehash: 41e13e20a1cf5a7000907b1cc7d8d2af5174ceba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728965"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="951e9-102">ICLRPolicyManager::SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="951e9-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>

<span data-ttu-id="951e9-103">設定指定之作業的超時值，並指定 common language runtime (CLR) 在作業發生時應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="951e9-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="951e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="951e9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="951e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="951e9-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="951e9-106">在其中一個 [EClrOperation](eclroperation-enumeration.md) 值，表示要設定其 timeout 和原則的作業 `action` 。</span><span class="sxs-lookup"><span data-stu-id="951e9-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="951e9-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="951e9-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="951e9-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="951e9-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="951e9-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="951e9-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="951e9-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="951e9-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="951e9-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="951e9-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="951e9-112">在新的超時值（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="951e9-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="951e9-113">無限期的值會導致 `operation` 永遠沒有時間。</span><span class="sxs-lookup"><span data-stu-id="951e9-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="951e9-114">在其中一個 [EPolicyAction](epolicyaction-enumeration.md) 值，表示 CLR 在發生時應採取的原則動作 `operation` 。</span><span class="sxs-lookup"><span data-stu-id="951e9-114">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="951e9-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="951e9-115">Return Value</span></span>  
  
|<span data-ttu-id="951e9-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="951e9-116">HRESULT</span></span>|<span data-ttu-id="951e9-117">描述</span><span class="sxs-lookup"><span data-stu-id="951e9-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="951e9-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="951e9-118">S_OK</span></span>|<span data-ttu-id="951e9-119">`SetTimeoutAndAction` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="951e9-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="951e9-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="951e9-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="951e9-121">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="951e9-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="951e9-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="951e9-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="951e9-123">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="951e9-123">The call timed out.</span></span>|  
|<span data-ttu-id="951e9-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="951e9-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="951e9-125">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="951e9-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="951e9-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="951e9-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="951e9-127">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="951e9-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="951e9-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="951e9-128">E_FAIL</span></span>|<span data-ttu-id="951e9-129">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="951e9-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="951e9-130">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="951e9-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="951e9-131">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="951e9-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="951e9-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="951e9-132">E_INVALIDARG</span></span>|<span data-ttu-id="951e9-133">無法針對指定的設定 timeout `operation` ，或為提供的值無效 `action` 。</span><span class="sxs-lookup"><span data-stu-id="951e9-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="951e9-134">備註</span><span class="sxs-lookup"><span data-stu-id="951e9-134">Remarks</span></span>  

 <span data-ttu-id="951e9-135">`SetTimeoutAndAction` 封裝 [ICLRPolicyManager：： SetTimeout](iclrpolicymanager-settimeout-method.md) 和 [ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) 方法的功能，並可呼叫這兩個方法來取代順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="951e9-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="951e9-136">並非所有的原則動作值都可以指定為 CLR 作業的超時行為。</span><span class="sxs-lookup"><span data-stu-id="951e9-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="951e9-137">請參閱這兩個方法中有效值的備註章節。</span><span class="sxs-lookup"><span data-stu-id="951e9-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="951e9-138">需求</span><span class="sxs-lookup"><span data-stu-id="951e9-138">Requirements</span></span>  

 <span data-ttu-id="951e9-139">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="951e9-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="951e9-140">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="951e9-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="951e9-141">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="951e9-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="951e9-142">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="951e9-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951e9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="951e9-143">See also</span></span>

- [<span data-ttu-id="951e9-144">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="951e9-144">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="951e9-145">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="951e9-145">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="951e9-146">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="951e9-146">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="951e9-147">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="951e9-147">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="951e9-148">ICLRPolicyManager：： SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="951e9-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
