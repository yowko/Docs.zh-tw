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
ms.openlocfilehash: 3847c5e5704f4eef138bf8b3f7966e4ff66d8784
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716307"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="08d39-102">ICLRSyncManager::GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="08d39-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="08d39-103">取得[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)擁有所指定的 cookie 識別監視器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="08d39-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d39-104">語法</span><span class="sxs-lookup"><span data-stu-id="08d39-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08d39-105">參數</span><span class="sxs-lookup"><span data-stu-id="08d39-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="08d39-106">[in]與監視相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="08d39-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="08d39-107">[out]指標`IHostTask`目前擁有監視器，則為 null 如果沒有工作具有擁有權。</span><span class="sxs-lookup"><span data-stu-id="08d39-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08d39-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="08d39-108">Return Value</span></span>  
  
|<span data-ttu-id="08d39-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08d39-109">HRESULT</span></span>|<span data-ttu-id="08d39-110">描述</span><span class="sxs-lookup"><span data-stu-id="08d39-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08d39-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="08d39-111">S_OK</span></span>|<span data-ttu-id="08d39-112">`GetMonitorOwner` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="08d39-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="08d39-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08d39-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08d39-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="08d39-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08d39-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08d39-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08d39-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="08d39-116">The call timed out.</span></span>|  
|<span data-ttu-id="08d39-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08d39-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08d39-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="08d39-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08d39-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08d39-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08d39-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="08d39-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08d39-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08d39-121">E_FAIL</span></span>|<span data-ttu-id="08d39-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="08d39-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08d39-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="08d39-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08d39-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="08d39-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d39-125">備註</span><span class="sxs-lookup"><span data-stu-id="08d39-125">Remarks</span></span>  
 <span data-ttu-id="08d39-126">主機通常會呼叫`GetMonitorOwner`死結偵測機制的一部分。</span><span class="sxs-lookup"><span data-stu-id="08d39-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="08d39-127">建立藉由呼叫時，cookie 是與監視相關聯[ihostsyncmanager:: Createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)。</span><span class="sxs-lookup"><span data-stu-id="08d39-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08d39-128">可能會封鎖呼叫釋放基準監視的事件，但不是會鎖死，如果此方法的呼叫正在目前作用中與該監視器相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="08d39-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="08d39-129">如果嘗試取得此監視，也可能會封鎖其他工作。</span><span class="sxs-lookup"><span data-stu-id="08d39-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="08d39-130">`GetMonitorOwner` 一律會立即傳回，而且可以在呼叫之後任何時間呼叫`CreateMonitorEvent`。</span><span class="sxs-lookup"><span data-stu-id="08d39-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="08d39-131">主應用程式不需要等候，直到工作在等候事件。</span><span class="sxs-lookup"><span data-stu-id="08d39-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d39-132">需求</span><span class="sxs-lookup"><span data-stu-id="08d39-132">Requirements</span></span>  
 <span data-ttu-id="08d39-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08d39-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d39-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08d39-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08d39-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="08d39-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08d39-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d39-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d39-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08d39-137">See also</span></span>
- [<span data-ttu-id="08d39-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="08d39-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="08d39-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="08d39-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
