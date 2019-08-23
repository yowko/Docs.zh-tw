---
title: ICLRSyncManager::GetMonitorOwner 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e08af840d1c4a654fa9b9ff8b2064f5265afaf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943247"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="43e14-102">ICLRSyncManager::GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="43e14-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="43e14-103">取得擁有指定之 cookie 所識別之監視器的[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="43e14-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43e14-104">語法</span><span class="sxs-lookup"><span data-stu-id="43e14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43e14-105">參數</span><span class="sxs-lookup"><span data-stu-id="43e14-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="43e14-106">在與監視相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="43e14-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="43e14-107">脫銷目前擁有此監視器`IHostTask`之的指標, 如果沒有任何工作具有擁有權, 則為 null。</span><span class="sxs-lookup"><span data-stu-id="43e14-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43e14-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="43e14-108">Return Value</span></span>  
  
|<span data-ttu-id="43e14-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43e14-109">HRESULT</span></span>|<span data-ttu-id="43e14-110">描述</span><span class="sxs-lookup"><span data-stu-id="43e14-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43e14-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="43e14-111">S_OK</span></span>|<span data-ttu-id="43e14-112">`GetMonitorOwner`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="43e14-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="43e14-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43e14-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43e14-114">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="43e14-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43e14-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43e14-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43e14-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="43e14-116">The call timed out.</span></span>|  
|<span data-ttu-id="43e14-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43e14-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43e14-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="43e14-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43e14-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43e14-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43e14-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="43e14-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43e14-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43e14-121">E_FAIL</span></span>|<span data-ttu-id="43e14-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="43e14-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43e14-123">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="43e14-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43e14-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="43e14-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43e14-125">備註</span><span class="sxs-lookup"><span data-stu-id="43e14-125">Remarks</span></span>  
 <span data-ttu-id="43e14-126">主機通常會呼叫`GetMonitorOwner`作為鎖死偵測機制的一部分。</span><span class="sxs-lookup"><span data-stu-id="43e14-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="43e14-127">當使用[IHostSyncManager:: CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)的呼叫建立時, cookie 會與監視相關聯。</span><span class="sxs-lookup"><span data-stu-id="43e14-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43e14-128">呼叫以釋放監視所基礎的事件可能會封鎖, 但不會鎖死, 如果對此方法的呼叫目前作用於與該監視相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="43e14-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="43e14-129">其他工作也可能會在嘗試取得此監視時封鎖。</span><span class="sxs-lookup"><span data-stu-id="43e14-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="43e14-130">`GetMonitorOwner`一律會立即傳回, 而且可以在呼叫`CreateMonitorEvent`之後隨時呼叫。</span><span class="sxs-lookup"><span data-stu-id="43e14-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="43e14-131">主機不需要等候, 直到工作在等候事件為止。</span><span class="sxs-lookup"><span data-stu-id="43e14-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43e14-132">需求</span><span class="sxs-lookup"><span data-stu-id="43e14-132">Requirements</span></span>  
 <span data-ttu-id="43e14-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43e14-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43e14-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43e14-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43e14-135">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="43e14-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43e14-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43e14-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e14-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43e14-137">See also</span></span>

- [<span data-ttu-id="43e14-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="43e14-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="43e14-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="43e14-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
