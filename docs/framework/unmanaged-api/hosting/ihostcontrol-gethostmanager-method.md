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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e51ff24698a2839972f9a36eac6c18d4f6709ebd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600155"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="80cdc-102">IHostControl::GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="80cdc-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="80cdc-103">取得主機的介面實作的介面指標，具有指定`IID`。</span><span class="sxs-lookup"><span data-stu-id="80cdc-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80cdc-104">語法</span><span class="sxs-lookup"><span data-stu-id="80cdc-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80cdc-105">參數</span><span class="sxs-lookup"><span data-stu-id="80cdc-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="80cdc-106">[in]`IID` Common language runtime (CLR) 查詢的介面。</span><span class="sxs-lookup"><span data-stu-id="80cdc-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="80cdc-107">[out]主機實作的介面或如果主機不支援此介面為 null 指標。</span><span class="sxs-lookup"><span data-stu-id="80cdc-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80cdc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="80cdc-108">Return Value</span></span>  
  
|<span data-ttu-id="80cdc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80cdc-109">HRESULT</span></span>|<span data-ttu-id="80cdc-110">描述</span><span class="sxs-lookup"><span data-stu-id="80cdc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80cdc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="80cdc-111">S_OK</span></span>|<span data-ttu-id="80cdc-112">`GetHostManager` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="80cdc-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="80cdc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80cdc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80cdc-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="80cdc-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80cdc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80cdc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80cdc-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="80cdc-116">The call timed out.</span></span>|  
|<span data-ttu-id="80cdc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80cdc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80cdc-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="80cdc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80cdc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80cdc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80cdc-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="80cdc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80cdc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80cdc-121">E_FAIL</span></span>|<span data-ttu-id="80cdc-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="80cdc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80cdc-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="80cdc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80cdc-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="80cdc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="80cdc-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="80cdc-125">E_INVALIDARG</span></span>|<span data-ttu-id="80cdc-126">要求`IID`無效。</span><span class="sxs-lookup"><span data-stu-id="80cdc-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="80cdc-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="80cdc-127">E_NOINTERFACE</span></span>|<span data-ttu-id="80cdc-128">不支援要求的介面。</span><span class="sxs-lookup"><span data-stu-id="80cdc-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80cdc-129">備註</span><span class="sxs-lookup"><span data-stu-id="80cdc-129">Remarks</span></span>  
 <span data-ttu-id="80cdc-130">CLR 會查詢主機判斷它是否支援一或多個下列介面：</span><span class="sxs-lookup"><span data-stu-id="80cdc-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="80cdc-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="80cdc-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="80cdc-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="80cdc-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="80cdc-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="80cdc-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="80cdc-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="80cdc-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="80cdc-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="80cdc-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="80cdc-140">如果主機支援指定的介面，它會設定`ppObject`到它的實作該介面。</span><span class="sxs-lookup"><span data-stu-id="80cdc-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="80cdc-141">否則，它會設定`ppObject`為 null。</span><span class="sxs-lookup"><span data-stu-id="80cdc-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="80cdc-142">CLR 不會呼叫`Release`主應用程式管理員，即使您關閉上。</span><span class="sxs-lookup"><span data-stu-id="80cdc-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80cdc-143">需求</span><span class="sxs-lookup"><span data-stu-id="80cdc-143">Requirements</span></span>  
 <span data-ttu-id="80cdc-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80cdc-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80cdc-145">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80cdc-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80cdc-146">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80cdc-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80cdc-147">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80cdc-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80cdc-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80cdc-148">See also</span></span>

- [<span data-ttu-id="80cdc-149">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="80cdc-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
