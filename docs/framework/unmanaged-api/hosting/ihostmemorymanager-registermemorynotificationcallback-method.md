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
ms.openlocfilehash: 4400fab27ed82e540230ce4196844285e8e37d16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128641"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="79251-102">IHostMemoryManager::RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="79251-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="79251-103">註冊主機所叫用的回呼函式指標，以通知 common language runtime （CLR）目前在電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="79251-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79251-104">語法</span><span class="sxs-lookup"><span data-stu-id="79251-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79251-105">參數</span><span class="sxs-lookup"><span data-stu-id="79251-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="79251-106">在CLR 所執行之[ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="79251-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79251-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="79251-107">Return Value</span></span>  
  
|<span data-ttu-id="79251-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79251-108">HRESULT</span></span>|<span data-ttu-id="79251-109">描述</span><span class="sxs-lookup"><span data-stu-id="79251-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79251-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="79251-110">S_OK</span></span>|<span data-ttu-id="79251-111">已成功傳回 `RegisterMemoryNotificationCallback`。</span><span class="sxs-lookup"><span data-stu-id="79251-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="79251-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79251-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79251-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="79251-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79251-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79251-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79251-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="79251-115">The call timed out.</span></span>|  
|<span data-ttu-id="79251-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79251-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79251-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="79251-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79251-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79251-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79251-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="79251-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79251-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79251-120">E_FAIL</span></span>|<span data-ttu-id="79251-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="79251-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79251-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="79251-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79251-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="79251-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79251-124">備註</span><span class="sxs-lookup"><span data-stu-id="79251-124">Remarks</span></span>  
 <span data-ttu-id="79251-125">因為 `ICLRMemoryNotificationCallback` 介面只會定義一個方法（[ICLRMemoryNotificationCallback：： OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)），而且因為 `pCallback` 是 CLR 所提供之 `ICLRMemoryNotificationCallback` 實例的指標，所以會有效地註冊回呼函數本身。</span><span class="sxs-lookup"><span data-stu-id="79251-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="79251-126">主機會叫用 `OnMemoryNotification` 來報告記憶體壓力條件，而不是使用標準的 Win32 `CreateMemoryResourceNotification` 函數。</span><span class="sxs-lookup"><span data-stu-id="79251-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="79251-127">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="79251-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79251-128">對 `OnMemoryNotification` 的呼叫永遠不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="79251-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="79251-129">它們一律會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="79251-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79251-130">需求</span><span class="sxs-lookup"><span data-stu-id="79251-130">Requirements</span></span>  
 <span data-ttu-id="79251-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79251-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79251-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="79251-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79251-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="79251-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79251-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79251-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79251-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="79251-135">See also</span></span>

- [<span data-ttu-id="79251-136">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="79251-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="79251-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="79251-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
