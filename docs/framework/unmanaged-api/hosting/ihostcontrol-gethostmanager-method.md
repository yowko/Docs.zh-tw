---
title: IHostControl::GetHostManager 方法
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: 25e931ec17cad3508d548fb4ca7e53b0ade3f119
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804960"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="e9daa-102">IHostControl::GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="e9daa-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="e9daa-103">取得具有指定之之介面的主機介面指標 `IID` 。</span><span class="sxs-lookup"><span data-stu-id="e9daa-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9daa-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9daa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9daa-105">參數</span><span class="sxs-lookup"><span data-stu-id="e9daa-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="e9daa-106">在`IID`Common language runtime （CLR）所查詢之介面的。</span><span class="sxs-lookup"><span data-stu-id="e9daa-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="e9daa-107">脫銷主機實介面的指標，如果主機不支援這個介面，則為 null。</span><span class="sxs-lookup"><span data-stu-id="e9daa-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9daa-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e9daa-108">Return Value</span></span>  
  
|<span data-ttu-id="e9daa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9daa-109">HRESULT</span></span>|<span data-ttu-id="e9daa-110">描述</span><span class="sxs-lookup"><span data-stu-id="e9daa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9daa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9daa-111">S_OK</span></span>|<span data-ttu-id="e9daa-112">`GetHostManager`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e9daa-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="e9daa-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9daa-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9daa-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e9daa-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9daa-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9daa-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9daa-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e9daa-116">The call timed out.</span></span>|  
|<span data-ttu-id="e9daa-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9daa-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9daa-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e9daa-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9daa-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9daa-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9daa-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e9daa-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9daa-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9daa-121">E_FAIL</span></span>|<span data-ttu-id="e9daa-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e9daa-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9daa-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="e9daa-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9daa-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e9daa-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e9daa-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e9daa-125">E_INVALIDARG</span></span>|<span data-ttu-id="e9daa-126">要求的無效 `IID` 。</span><span class="sxs-lookup"><span data-stu-id="e9daa-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="e9daa-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="e9daa-127">E_NOINTERFACE</span></span>|<span data-ttu-id="e9daa-128">不支援要求的介面。</span><span class="sxs-lookup"><span data-stu-id="e9daa-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9daa-129">備註</span><span class="sxs-lookup"><span data-stu-id="e9daa-129">Remarks</span></span>  
 <span data-ttu-id="e9daa-130">CLR 會查詢主機，以判斷它是否支援下列一個或多個介面：</span><span class="sxs-lookup"><span data-stu-id="e9daa-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="e9daa-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-131">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="e9daa-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-132">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="e9daa-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-133">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="e9daa-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-134">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="e9daa-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-135">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="e9daa-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-136">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="e9daa-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-137">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="e9daa-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-138">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="e9daa-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="e9daa-139">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="e9daa-140">如果主機支援指定的介面，它會將設定 `ppObject` 為該介面的執行。</span><span class="sxs-lookup"><span data-stu-id="e9daa-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="e9daa-141">否則，它會將設定 `ppObject` 為 null。</span><span class="sxs-lookup"><span data-stu-id="e9daa-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="e9daa-142">CLR 不會呼叫 `Release` 主機管理員，即使您將它關閉也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e9daa-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9daa-143">規格需求</span><span class="sxs-lookup"><span data-stu-id="e9daa-143">Requirements</span></span>  
 <span data-ttu-id="e9daa-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9daa-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9daa-145">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e9daa-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9daa-146">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e9daa-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9daa-147">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9daa-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9daa-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9daa-148">See also</span></span>

- [<span data-ttu-id="e9daa-149">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="e9daa-149">IHostControl Interface</span></span>](ihostcontrol-interface.md)
