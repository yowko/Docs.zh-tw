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
ms.openlocfilehash: 68a8493a9eb5177844e81ef7a9612f979ffe89c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638550"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="dfde1-102">ICLROnEventManager::RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="dfde1-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="dfde1-103">註冊指定的事件的回呼指標。</span><span class="sxs-lookup"><span data-stu-id="dfde1-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfde1-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfde1-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfde1-105">參數</span><span class="sxs-lookup"><span data-stu-id="dfde1-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="dfde1-106">[in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，表示要註冊回呼指標所描述的事件`pAction`。</span><span class="sxs-lookup"><span data-stu-id="dfde1-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="dfde1-107">[in]指標[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)已註冊的事件引發時呼叫的物件。</span><span class="sxs-lookup"><span data-stu-id="dfde1-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfde1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="dfde1-108">Return Value</span></span>  
  
|<span data-ttu-id="dfde1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfde1-109">HRESULT</span></span>|<span data-ttu-id="dfde1-110">描述</span><span class="sxs-lookup"><span data-stu-id="dfde1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfde1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfde1-111">S_OK</span></span>|<span data-ttu-id="dfde1-112">`RegisterActionOnEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dfde1-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="dfde1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfde1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfde1-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="dfde1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfde1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfde1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfde1-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dfde1-116">The call timed out.</span></span>|  
|<span data-ttu-id="dfde1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfde1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfde1-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dfde1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfde1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfde1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfde1-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dfde1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfde1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfde1-121">E_FAIL</span></span>|<span data-ttu-id="dfde1-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="dfde1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dfde1-123">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="dfde1-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfde1-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dfde1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfde1-125">備註</span><span class="sxs-lookup"><span data-stu-id="dfde1-125">Remarks</span></span>  
 <span data-ttu-id="dfde1-126">主機可以註冊的一個或兩個所描述的兩個事件類型的回呼`EClrEvent`。</span><span class="sxs-lookup"><span data-stu-id="dfde1-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="dfde1-127">取得主機`ICLROnEventManager`介面，藉由呼叫[iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="dfde1-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfde1-128">事件的`RegisterActionOnEvent`可以引發暫存器，一次以上，並從不同的執行緒，以表示卸載或 CLR 的停用。</span><span class="sxs-lookup"><span data-stu-id="dfde1-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfde1-129">需求</span><span class="sxs-lookup"><span data-stu-id="dfde1-129">Requirements</span></span>  
 <span data-ttu-id="dfde1-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfde1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfde1-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfde1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfde1-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dfde1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfde1-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfde1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfde1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfde1-134">See also</span></span>

- [<span data-ttu-id="dfde1-135">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="dfde1-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="dfde1-136">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="dfde1-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="dfde1-137">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="dfde1-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="dfde1-138">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="dfde1-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
