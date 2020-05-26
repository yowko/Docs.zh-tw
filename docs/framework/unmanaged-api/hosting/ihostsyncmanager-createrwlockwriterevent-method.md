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
ms.openlocfilehash: f00d166541f7955516e9d5c1dce2a4342c08ad0a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803152"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="54fea-102">IHostSyncManager::CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="54fea-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="54fea-103">建立自動重設事件物件，以執行寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="54fea-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54fea-104">語法</span><span class="sxs-lookup"><span data-stu-id="54fea-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54fea-105">參數</span><span class="sxs-lookup"><span data-stu-id="54fea-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="54fea-106">在要與自動重設事件產生關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="54fea-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="54fea-107">脫銷[IHostAutoEvent](ihostautoevent-interface.md)實例位址的指標，如果無法建立事件物件則為 null。</span><span class="sxs-lookup"><span data-stu-id="54fea-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54fea-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="54fea-108">Return Value</span></span>  
  
|<span data-ttu-id="54fea-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54fea-109">HRESULT</span></span>|<span data-ttu-id="54fea-110">描述</span><span class="sxs-lookup"><span data-stu-id="54fea-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54fea-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="54fea-111">S_OK</span></span>|<span data-ttu-id="54fea-112">`CreateRWLockWriterEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="54fea-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="54fea-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54fea-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54fea-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="54fea-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54fea-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54fea-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54fea-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="54fea-116">The call timed out.</span></span>|  
|<span data-ttu-id="54fea-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54fea-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54fea-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="54fea-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54fea-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54fea-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54fea-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="54fea-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54fea-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54fea-121">E_FAIL</span></span>|<span data-ttu-id="54fea-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="54fea-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54fea-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="54fea-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54fea-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="54fea-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="54fea-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="54fea-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="54fea-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="54fea-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54fea-127">備註</span><span class="sxs-lookup"><span data-stu-id="54fea-127">Remarks</span></span>  
 <span data-ttu-id="54fea-128">CLR 會呼叫 `CreateRWLockWriterEvent` 方法來取得實例的參考， `IHostAutoEvent` 以在其寫入器鎖定的執行中使用。</span><span class="sxs-lookup"><span data-stu-id="54fea-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="54fea-129">主機可以使用指定的 cookie，藉由呼叫[ICLRSyncManager](iclrsyncmanager-interface.md)介面的反復專案方法，來判斷哪些工作正在等候鎖定。</span><span class="sxs-lookup"><span data-stu-id="54fea-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54fea-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="54fea-130">Requirements</span></span>  
 <span data-ttu-id="54fea-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54fea-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54fea-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="54fea-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54fea-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="54fea-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54fea-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54fea-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54fea-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54fea-135">See also</span></span>

- [<span data-ttu-id="54fea-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="54fea-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="54fea-137">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="54fea-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="54fea-138">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="54fea-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="54fea-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="54fea-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
