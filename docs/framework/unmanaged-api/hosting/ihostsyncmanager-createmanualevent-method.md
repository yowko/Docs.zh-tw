---
title: IHostSyncManager::CreateManualEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 13679b4d40e660dfdd18e6fbafe19226b2ffda37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195861"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="91958-102">IHostSyncManager::CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="91958-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="91958-103">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="91958-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91958-104">語法</span><span class="sxs-lookup"><span data-stu-id="91958-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91958-105">參數</span><span class="sxs-lookup"><span data-stu-id="91958-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="91958-106">[in] `true`，如果物件已收到信號，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="91958-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="91958-107">脫銷[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)實例位址的指標，如果無法建立事件則為 null。</span><span class="sxs-lookup"><span data-stu-id="91958-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91958-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="91958-108">Return Value</span></span>  
  
|<span data-ttu-id="91958-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91958-109">HRESULT</span></span>|<span data-ttu-id="91958-110">描述</span><span class="sxs-lookup"><span data-stu-id="91958-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91958-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="91958-111">S_OK</span></span>|<span data-ttu-id="91958-112">已成功傳回 `CreateManualEvent`。</span><span class="sxs-lookup"><span data-stu-id="91958-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="91958-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91958-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91958-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="91958-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91958-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91958-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91958-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="91958-116">The call timed out.</span></span>|  
|<span data-ttu-id="91958-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91958-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91958-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="91958-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91958-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91958-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91958-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="91958-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91958-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91958-121">E_FAIL</span></span>|<span data-ttu-id="91958-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="91958-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91958-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="91958-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91958-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="91958-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="91958-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="91958-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="91958-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="91958-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91958-127">備註</span><span class="sxs-lookup"><span data-stu-id="91958-127">Remarks</span></span>  
 <span data-ttu-id="91958-128">`CreateManualEvent` 會建立一個 `IHostManualEvent`，這是手動重設的事件物件，需要呼叫[IHostManualEvent：： reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)方法，才能將它設定為非信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="91958-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="91958-129">`CreateManualEvent` 會使用針對 `bManualReset` 參數所指定 `true` 值來鏡像 Win32 `CreateEvent` 函數。</span><span class="sxs-lookup"><span data-stu-id="91958-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91958-130">需求</span><span class="sxs-lookup"><span data-stu-id="91958-130">Requirements</span></span>  
 <span data-ttu-id="91958-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91958-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91958-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="91958-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91958-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="91958-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91958-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91958-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91958-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="91958-135">See also</span></span>

- [<span data-ttu-id="91958-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="91958-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="91958-137">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="91958-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="91958-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="91958-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
