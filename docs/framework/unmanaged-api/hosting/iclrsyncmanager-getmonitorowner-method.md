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
ms.openlocfilehash: a2cb82d8071518af4d4bc3276871f3846a5a5693
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687064"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="691f3-102">ICLRSyncManager::GetMonitorOwner 方法</span><span class="sxs-lookup"><span data-stu-id="691f3-102">ICLRSyncManager::GetMonitorOwner Method</span></span>

<span data-ttu-id="691f3-103">取得擁有指定之 cookie 所識別之監視的 [IHostTask](ihosttask-interface.md) 實例。</span><span class="sxs-lookup"><span data-stu-id="691f3-103">Gets the [IHostTask](ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="691f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="691f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="691f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="691f3-105">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="691f3-106">在與監視器相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="691f3-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="691f3-107">擴展 `IHostTask` 目前擁有監視之的指標，如果沒有任何工作擁有擁有權，則為 null。</span><span class="sxs-lookup"><span data-stu-id="691f3-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="691f3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="691f3-108">Return Value</span></span>  
  
|<span data-ttu-id="691f3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="691f3-109">HRESULT</span></span>|<span data-ttu-id="691f3-110">描述</span><span class="sxs-lookup"><span data-stu-id="691f3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="691f3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="691f3-111">S_OK</span></span>|<span data-ttu-id="691f3-112">`GetMonitorOwner` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="691f3-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="691f3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="691f3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="691f3-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="691f3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="691f3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="691f3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="691f3-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="691f3-116">The call timed out.</span></span>|  
|<span data-ttu-id="691f3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="691f3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="691f3-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="691f3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="691f3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="691f3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="691f3-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="691f3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="691f3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="691f3-121">E_FAIL</span></span>|<span data-ttu-id="691f3-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="691f3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="691f3-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="691f3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="691f3-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="691f3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="691f3-125">備註</span><span class="sxs-lookup"><span data-stu-id="691f3-125">Remarks</span></span>  

 <span data-ttu-id="691f3-126">主機通常會在 `GetMonitorOwner` 鎖死偵測機制中呼叫。</span><span class="sxs-lookup"><span data-stu-id="691f3-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="691f3-127">當您使用 [IHostSyncManager：： CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md)的呼叫來建立時，cookie 會與監視器相關聯。</span><span class="sxs-lookup"><span data-stu-id="691f3-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="691f3-128">如果呼叫這個方法的呼叫目前在與該監視相關聯的 cookie 上生效，則呼叫可能會封鎖監視器基礎的事件，但不會產生鎖死。</span><span class="sxs-lookup"><span data-stu-id="691f3-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="691f3-129">其他工作也可能會在嘗試取得此監視器時封鎖。</span><span class="sxs-lookup"><span data-stu-id="691f3-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="691f3-130">`GetMonitorOwner` 一律會立即傳回，而且可以在呼叫之後隨時呼叫 `CreateMonitorEvent` 。</span><span class="sxs-lookup"><span data-stu-id="691f3-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="691f3-131">主機不需要等到工作正在等候事件。</span><span class="sxs-lookup"><span data-stu-id="691f3-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="691f3-132">需求</span><span class="sxs-lookup"><span data-stu-id="691f3-132">Requirements</span></span>  

 <span data-ttu-id="691f3-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="691f3-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="691f3-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="691f3-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="691f3-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="691f3-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="691f3-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="691f3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691f3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="691f3-137">See also</span></span>

- [<span data-ttu-id="691f3-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="691f3-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="691f3-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="691f3-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
