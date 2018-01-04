---
title: "IHostMemoryManager::RegisterMemoryNotificationCallback 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.RegisterMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a59de95ea671b6f568ade81005c718cac00350e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="7af89-102">IHostMemoryManager::RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="7af89-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="7af89-103">目前的記憶體負載，在電腦上的註冊以通知 common language runtime (CLR) 的主機會叫用的回呼函式的指標。</span><span class="sxs-lookup"><span data-stu-id="7af89-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af89-104">語法</span><span class="sxs-lookup"><span data-stu-id="7af89-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7af89-105">參數</span><span class="sxs-lookup"><span data-stu-id="7af89-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="7af89-106">[in]介面指標[ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)由 CLR 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7af89-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7af89-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7af89-107">Return Value</span></span>  
  
|<span data-ttu-id="7af89-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7af89-108">HRESULT</span></span>|<span data-ttu-id="7af89-109">描述</span><span class="sxs-lookup"><span data-stu-id="7af89-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7af89-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7af89-110">S_OK</span></span>|<span data-ttu-id="7af89-111">`RegisterMemoryNotificationCallback`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7af89-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="7af89-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7af89-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7af89-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7af89-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7af89-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7af89-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7af89-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="7af89-115">The call timed out.</span></span>|  
|<span data-ttu-id="7af89-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7af89-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7af89-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7af89-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7af89-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7af89-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7af89-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="7af89-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7af89-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7af89-120">E_FAIL</span></span>|<span data-ttu-id="7af89-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7af89-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7af89-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="7af89-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7af89-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7af89-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7af89-124">備註</span><span class="sxs-lookup"><span data-stu-id="7af89-124">Remarks</span></span>  
 <span data-ttu-id="7af89-125">因為`ICLRMemoryNotificationCallback`介面會定義只有一個方法 ([iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md))，而且因為`pCallback`是指向`ICLRMemoryNotificationCallback`CLR 所提供的執行個體註冊是有效的回呼函式本身。</span><span class="sxs-lookup"><span data-stu-id="7af89-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="7af89-126">主機會叫用`OnMemoryNotification`報表記憶體不足壓力的情況，而不是使用標準 Win32`CreateMemoryResourceNotification`函式。</span><span class="sxs-lookup"><span data-stu-id="7af89-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="7af89-127">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="7af89-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7af89-128">呼叫`OnMemoryNotification`永遠不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="7af89-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="7af89-129">它們一律立即傳回。</span><span class="sxs-lookup"><span data-stu-id="7af89-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7af89-130">需求</span><span class="sxs-lookup"><span data-stu-id="7af89-130">Requirements</span></span>  
 <span data-ttu-id="7af89-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7af89-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af89-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7af89-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7af89-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7af89-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7af89-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7af89-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af89-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="7af89-135">See Also</span></span>  
 [<span data-ttu-id="7af89-136">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7af89-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="7af89-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="7af89-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
