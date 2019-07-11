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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9c2ebb2bc9c1137a4e3716d98387278959f77d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757327"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="aaada-102">ICLRPolicyManager::SetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="aaada-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="aaada-103">設定指定之作業的逾時值。</span><span class="sxs-lookup"><span data-stu-id="aaada-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaada-104">語法</span><span class="sxs-lookup"><span data-stu-id="aaada-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaada-105">參數</span><span class="sxs-lookup"><span data-stu-id="aaada-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="aaada-106">[in]其中一個[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，表示要設定逾時的常見語言執行平台 (CLR) 作業。</span><span class="sxs-lookup"><span data-stu-id="aaada-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="aaada-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="aaada-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="aaada-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="aaada-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="aaada-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="aaada-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="aaada-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="aaada-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="aaada-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="aaada-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="aaada-112">[in]新逾時值，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="aaada-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="aaada-113">無限的值會導致作業永遠不會逾時。</span><span class="sxs-lookup"><span data-stu-id="aaada-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaada-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="aaada-114">Return Value</span></span>  
  
|<span data-ttu-id="aaada-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aaada-115">HRESULT</span></span>|<span data-ttu-id="aaada-116">描述</span><span class="sxs-lookup"><span data-stu-id="aaada-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaada-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="aaada-117">S_OK</span></span>|<span data-ttu-id="aaada-118">`SetTimeout` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="aaada-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="aaada-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aaada-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aaada-120">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="aaada-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aaada-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aaada-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aaada-122">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="aaada-122">The call timed out.</span></span>|  
|<span data-ttu-id="aaada-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aaada-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aaada-124">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="aaada-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aaada-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aaada-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aaada-126">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="aaada-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aaada-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aaada-127">E_FAIL</span></span>|<span data-ttu-id="aaada-128">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="aaada-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aaada-129">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="aaada-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aaada-130">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="aaada-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aaada-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="aaada-131">E_INVALIDARG</span></span>|<span data-ttu-id="aaada-132">無法設定逾時指定`operation`，或為無效的值提供`operation`。</span><span class="sxs-lookup"><span data-stu-id="aaada-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aaada-133">需求</span><span class="sxs-lookup"><span data-stu-id="aaada-133">Requirements</span></span>  
 <span data-ttu-id="aaada-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aaada-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaada-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aaada-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aaada-136">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="aaada-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aaada-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaada-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaada-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaada-138">See also</span></span>

- [<span data-ttu-id="aaada-139">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="aaada-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="aaada-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="aaada-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="aaada-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="aaada-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
