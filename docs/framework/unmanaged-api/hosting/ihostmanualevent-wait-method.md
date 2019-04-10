---
title: IHostManualEvent::Wait 方法
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f90bf2b7472af3f9125edbd29f6924ddec9c1530
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219989"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="b1491-102">IHostManualEvent::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="b1491-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="b1491-103">造成目前[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)等候，直到它所屬於的執行個體或指定的時間量。</span><span class="sxs-lookup"><span data-stu-id="b1491-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1491-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1491-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1491-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1491-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="b1491-106">[in]如果在傳回之前，等待的毫秒數目前`IHostManualEvent`不屬於執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1491-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="b1491-107">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指出主應用程式如果這個，應該採取的動作作業封鎖。</span><span class="sxs-lookup"><span data-stu-id="b1491-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1491-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1491-108">Return Value</span></span>  
  
|<span data-ttu-id="b1491-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1491-109">HRESULT</span></span>|<span data-ttu-id="b1491-110">描述</span><span class="sxs-lookup"><span data-stu-id="b1491-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1491-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1491-111">S_OK</span></span>|`Wait` <span data-ttu-id="b1491-112">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b1491-112">returned successfully.</span></span>|  
|<span data-ttu-id="b1491-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1491-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1491-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b1491-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1491-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1491-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1491-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b1491-116">The call timed out.</span></span>|  
|<span data-ttu-id="b1491-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1491-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1491-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b1491-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1491-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1491-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1491-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b1491-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1491-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1491-121">E_FAIL</span></span>|<span data-ttu-id="b1491-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1491-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1491-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b1491-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1491-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b1491-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1491-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="b1491-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="b1491-126">主機會等候時間間隔內偵測到死結，然後選擇 目前`IHostManualEvent`作為死結的犧牲者的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1491-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1491-127">需求</span><span class="sxs-lookup"><span data-stu-id="b1491-127">Requirements</span></span>  
 <span data-ttu-id="b1491-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1491-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1491-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1491-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1491-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b1491-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b1491-131">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b1491-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1491-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1491-132">See also</span></span>

- [<span data-ttu-id="b1491-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b1491-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b1491-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b1491-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="b1491-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b1491-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="b1491-136">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="b1491-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="b1491-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b1491-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
