---
title: "IHostSyncManager::CreateRWLockWriterEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockWriterEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb38cd76a051b1a4459dff4f8164a6405f5fb32d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="24e40-102">IHostSyncManager::CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="24e40-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="24e40-103">建立自動重設事件物件的寫入器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="24e40-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e40-104">語法</span><span class="sxs-lookup"><span data-stu-id="24e40-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24e40-105">參數</span><span class="sxs-lookup"><span data-stu-id="24e40-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="24e40-106">[in]要與自動重設事件關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="24e40-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="24e40-107">[out]位址指標[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)執行個體，或如果無法建立事件物件則為 null。</span><span class="sxs-lookup"><span data-stu-id="24e40-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24e40-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="24e40-108">Return Value</span></span>  
  
|<span data-ttu-id="24e40-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24e40-109">HRESULT</span></span>|<span data-ttu-id="24e40-110">描述</span><span class="sxs-lookup"><span data-stu-id="24e40-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24e40-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="24e40-111">S_OK</span></span>|<span data-ttu-id="24e40-112">`CreateRWLockWriterEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="24e40-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="24e40-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24e40-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24e40-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="24e40-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="24e40-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="24e40-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="24e40-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="24e40-116">The call timed out.</span></span>|  
|<span data-ttu-id="24e40-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="24e40-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="24e40-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="24e40-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="24e40-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="24e40-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="24e40-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="24e40-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="24e40-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24e40-121">E_FAIL</span></span>|<span data-ttu-id="24e40-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="24e40-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="24e40-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="24e40-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="24e40-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="24e40-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="24e40-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="24e40-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="24e40-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="24e40-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24e40-127">備註</span><span class="sxs-lookup"><span data-stu-id="24e40-127">Remarks</span></span>  
 <span data-ttu-id="24e40-128">CLR 會呼叫`CreateRWLockWriterEvent`方法來取得參考`IHostAutoEvent`寫入器鎖定的實作中使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="24e40-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="24e40-129">主機可以使用指定的 cookie，以判斷哪些工作正在等候鎖定的反覆項目方法[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="24e40-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e40-130">需求</span><span class="sxs-lookup"><span data-stu-id="24e40-130">Requirements</span></span>  
 <span data-ttu-id="24e40-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24e40-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24e40-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24e40-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24e40-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="24e40-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24e40-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24e40-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e40-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="24e40-135">See Also</span></span>  
 [<span data-ttu-id="24e40-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="24e40-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="24e40-137">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="24e40-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="24e40-138">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="24e40-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="24e40-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="24e40-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
