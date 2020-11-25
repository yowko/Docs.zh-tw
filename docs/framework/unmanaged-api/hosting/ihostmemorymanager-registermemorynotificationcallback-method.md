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
ms.openlocfilehash: edb29378412583d7cdec804b08f8f622d642b02f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731302"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="81236-102">IHostMemoryManager::RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="81236-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>

<span data-ttu-id="81236-103">註冊回呼函式的指標，主機會叫用此函式，以通知 common language runtime (CLR) 電腦上目前的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="81236-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81236-104">語法</span><span class="sxs-lookup"><span data-stu-id="81236-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81236-105">參數</span><span class="sxs-lookup"><span data-stu-id="81236-105">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="81236-106">在CLR 所執行之 [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="81236-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81236-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="81236-107">Return Value</span></span>  
  
|<span data-ttu-id="81236-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81236-108">HRESULT</span></span>|<span data-ttu-id="81236-109">描述</span><span class="sxs-lookup"><span data-stu-id="81236-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81236-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="81236-110">S_OK</span></span>|<span data-ttu-id="81236-111">`RegisterMemoryNotificationCallback` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="81236-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="81236-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81236-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81236-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="81236-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81236-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81236-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81236-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="81236-115">The call timed out.</span></span>|  
|<span data-ttu-id="81236-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81236-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81236-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="81236-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81236-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81236-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81236-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="81236-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81236-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81236-120">E_FAIL</span></span>|<span data-ttu-id="81236-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="81236-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81236-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="81236-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81236-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="81236-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81236-124">備註</span><span class="sxs-lookup"><span data-stu-id="81236-124">Remarks</span></span>  

 <span data-ttu-id="81236-125">因為此 `ICLRMemoryNotificationCallback` 介面只會定義一個方法 ([ICLRMemoryNotificationCallback：： OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)) ，而且因為 `pCallback` 是 CLR 提供之實例的指標，所以該註冊對回呼函式 `ICLRMemoryNotificationCallback` 本身而言是有效的。</span><span class="sxs-lookup"><span data-stu-id="81236-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="81236-126">主機會叫 `OnMemoryNotification` 用以報告記憶體壓力條件，而不是使用標準 Win32 `CreateMemoryResourceNotification` 函數。</span><span class="sxs-lookup"><span data-stu-id="81236-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="81236-127">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="81236-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81236-128">`OnMemoryNotification`永遠不會封鎖的呼叫。</span><span class="sxs-lookup"><span data-stu-id="81236-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="81236-129">它們一律會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="81236-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81236-130">需求</span><span class="sxs-lookup"><span data-stu-id="81236-130">Requirements</span></span>  

 <span data-ttu-id="81236-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81236-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81236-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="81236-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81236-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="81236-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81236-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81236-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81236-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81236-135">See also</span></span>

- [<span data-ttu-id="81236-136">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="81236-136">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="81236-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="81236-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
