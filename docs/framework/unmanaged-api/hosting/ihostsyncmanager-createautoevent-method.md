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
ms.openlocfilehash: ba221beaa0edce49e75f75edddaee72e1beb9747
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803507"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="7c421-102">IHostSyncManager::CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="7c421-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="7c421-103">建立自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="7c421-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c421-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c421-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c421-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c421-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="7c421-106">脫銷主機所實[IHostAutoEvent](ihostautoevent-interface.md)實例的位址指標，如果無法建立事件物件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="7c421-106">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c421-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7c421-107">Return Value</span></span>  
  
|<span data-ttu-id="7c421-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c421-108">HRESULT</span></span>|<span data-ttu-id="7c421-109">描述</span><span class="sxs-lookup"><span data-stu-id="7c421-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c421-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c421-110">S_OK</span></span>|<span data-ttu-id="7c421-111">`CreateAutoEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7c421-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="7c421-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c421-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c421-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7c421-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c421-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c421-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c421-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="7c421-115">The call timed out.</span></span>|  
|<span data-ttu-id="7c421-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c421-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c421-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7c421-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c421-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c421-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c421-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="7c421-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c421-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c421-120">E_FAIL</span></span>|<span data-ttu-id="7c421-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7c421-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c421-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="7c421-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c421-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7c421-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7c421-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7c421-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7c421-125">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="7c421-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c421-126">備註</span><span class="sxs-lookup"><span data-stu-id="7c421-126">Remarks</span></span>  
 <span data-ttu-id="7c421-127">`CreateAutoEvent`建立自動事件物件，其狀態會在等候的執行緒釋放之後自動變更為非信號。</span><span class="sxs-lookup"><span data-stu-id="7c421-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="7c421-128">這個方法會 `CreateEvent` 使用 `false` 針對參數所指定的值來鏡像 Win32 函數。 `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="7c421-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c421-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="7c421-129">Requirements</span></span>  
 <span data-ttu-id="7c421-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c421-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c421-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7c421-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c421-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7c421-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c421-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c421-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c421-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c421-134">See also</span></span>

- [<span data-ttu-id="7c421-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7c421-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7c421-136">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="7c421-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="7c421-137">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="7c421-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="7c421-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7c421-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
