---
title: ICLRPolicyManager::SetTimeout 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
ms.openlocfilehash: 516ba1325404e757af8e38de239864b21b1640f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140755"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="782e0-102">ICLRPolicyManager::SetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="782e0-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="782e0-103">設定指定之作業的超時值。</span><span class="sxs-lookup"><span data-stu-id="782e0-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="782e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="782e0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="782e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="782e0-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="782e0-106">在其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示要設定其超時時間的 common language RUNTIME （CLR）運算。</span><span class="sxs-lookup"><span data-stu-id="782e0-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="782e0-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="782e0-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="782e0-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="782e0-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="782e0-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="782e0-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="782e0-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="782e0-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="782e0-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="782e0-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="782e0-112">在新的超時值（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="782e0-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="782e0-113">無限值會導致作業永遠不會超時。</span><span class="sxs-lookup"><span data-stu-id="782e0-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="782e0-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="782e0-114">Return Value</span></span>  
  
|<span data-ttu-id="782e0-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="782e0-115">HRESULT</span></span>|<span data-ttu-id="782e0-116">描述</span><span class="sxs-lookup"><span data-stu-id="782e0-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="782e0-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="782e0-117">S_OK</span></span>|<span data-ttu-id="782e0-118">已成功傳回 `SetTimeout`。</span><span class="sxs-lookup"><span data-stu-id="782e0-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="782e0-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="782e0-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="782e0-120">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="782e0-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="782e0-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="782e0-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="782e0-122">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="782e0-122">The call timed out.</span></span>|  
|<span data-ttu-id="782e0-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="782e0-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="782e0-124">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="782e0-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="782e0-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="782e0-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="782e0-126">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="782e0-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="782e0-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="782e0-127">E_FAIL</span></span>|<span data-ttu-id="782e0-128">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="782e0-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="782e0-129">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="782e0-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="782e0-130">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="782e0-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="782e0-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="782e0-131">E_INVALIDARG</span></span>|<span data-ttu-id="782e0-132">無法為指定的 `operation`設定超時，或為 `operation`提供了不正確值。</span><span class="sxs-lookup"><span data-stu-id="782e0-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="782e0-133">需求</span><span class="sxs-lookup"><span data-stu-id="782e0-133">Requirements</span></span>  
 <span data-ttu-id="782e0-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="782e0-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="782e0-135">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="782e0-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="782e0-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="782e0-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="782e0-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="782e0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782e0-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="782e0-138">See also</span></span>

- [<span data-ttu-id="782e0-139">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="782e0-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="782e0-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="782e0-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="782e0-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="782e0-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
