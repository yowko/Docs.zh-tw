---
title: ICLROnEventManager::RegisterActionOnEvent 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36d4b0692b112a66fea3dd878c7054a083fb68ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951140"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="e89e4-102">ICLROnEventManager::RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="e89e4-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="e89e4-103">為指定的事件註冊回呼指標。</span><span class="sxs-lookup"><span data-stu-id="e89e4-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="e89e4-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e89e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="e89e4-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="e89e4-106">在其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值, 表示要註冊其所描述`pAction`之回呼指標的事件。</span><span class="sxs-lookup"><span data-stu-id="e89e4-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="e89e4-107">在當註冊的事件引發時, 所呼叫之[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="e89e4-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e89e4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e89e4-108">Return Value</span></span>  
  
|<span data-ttu-id="e89e4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e89e4-109">HRESULT</span></span>|<span data-ttu-id="e89e4-110">說明</span><span class="sxs-lookup"><span data-stu-id="e89e4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e89e4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e89e4-111">S_OK</span></span>|<span data-ttu-id="e89e4-112">`RegisterActionOnEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e89e4-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e89e4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e89e4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e89e4-114">Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e89e4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e89e4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e89e4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e89e4-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e89e4-116">The call timed out.</span></span>|  
|<span data-ttu-id="e89e4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e89e4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e89e4-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e89e4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e89e4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e89e4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e89e4-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e89e4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e89e4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e89e4-121">E_FAIL</span></span>|<span data-ttu-id="e89e4-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e89e4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e89e4-123">在方法傳回 E_FAIL 之後, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="e89e4-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e89e4-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e89e4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e89e4-125">備註</span><span class="sxs-lookup"><span data-stu-id="e89e4-125">Remarks</span></span>  
 <span data-ttu-id="e89e4-126">主機可以為所描述`EClrEvent`的兩個事件種類的其中一個或兩個註冊回呼。</span><span class="sxs-lookup"><span data-stu-id="e89e4-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="e89e4-127">主機會藉由`ICLROnEventManager`呼叫[ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法來取得介面。</span><span class="sxs-lookup"><span data-stu-id="e89e4-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e89e4-128">`RegisterActionOnEvent`註冊的事件可以引發一次以上, 並從不同的執行緒發出, 以表示卸載或停用 CLR。</span><span class="sxs-lookup"><span data-stu-id="e89e4-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e89e4-129">需求</span><span class="sxs-lookup"><span data-stu-id="e89e4-129">Requirements</span></span>  
 <span data-ttu-id="e89e4-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e89e4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e89e4-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e89e4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e89e4-132">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e89e4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e89e4-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e89e4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89e4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e89e4-134">See also</span></span>

- [<span data-ttu-id="e89e4-135">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="e89e4-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="e89e4-136">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="e89e4-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="e89e4-137">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="e89e4-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e89e4-138">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="e89e4-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
