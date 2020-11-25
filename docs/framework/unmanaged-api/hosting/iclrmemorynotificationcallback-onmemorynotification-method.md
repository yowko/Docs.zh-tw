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
ms.openlocfilehash: f9b2715801ebcaff3d97962540a4b1b103bbd53b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730466"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="aeab1-102">ICLRMemoryNotificationCallback::OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="aeab1-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>

<span data-ttu-id="aeab1-103">通知 common language runtime (CLR) 電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="aeab1-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeab1-104">語法</span><span class="sxs-lookup"><span data-stu-id="aeab1-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeab1-105">參數</span><span class="sxs-lookup"><span data-stu-id="aeab1-105">Parameters</span></span>  

 `eMemoryAvailable`  
 <span data-ttu-id="aeab1-106">在其中一個 [EMemoryAvailable](ememoryavailable-enumeration.md) 值，表示電腦目前遇到的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="aeab1-106">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aeab1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="aeab1-107">Return Value</span></span>  
  
|<span data-ttu-id="aeab1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aeab1-108">HRESULT</span></span>|<span data-ttu-id="aeab1-109">描述</span><span class="sxs-lookup"><span data-stu-id="aeab1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aeab1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aeab1-110">S_OK</span></span>|<span data-ttu-id="aeab1-111">`OnMemoryNotification` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="aeab1-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="aeab1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aeab1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aeab1-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="aeab1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aeab1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aeab1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aeab1-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="aeab1-115">The call timed out.</span></span>|  
|<span data-ttu-id="aeab1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aeab1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aeab1-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="aeab1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aeab1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aeab1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aeab1-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="aeab1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aeab1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aeab1-120">E_FAIL</span></span>|<span data-ttu-id="aeab1-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="aeab1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aeab1-122">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="aeab1-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aeab1-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="aeab1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeab1-124">備註</span><span class="sxs-lookup"><span data-stu-id="aeab1-124">Remarks</span></span>  

 <span data-ttu-id="aeab1-125">CLR 會 `OnMemoryNotification` 使用 [IHostMemoryManager：： RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) 方法的呼叫，將回呼註冊至。</span><span class="sxs-lookup"><span data-stu-id="aeab1-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="aeab1-126">當主機報告記憶體資源不足時，執行時間會使用回呼中傳回的資訊來釋放額外的記憶體。</span><span class="sxs-lookup"><span data-stu-id="aeab1-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeab1-127">`OnMemoryNotification`永遠不會封鎖的呼叫。</span><span class="sxs-lookup"><span data-stu-id="aeab1-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="aeab1-128">它們一律會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="aeab1-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeab1-129">需求</span><span class="sxs-lookup"><span data-stu-id="aeab1-129">Requirements</span></span>  

 <span data-ttu-id="aeab1-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aeab1-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeab1-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="aeab1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeab1-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="aeab1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeab1-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeab1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeab1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aeab1-134">See also</span></span>

- [<span data-ttu-id="aeab1-135">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="aeab1-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="aeab1-136">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="aeab1-136">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="aeab1-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="aeab1-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
