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
ms.openlocfilehash: e340dcb5dc093f965e6c08a24a3d65ed0aa6e07a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680816"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="50ca4-102">IHostControl::GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="50ca4-102">IHostControl::GetHostManager Method</span></span>

<span data-ttu-id="50ca4-103">取得具有指定之介面的主機實介面指標 `IID` 。</span><span class="sxs-lookup"><span data-stu-id="50ca4-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ca4-104">語法</span><span class="sxs-lookup"><span data-stu-id="50ca4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50ca4-105">參數</span><span class="sxs-lookup"><span data-stu-id="50ca4-105">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="50ca4-106">在 `IID` Common language runtime (CLR) 要查詢的介面。</span><span class="sxs-lookup"><span data-stu-id="50ca4-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="50ca4-107">擴展主機執行之介面的指標，如果主機不支援此介面，則為 null。</span><span class="sxs-lookup"><span data-stu-id="50ca4-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50ca4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="50ca4-108">Return Value</span></span>  
  
|<span data-ttu-id="50ca4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50ca4-109">HRESULT</span></span>|<span data-ttu-id="50ca4-110">描述</span><span class="sxs-lookup"><span data-stu-id="50ca4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50ca4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="50ca4-111">S_OK</span></span>|<span data-ttu-id="50ca4-112">`GetHostManager` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="50ca4-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="50ca4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50ca4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50ca4-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="50ca4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50ca4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50ca4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50ca4-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="50ca4-116">The call timed out.</span></span>|  
|<span data-ttu-id="50ca4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50ca4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50ca4-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="50ca4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50ca4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50ca4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50ca4-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="50ca4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50ca4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50ca4-121">E_FAIL</span></span>|<span data-ttu-id="50ca4-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="50ca4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50ca4-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="50ca4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50ca4-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="50ca4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="50ca4-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="50ca4-125">E_INVALIDARG</span></span>|<span data-ttu-id="50ca4-126">要求的無效 `IID` 。</span><span class="sxs-lookup"><span data-stu-id="50ca4-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="50ca4-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="50ca4-127">E_NOINTERFACE</span></span>|<span data-ttu-id="50ca4-128">不支援要求的介面。</span><span class="sxs-lookup"><span data-stu-id="50ca4-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50ca4-129">備註</span><span class="sxs-lookup"><span data-stu-id="50ca4-129">Remarks</span></span>  

 <span data-ttu-id="50ca4-130">CLR 會查詢主機，以判斷它是否支援下列一或多個介面：</span><span class="sxs-lookup"><span data-stu-id="50ca4-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="50ca4-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-131">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="50ca4-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-132">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="50ca4-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-133">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="50ca4-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-134">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="50ca4-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-135">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="50ca4-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-136">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="50ca4-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-137">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="50ca4-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-138">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="50ca4-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="50ca4-139">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="50ca4-140">如果主機支援指定的介面，則會將它設定 `ppObject` 為該介面的實作為。</span><span class="sxs-lookup"><span data-stu-id="50ca4-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="50ca4-141">否則，它會設定 `ppObject` 為 null。</span><span class="sxs-lookup"><span data-stu-id="50ca4-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="50ca4-142">即使您將它關閉，CLR 也不會呼叫 `Release` 主機管理員。</span><span class="sxs-lookup"><span data-stu-id="50ca4-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ca4-143">需求</span><span class="sxs-lookup"><span data-stu-id="50ca4-143">Requirements</span></span>  

 <span data-ttu-id="50ca4-144">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50ca4-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ca4-145">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="50ca4-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50ca4-146">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="50ca4-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50ca4-147">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ca4-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ca4-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50ca4-148">See also</span></span>

- [<span data-ttu-id="50ca4-149">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="50ca4-149">IHostControl Interface</span></span>](ihostcontrol-interface.md)
