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
ms.openlocfilehash: 5668d75c831710b4f077c325b40352a518ee2c96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434300"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="d450a-102">ICLRSyncManager::GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="d450a-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="d450a-103">取得[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)擁有指定的 cookie 所識別的監視器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d450a-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d450a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d450a-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d450a-105">參數</span><span class="sxs-lookup"><span data-stu-id="d450a-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="d450a-106">[in]監視相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="d450a-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="d450a-107">[out]指標`IHostTask`目前擁有的監視器或為 null 沒有工作是否擁有權。</span><span class="sxs-lookup"><span data-stu-id="d450a-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d450a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d450a-108">Return Value</span></span>  
  
|<span data-ttu-id="d450a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d450a-109">HRESULT</span></span>|<span data-ttu-id="d450a-110">描述</span><span class="sxs-lookup"><span data-stu-id="d450a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d450a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d450a-111">S_OK</span></span>|<span data-ttu-id="d450a-112">`GetMonitorOwner` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d450a-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="d450a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d450a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d450a-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d450a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d450a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d450a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d450a-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d450a-116">The call timed out.</span></span>|  
|<span data-ttu-id="d450a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d450a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d450a-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d450a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d450a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d450a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d450a-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d450a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d450a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d450a-121">E_FAIL</span></span>|<span data-ttu-id="d450a-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d450a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d450a-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d450a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d450a-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d450a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d450a-125">備註</span><span class="sxs-lookup"><span data-stu-id="d450a-125">Remarks</span></span>  
 <span data-ttu-id="d450a-126">主機通常會呼叫`GetMonitorOwner`死結偵測機制的一部分。</span><span class="sxs-lookup"><span data-stu-id="d450a-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="d450a-127">Cookie 會與監視相關聯時就會建立使用呼叫[ihostsyncmanager:: Createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d450a-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d450a-128">釋放基礎監視事件的呼叫可能封鎖，但不是會鎖死，如果此方法的呼叫位於目前作用中與該監視相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="d450a-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="d450a-129">當他們嘗試取得此監視，也可能會封鎖其他工作。</span><span class="sxs-lookup"><span data-stu-id="d450a-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="d450a-130">`GetMonitorOwner` 一律會立即傳回，而且可以隨時呼叫之後呼叫`CreateMonitorEvent`。</span><span class="sxs-lookup"><span data-stu-id="d450a-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="d450a-131">主機不需要等候工作在等候事件。</span><span class="sxs-lookup"><span data-stu-id="d450a-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d450a-132">需求</span><span class="sxs-lookup"><span data-stu-id="d450a-132">Requirements</span></span>  
 <span data-ttu-id="d450a-133">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d450a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d450a-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d450a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d450a-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d450a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d450a-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d450a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d450a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d450a-137">See Also</span></span>  
 [<span data-ttu-id="d450a-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d450a-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d450a-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d450a-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
