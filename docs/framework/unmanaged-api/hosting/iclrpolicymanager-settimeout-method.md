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
ms.openlocfilehash: b3e66a1e04ca3f3031adf1f0f7f71d689ee76b04
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703414"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="6e466-102">ICLRPolicyManager::SetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="6e466-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="6e466-103">設定指定之作業的超時值。</span><span class="sxs-lookup"><span data-stu-id="6e466-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e466-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e466-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e466-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e466-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="6e466-106">在其中一個[EClrOperation](eclroperation-enumeration.md)值，表示要設定其超時時間的 common language RUNTIME （CLR）運算。</span><span class="sxs-lookup"><span data-stu-id="6e466-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="6e466-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="6e466-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="6e466-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="6e466-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="6e466-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="6e466-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="6e466-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="6e466-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="6e466-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="6e466-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="6e466-112">在新的超時值（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="6e466-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="6e466-113">無限值會導致作業永遠不會超時。</span><span class="sxs-lookup"><span data-stu-id="6e466-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e466-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="6e466-114">Return Value</span></span>  
  
|<span data-ttu-id="6e466-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e466-115">HRESULT</span></span>|<span data-ttu-id="6e466-116">說明</span><span class="sxs-lookup"><span data-stu-id="6e466-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e466-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e466-117">S_OK</span></span>|<span data-ttu-id="6e466-118">`SetTimeout`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6e466-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="6e466-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e466-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e466-120">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6e466-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e466-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e466-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e466-122">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="6e466-122">The call timed out.</span></span>|  
|<span data-ttu-id="6e466-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e466-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e466-124">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6e466-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e466-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e466-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e466-126">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="6e466-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e466-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e466-127">E_FAIL</span></span>|<span data-ttu-id="6e466-128">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6e466-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e466-129">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="6e466-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e466-130">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6e466-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6e466-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6e466-131">E_INVALIDARG</span></span>|<span data-ttu-id="6e466-132">無法為指定的設定超時 `operation` ，或為提供了不正確值 `operation` 。</span><span class="sxs-lookup"><span data-stu-id="6e466-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e466-133">需求</span><span class="sxs-lookup"><span data-stu-id="6e466-133">Requirements</span></span>  
 <span data-ttu-id="6e466-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e466-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e466-135">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6e466-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e466-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6e466-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e466-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e466-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e466-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e466-138">See also</span></span>

- [<span data-ttu-id="6e466-139">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="6e466-139">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="6e466-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="6e466-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="6e466-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="6e466-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
