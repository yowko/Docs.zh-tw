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
ms.openlocfilehash: 87dfbe85d279aa191253857887c1d9b5b5f8c7cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088518"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="29ab3-102">IHostMemoryManager::RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="29ab3-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="29ab3-103">註冊以通知 common language runtime (CLR) 的主應用程式會叫用的回呼函式指標的目前的記憶體負載，在電腦上。</span><span class="sxs-lookup"><span data-stu-id="29ab3-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ab3-104">語法</span><span class="sxs-lookup"><span data-stu-id="29ab3-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ab3-105">參數</span><span class="sxs-lookup"><span data-stu-id="29ab3-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="29ab3-106">[in]介面指標[ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)由 CLR 實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29ab3-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29ab3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="29ab3-107">Return Value</span></span>  
  
|<span data-ttu-id="29ab3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29ab3-108">HRESULT</span></span>|<span data-ttu-id="29ab3-109">描述</span><span class="sxs-lookup"><span data-stu-id="29ab3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29ab3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="29ab3-110">S_OK</span></span>|<span data-ttu-id="29ab3-111">`RegisterMemoryNotificationCallback` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="29ab3-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="29ab3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29ab3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29ab3-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="29ab3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29ab3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29ab3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29ab3-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="29ab3-115">The call timed out.</span></span>|  
|<span data-ttu-id="29ab3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29ab3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29ab3-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="29ab3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29ab3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29ab3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29ab3-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="29ab3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29ab3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29ab3-120">E_FAIL</span></span>|<span data-ttu-id="29ab3-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="29ab3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29ab3-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="29ab3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29ab3-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="29ab3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29ab3-124">備註</span><span class="sxs-lookup"><span data-stu-id="29ab3-124">Remarks</span></span>  
 <span data-ttu-id="29ab3-125">因為`ICLRMemoryNotificationCallback`介面會定義只有一個方法 ([iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md))，而且因為`pCallback`是一個指向`ICLRMemoryNotificationCallback`CLR，所提供的執行個體註冊實際上是回呼函式本身。</span><span class="sxs-lookup"><span data-stu-id="29ab3-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="29ab3-126">主機會叫用`OnMemoryNotification`報告的記憶體不足的壓力條件，而不是使用標準的 Win32`CreateMemoryResourceNotification`函式。</span><span class="sxs-lookup"><span data-stu-id="29ab3-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="29ab3-127">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="29ab3-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29ab3-128">呼叫`OnMemoryNotification`絕對不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="29ab3-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="29ab3-129">它們永遠會立即回傳。</span><span class="sxs-lookup"><span data-stu-id="29ab3-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ab3-130">需求</span><span class="sxs-lookup"><span data-stu-id="29ab3-130">Requirements</span></span>  
 <span data-ttu-id="29ab3-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29ab3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ab3-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29ab3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29ab3-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="29ab3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29ab3-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ab3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ab3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29ab3-135">See also</span></span>

- [<span data-ttu-id="29ab3-136">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="29ab3-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="29ab3-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="29ab3-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
