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
ms.openlocfilehash: 67af8f125b2be39138bac5d51148215f3a3acf86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723866"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="77746-102">IHostSyncManager::CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="77746-102">IHostSyncManager::CreateManualEvent Method</span></span>

<span data-ttu-id="77746-103">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="77746-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77746-104">語法</span><span class="sxs-lookup"><span data-stu-id="77746-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77746-105">參數</span><span class="sxs-lookup"><span data-stu-id="77746-105">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="77746-106">[in] `true` ，如果物件收到信號，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="77746-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="77746-107">擴展 [IHostManualEvent](ihostmanualevent-interface.md) 實例位址的指標，如果無法建立事件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="77746-107">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77746-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="77746-108">Return Value</span></span>  
  
|<span data-ttu-id="77746-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77746-109">HRESULT</span></span>|<span data-ttu-id="77746-110">描述</span><span class="sxs-lookup"><span data-stu-id="77746-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77746-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="77746-111">S_OK</span></span>|<span data-ttu-id="77746-112">`CreateManualEvent` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="77746-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="77746-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77746-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77746-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="77746-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77746-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77746-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77746-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="77746-116">The call timed out.</span></span>|  
|<span data-ttu-id="77746-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77746-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77746-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="77746-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77746-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77746-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77746-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="77746-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77746-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77746-121">E_FAIL</span></span>|<span data-ttu-id="77746-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="77746-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77746-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="77746-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77746-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="77746-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="77746-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="77746-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="77746-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="77746-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77746-127">備註</span><span class="sxs-lookup"><span data-stu-id="77746-127">Remarks</span></span>  

 <span data-ttu-id="77746-128">`CreateManualEvent` 建立一個 `IHostManualEvent` 手動重設的事件物件，該物件需要呼叫 [IHostManualEvent：： reset](ihostmanualevent-reset-method.md) 方法，才能將它設定為非信號狀態。</span><span class="sxs-lookup"><span data-stu-id="77746-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="77746-129">`CreateManualEvent``CreateEvent`使用 `true` 針對參數指定的值，鏡像 Win32 函數 `bManualReset` 。</span><span class="sxs-lookup"><span data-stu-id="77746-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77746-130">需求</span><span class="sxs-lookup"><span data-stu-id="77746-130">Requirements</span></span>  

 <span data-ttu-id="77746-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77746-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77746-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="77746-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77746-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="77746-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77746-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77746-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77746-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77746-135">See also</span></span>

- [<span data-ttu-id="77746-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="77746-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="77746-137">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="77746-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="77746-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="77746-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
