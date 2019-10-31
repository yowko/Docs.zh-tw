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
ms.openlocfilehash: 11b9b500e16917498856888c437c58c0df2edafb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140981"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="1228e-102">ICLRMemoryNotificationCallback::OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="1228e-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="1228e-103">通知 common language runtime （CLR）電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="1228e-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1228e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1228e-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1228e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1228e-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="1228e-106">在其中一個[EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)值，表示電腦目前遇到的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="1228e-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1228e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1228e-107">Return Value</span></span>  
  
|<span data-ttu-id="1228e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1228e-108">HRESULT</span></span>|<span data-ttu-id="1228e-109">描述</span><span class="sxs-lookup"><span data-stu-id="1228e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1228e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1228e-110">S_OK</span></span>|<span data-ttu-id="1228e-111">已成功傳回 `OnMemoryNotification`。</span><span class="sxs-lookup"><span data-stu-id="1228e-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="1228e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1228e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1228e-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1228e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1228e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1228e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1228e-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="1228e-115">The call timed out.</span></span>|  
|<span data-ttu-id="1228e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1228e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1228e-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1228e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1228e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1228e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1228e-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="1228e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1228e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1228e-120">E_FAIL</span></span>|<span data-ttu-id="1228e-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1228e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1228e-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="1228e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1228e-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1228e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1228e-124">備註</span><span class="sxs-lookup"><span data-stu-id="1228e-124">Remarks</span></span>  
 <span data-ttu-id="1228e-125">CLR 會使用[IHostMemoryManager：： RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)方法的呼叫，將回呼註冊到 `OnMemoryNotification`。</span><span class="sxs-lookup"><span data-stu-id="1228e-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="1228e-126">執行時間會使用在回呼中傳回的資訊，在主機報告記憶體資源的不足時釋放額外的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1228e-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1228e-127">對 `OnMemoryNotification` 的呼叫永遠不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="1228e-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="1228e-128">它們一律會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="1228e-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1228e-129">需求</span><span class="sxs-lookup"><span data-stu-id="1228e-129">Requirements</span></span>  
 <span data-ttu-id="1228e-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1228e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1228e-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1228e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1228e-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1228e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1228e-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1228e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1228e-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="1228e-134">See also</span></span>

- [<span data-ttu-id="1228e-135">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="1228e-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="1228e-136">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="1228e-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="1228e-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1228e-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
