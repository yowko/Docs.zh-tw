---
title: IHostSyncManager::CreateRWLockWriterEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: 13eb23c530a4fe1b491f41cc65cc94dacc9d34f4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192001"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="50d3e-102">IHostSyncManager::CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="50d3e-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="50d3e-103">建立自動重設事件物件，以執行寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="50d3e-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50d3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="50d3e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50d3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="50d3e-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="50d3e-106">在要與自動重設事件產生關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="50d3e-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="50d3e-107">脫銷[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)實例位址的指標，如果無法建立事件物件則為 null。</span><span class="sxs-lookup"><span data-stu-id="50d3e-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50d3e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="50d3e-108">Return Value</span></span>  
  
|<span data-ttu-id="50d3e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50d3e-109">HRESULT</span></span>|<span data-ttu-id="50d3e-110">描述</span><span class="sxs-lookup"><span data-stu-id="50d3e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50d3e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="50d3e-111">S_OK</span></span>|<span data-ttu-id="50d3e-112">已成功傳回 `CreateRWLockWriterEvent`。</span><span class="sxs-lookup"><span data-stu-id="50d3e-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="50d3e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50d3e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50d3e-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="50d3e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50d3e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50d3e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50d3e-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="50d3e-116">The call timed out.</span></span>|  
|<span data-ttu-id="50d3e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50d3e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50d3e-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="50d3e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50d3e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50d3e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50d3e-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="50d3e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50d3e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50d3e-121">E_FAIL</span></span>|<span data-ttu-id="50d3e-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="50d3e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50d3e-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="50d3e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50d3e-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="50d3e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="50d3e-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="50d3e-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="50d3e-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="50d3e-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50d3e-127">備註</span><span class="sxs-lookup"><span data-stu-id="50d3e-127">Remarks</span></span>  
 <span data-ttu-id="50d3e-128">CLR 會呼叫 `CreateRWLockWriterEvent` 方法，以取得 `IHostAutoEvent` 實例的參考，以在其寫入器鎖定的執行中使用。</span><span class="sxs-lookup"><span data-stu-id="50d3e-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="50d3e-129">主機可以使用指定的 cookie，藉由呼叫[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)介面的反復專案方法，來判斷哪些工作正在等候鎖定。</span><span class="sxs-lookup"><span data-stu-id="50d3e-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50d3e-130">需求</span><span class="sxs-lookup"><span data-stu-id="50d3e-130">Requirements</span></span>  
 <span data-ttu-id="50d3e-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50d3e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50d3e-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="50d3e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50d3e-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="50d3e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50d3e-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50d3e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d3e-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="50d3e-135">See also</span></span>

- [<span data-ttu-id="50d3e-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="50d3e-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="50d3e-137">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="50d3e-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="50d3e-138">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="50d3e-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="50d3e-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="50d3e-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
