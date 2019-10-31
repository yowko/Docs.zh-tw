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
ms.openlocfilehash: b3778e12dd96d4f4653633252e13469601c4879d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139446"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="025bf-102">IHostSyncManager::CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="025bf-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="025bf-103">建立自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="025bf-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="025bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="025bf-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="025bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="025bf-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="025bf-106">脫銷主機所實[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)實例的位址指標，如果無法建立事件物件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="025bf-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="025bf-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="025bf-107">Return Value</span></span>  
  
|<span data-ttu-id="025bf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="025bf-108">HRESULT</span></span>|<span data-ttu-id="025bf-109">描述</span><span class="sxs-lookup"><span data-stu-id="025bf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="025bf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="025bf-110">S_OK</span></span>|<span data-ttu-id="025bf-111">已成功傳回 `CreateAutoEvent`。</span><span class="sxs-lookup"><span data-stu-id="025bf-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="025bf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="025bf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="025bf-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="025bf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="025bf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="025bf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="025bf-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="025bf-115">The call timed out.</span></span>|  
|<span data-ttu-id="025bf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="025bf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="025bf-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="025bf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="025bf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="025bf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="025bf-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="025bf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="025bf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="025bf-120">E_FAIL</span></span>|<span data-ttu-id="025bf-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="025bf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="025bf-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="025bf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="025bf-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="025bf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="025bf-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="025bf-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="025bf-125">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="025bf-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="025bf-126">備註</span><span class="sxs-lookup"><span data-stu-id="025bf-126">Remarks</span></span>  
 <span data-ttu-id="025bf-127">`CreateAutoEvent` 會建立自動事件物件，其狀態會在等候的執行緒釋放之後自動變更為非信號。</span><span class="sxs-lookup"><span data-stu-id="025bf-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="025bf-128">這個方法會使用針對 `bManualReset` 參數所指定的 `false` 值，鏡像 Win32 `CreateEvent` 函式</span><span class="sxs-lookup"><span data-stu-id="025bf-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="025bf-129">需求</span><span class="sxs-lookup"><span data-stu-id="025bf-129">Requirements</span></span>  
 <span data-ttu-id="025bf-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="025bf-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="025bf-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="025bf-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="025bf-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="025bf-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="025bf-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="025bf-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025bf-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="025bf-134">See also</span></span>

- [<span data-ttu-id="025bf-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="025bf-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="025bf-136">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="025bf-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="025bf-137">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="025bf-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="025bf-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="025bf-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
