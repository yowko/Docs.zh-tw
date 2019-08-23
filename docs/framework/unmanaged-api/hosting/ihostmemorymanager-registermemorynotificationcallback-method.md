---
title: IHostMemoryManager::RegisterMemoryNotificationCallback 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34701642a9e76ec52141e00fe9dde92878faccd2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945441"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="ef336-102">IHostMemoryManager::RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="ef336-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="ef336-103">註冊主機所叫用的回呼函式指標, 以通知 common language runtime (CLR) 目前在電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="ef336-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef336-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef336-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef336-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef336-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="ef336-106">在CLR 所執行之[ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ef336-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef336-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ef336-107">Return Value</span></span>  
  
|<span data-ttu-id="ef336-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef336-108">HRESULT</span></span>|<span data-ttu-id="ef336-109">說明</span><span class="sxs-lookup"><span data-stu-id="ef336-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef336-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef336-110">S_OK</span></span>|<span data-ttu-id="ef336-111">`RegisterMemoryNotificationCallback`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ef336-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="ef336-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef336-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef336-113">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ef336-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef336-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef336-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef336-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="ef336-115">The call timed out.</span></span>|  
|<span data-ttu-id="ef336-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef336-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef336-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ef336-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef336-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef336-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef336-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="ef336-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef336-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef336-120">E_FAIL</span></span>|<span data-ttu-id="ef336-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ef336-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef336-122">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="ef336-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef336-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ef336-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef336-124">備註</span><span class="sxs-lookup"><span data-stu-id="ef336-124">Remarks</span></span>  
 <span data-ttu-id="ef336-125">因為介面只會定義一個方法 ([ICLRMemoryNotificationCallback:: OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), 而且因為`pCallback`是 CLR 提供之`ICLRMemoryNotificationCallback`實例的指標, 所以有效註冊的目的是`ICLRMemoryNotificationCallback`回呼函式本身。</span><span class="sxs-lookup"><span data-stu-id="ef336-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="ef336-126">主機`OnMemoryNotification`會叫用來報告記憶體壓力條件, 而不是使用標準`CreateMemoryResourceNotification`的 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="ef336-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="ef336-127">如需詳細資訊, 請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="ef336-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef336-128">`OnMemoryNotification`從不封鎖的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ef336-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="ef336-129">它們一律會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="ef336-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef336-130">需求</span><span class="sxs-lookup"><span data-stu-id="ef336-130">Requirements</span></span>  
 <span data-ttu-id="ef336-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef336-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef336-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef336-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef336-133">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ef336-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef336-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef336-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef336-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef336-135">See also</span></span>

- [<span data-ttu-id="ef336-136">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ef336-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="ef336-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="ef336-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
