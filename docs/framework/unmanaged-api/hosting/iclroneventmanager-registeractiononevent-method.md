---
title: "ICLROnEventManager::RegisterActionOnEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 008bdc856c9fbede7398f467674ac191c1860128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="97fc9-102">ICLROnEventManager::RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="97fc9-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="97fc9-103">註冊指定的事件的回呼指標。</span><span class="sxs-lookup"><span data-stu-id="97fc9-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fc9-104">語法</span><span class="sxs-lookup"><span data-stu-id="97fc9-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97fc9-105">參數</span><span class="sxs-lookup"><span data-stu-id="97fc9-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="97fc9-106">[in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，表示其註冊回呼指標所描述的事件`pAction`。</span><span class="sxs-lookup"><span data-stu-id="97fc9-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="97fc9-107">[in]指標[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)已註冊的事件引發時呼叫的物件。</span><span class="sxs-lookup"><span data-stu-id="97fc9-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97fc9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="97fc9-108">Return Value</span></span>  
  
|<span data-ttu-id="97fc9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97fc9-109">HRESULT</span></span>|<span data-ttu-id="97fc9-110">描述</span><span class="sxs-lookup"><span data-stu-id="97fc9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97fc9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="97fc9-111">S_OK</span></span>|<span data-ttu-id="97fc9-112">`RegisterActionOnEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="97fc9-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="97fc9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97fc9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97fc9-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="97fc9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97fc9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97fc9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97fc9-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="97fc9-116">The call timed out.</span></span>|  
|<span data-ttu-id="97fc9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97fc9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97fc9-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="97fc9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97fc9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97fc9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97fc9-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="97fc9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97fc9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97fc9-121">E_FAIL</span></span>|<span data-ttu-id="97fc9-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="97fc9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97fc9-123">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="97fc9-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97fc9-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="97fc9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97fc9-125">備註</span><span class="sxs-lookup"><span data-stu-id="97fc9-125">Remarks</span></span>  
 <span data-ttu-id="97fc9-126">主機可以註冊回呼的一個或兩個所描述的兩個事件類型`EClrEvent`。</span><span class="sxs-lookup"><span data-stu-id="97fc9-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="97fc9-127">取得主機`ICLROnEventManager`介面，藉由呼叫[iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="97fc9-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97fc9-128">事件的`RegisterActionOnEvent`可以引發暫存器，一次以上，從不同的執行緒，以便通知卸載或 CLR 的停用。</span><span class="sxs-lookup"><span data-stu-id="97fc9-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fc9-129">需求</span><span class="sxs-lookup"><span data-stu-id="97fc9-129">Requirements</span></span>  
 <span data-ttu-id="97fc9-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97fc9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97fc9-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97fc9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97fc9-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="97fc9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97fc9-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97fc9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fc9-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="97fc9-134">See Also</span></span>  
 [<span data-ttu-id="97fc9-135">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="97fc9-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="97fc9-136">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="97fc9-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="97fc9-137">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="97fc9-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="97fc9-138">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="97fc9-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
