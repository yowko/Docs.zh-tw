---
title: "IHostManualEvent::Wait 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Wait
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2bd584e1ada69adca7f8ef77f98533ef7a1ba16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="b954e-102">IHostManualEvent::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="b954e-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="b954e-103">造成目前[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)等候，直到它擁有，執行個體或指定的經過時間量。</span><span class="sxs-lookup"><span data-stu-id="b954e-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b954e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b954e-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b954e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b954e-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="b954e-106">[in]如果在傳回之前等候的毫秒數目前`IHostManualEvent`不屬於執行個體。</span><span class="sxs-lookup"><span data-stu-id="b954e-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="b954e-107">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，表示主應用程式應該的採取此作業的區塊。</span><span class="sxs-lookup"><span data-stu-id="b954e-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b954e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b954e-108">Return Value</span></span>  
  
|<span data-ttu-id="b954e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b954e-109">HRESULT</span></span>|<span data-ttu-id="b954e-110">描述</span><span class="sxs-lookup"><span data-stu-id="b954e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b954e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b954e-111">S_OK</span></span>|<span data-ttu-id="b954e-112">`Wait`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b954e-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="b954e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b954e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b954e-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b954e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b954e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b954e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b954e-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b954e-116">The call timed out.</span></span>|  
|<span data-ttu-id="b954e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b954e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b954e-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b954e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b954e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b954e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b954e-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b954e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b954e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b954e-121">E_FAIL</span></span>|<span data-ttu-id="b954e-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b954e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b954e-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="b954e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b954e-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b954e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b954e-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="b954e-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="b954e-126">主機的等候時間間隔內偵測到死結，並選擇 目前`IHostManualEvent`為死結的犧牲者的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b954e-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b954e-127">需求</span><span class="sxs-lookup"><span data-stu-id="b954e-127">Requirements</span></span>  
 <span data-ttu-id="b954e-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b954e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b954e-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b954e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b954e-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b954e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b954e-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b954e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b954e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b954e-132">See Also</span></span>  
 [<span data-ttu-id="b954e-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b954e-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="b954e-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b954e-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="b954e-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b954e-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="b954e-136">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="b954e-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="b954e-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b954e-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
