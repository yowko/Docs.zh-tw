---
title: "IHostSemaphore::Wait 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15c86ee8b1de22f07b01290f5a830afd95427ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="9d208-102">IHostSemaphore::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="9d208-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="9d208-103">造成目前[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)等候，直到它擁有的執行個體或指定的經過時間量。</span><span class="sxs-lookup"><span data-stu-id="9d208-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d208-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d208-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d208-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d208-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="9d208-106">[in]如果在傳回之前等候的毫秒數目前`IHostSemaphore`不屬於執行個體。</span><span class="sxs-lookup"><span data-stu-id="9d208-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="9d208-107">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指定哪些主機應該的採取此作業的區塊。</span><span class="sxs-lookup"><span data-stu-id="9d208-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d208-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9d208-108">Return Value</span></span>  
  
|<span data-ttu-id="9d208-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d208-109">HRESULT</span></span>|<span data-ttu-id="9d208-110">描述</span><span class="sxs-lookup"><span data-stu-id="9d208-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d208-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d208-111">S_OK</span></span>|<span data-ttu-id="9d208-112">`Wait`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9d208-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="9d208-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d208-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d208-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9d208-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d208-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d208-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d208-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="9d208-116">The call timed out.</span></span>|  
|<span data-ttu-id="9d208-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d208-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d208-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9d208-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d208-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d208-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d208-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="9d208-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d208-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d208-121">E_FAIL</span></span>|<span data-ttu-id="9d208-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9d208-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d208-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="9d208-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d208-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9d208-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d208-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="9d208-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="9d208-126">主機的等候時間間隔內偵測到死結，並選擇 目前`IHostSemaphore`作為死結的犧牲者的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9d208-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d208-127">需求</span><span class="sxs-lookup"><span data-stu-id="9d208-127">Requirements</span></span>  
 <span data-ttu-id="9d208-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d208-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d208-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d208-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d208-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9d208-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d208-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d208-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d208-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="9d208-132">See Also</span></span>  
 [<span data-ttu-id="9d208-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9d208-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9d208-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9d208-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9d208-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9d208-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="9d208-136">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="9d208-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="9d208-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9d208-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
