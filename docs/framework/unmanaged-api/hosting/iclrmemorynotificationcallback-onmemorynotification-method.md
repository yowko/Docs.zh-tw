---
title: ICLRMemoryNotificationCallback::OnMemoryNotification 方法
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 899d0cf6a0475846b749bd0b7cbda41b1b88253d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949697"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="047ae-102">ICLRMemoryNotificationCallback::OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="047ae-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="047ae-103">通知 common language runtime (CLR) 電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="047ae-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="047ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="047ae-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="047ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="047ae-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="047ae-106">在其中一個[EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)值, 表示電腦目前遇到的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="047ae-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="047ae-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="047ae-107">Return Value</span></span>  
  
|<span data-ttu-id="047ae-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="047ae-108">HRESULT</span></span>|<span data-ttu-id="047ae-109">描述</span><span class="sxs-lookup"><span data-stu-id="047ae-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="047ae-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="047ae-110">S_OK</span></span>|<span data-ttu-id="047ae-111">`OnMemoryNotification`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="047ae-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="047ae-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="047ae-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="047ae-113">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="047ae-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="047ae-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="047ae-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="047ae-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="047ae-115">The call timed out.</span></span>|  
|<span data-ttu-id="047ae-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="047ae-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="047ae-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="047ae-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="047ae-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="047ae-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="047ae-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="047ae-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="047ae-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="047ae-120">E_FAIL</span></span>|<span data-ttu-id="047ae-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="047ae-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="047ae-122">在方法傳回 E_FAIL 之後, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="047ae-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="047ae-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="047ae-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="047ae-124">備註</span><span class="sxs-lookup"><span data-stu-id="047ae-124">Remarks</span></span>  
 <span data-ttu-id="047ae-125">CLR 會使用`OnMemoryNotification` [IHostMemoryManager:: RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)方法的呼叫, 將回呼註冊至。</span><span class="sxs-lookup"><span data-stu-id="047ae-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="047ae-126">執行時間會使用在回呼中傳回的資訊, 在主機報告記憶體資源的不足時釋放額外的記憶體。</span><span class="sxs-lookup"><span data-stu-id="047ae-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="047ae-127">`OnMemoryNotification`從不封鎖的呼叫。</span><span class="sxs-lookup"><span data-stu-id="047ae-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="047ae-128">它們一律會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="047ae-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="047ae-129">需求</span><span class="sxs-lookup"><span data-stu-id="047ae-129">Requirements</span></span>  
 <span data-ttu-id="047ae-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="047ae-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="047ae-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="047ae-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="047ae-132">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="047ae-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="047ae-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="047ae-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047ae-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="047ae-134">See also</span></span>

- [<span data-ttu-id="047ae-135">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="047ae-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="047ae-136">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="047ae-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="047ae-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="047ae-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
