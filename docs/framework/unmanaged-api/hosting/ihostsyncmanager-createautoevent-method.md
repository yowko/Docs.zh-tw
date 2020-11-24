---
title: IHostSyncManager::CreateAutoEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: 37c306df76a796d6e0a2b7540ebd85c13865dfbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682974"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="9d9b2-102">IHostSyncManager::CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="9d9b2-102">IHostSyncManager::CreateAutoEvent Method</span></span>

<span data-ttu-id="9d9b2-103">建立自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d9b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d9b2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d9b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d9b2-105">Parameters</span></span>  

 `ppEvent`  
 <span data-ttu-id="9d9b2-106">擴展主機所執行之 [IHostAutoEvent](ihostautoevent-interface.md) 實例位址的指標，如果無法建立事件物件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-106">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d9b2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9d9b2-107">Return Value</span></span>  
  
|<span data-ttu-id="9d9b2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d9b2-108">HRESULT</span></span>|<span data-ttu-id="9d9b2-109">描述</span><span class="sxs-lookup"><span data-stu-id="9d9b2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d9b2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d9b2-110">S_OK</span></span>|<span data-ttu-id="9d9b2-111">`CreateAutoEvent` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9d9b2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d9b2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d9b2-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d9b2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d9b2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d9b2-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-115">The call timed out.</span></span>|  
|<span data-ttu-id="9d9b2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d9b2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d9b2-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d9b2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d9b2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d9b2-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d9b2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d9b2-120">E_FAIL</span></span>|<span data-ttu-id="9d9b2-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d9b2-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d9b2-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d9b2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9d9b2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9d9b2-125">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d9b2-126">備註</span><span class="sxs-lookup"><span data-stu-id="9d9b2-126">Remarks</span></span>  

 <span data-ttu-id="9d9b2-127">`CreateAutoEvent` 建立自動事件物件，其狀態會在等候的執行緒釋放後自動變更為非信號。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="9d9b2-128">這個方法會將 Win32 `CreateEvent` 函數與 `false` 針對參數指定的值進行鏡像處理 `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="9d9b2-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d9b2-129">需求</span><span class="sxs-lookup"><span data-stu-id="9d9b2-129">Requirements</span></span>  

 <span data-ttu-id="9d9b2-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9b2-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d9b2-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9d9b2-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d9b2-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9d9b2-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d9b2-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d9b2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9b2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d9b2-134">See also</span></span>

- [<span data-ttu-id="9d9b2-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9d9b2-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="9d9b2-136">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9d9b2-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="9d9b2-137">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="9d9b2-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="9d9b2-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9d9b2-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
