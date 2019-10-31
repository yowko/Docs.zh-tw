---
title: IHostSemaphore::Wait 方法
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: bf09f7bc6c3e3aabfc16f9cad277c46be024b01d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139447"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="78cfd-102">IHostSemaphore::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="78cfd-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="78cfd-103">導致目前的[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)實例等到其擁有或指定的時間量經過之後，才會等候。</span><span class="sxs-lookup"><span data-stu-id="78cfd-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cfd-104">語法</span><span class="sxs-lookup"><span data-stu-id="78cfd-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78cfd-105">參數</span><span class="sxs-lookup"><span data-stu-id="78cfd-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="78cfd-106">在如果目前的 `IHostSemaphore` 實例不是擁有的，則傳回之前要等候的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="78cfd-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="78cfd-107">在其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指定當此作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="78cfd-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78cfd-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="78cfd-108">Return Value</span></span>  
  
|<span data-ttu-id="78cfd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78cfd-109">HRESULT</span></span>|<span data-ttu-id="78cfd-110">描述</span><span class="sxs-lookup"><span data-stu-id="78cfd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78cfd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="78cfd-111">S_OK</span></span>|<span data-ttu-id="78cfd-112">已成功傳回 `Wait`。</span><span class="sxs-lookup"><span data-stu-id="78cfd-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="78cfd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78cfd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78cfd-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="78cfd-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78cfd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78cfd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78cfd-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="78cfd-116">The call timed out.</span></span>|  
|<span data-ttu-id="78cfd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78cfd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78cfd-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="78cfd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78cfd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78cfd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78cfd-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="78cfd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78cfd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78cfd-121">E_FAIL</span></span>|<span data-ttu-id="78cfd-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="78cfd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78cfd-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="78cfd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78cfd-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="78cfd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78cfd-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="78cfd-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="78cfd-126">主機在等候間隔期間偵測到鎖死，並選擇目前的 `IHostSemaphore` 實例作為鎖死犧牲者。</span><span class="sxs-lookup"><span data-stu-id="78cfd-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78cfd-127">需求</span><span class="sxs-lookup"><span data-stu-id="78cfd-127">Requirements</span></span>  
 <span data-ttu-id="78cfd-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78cfd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cfd-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="78cfd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78cfd-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="78cfd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78cfd-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cfd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cfd-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="78cfd-132">See also</span></span>

- [<span data-ttu-id="78cfd-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="78cfd-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="78cfd-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="78cfd-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="78cfd-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="78cfd-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="78cfd-136">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="78cfd-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="78cfd-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="78cfd-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
