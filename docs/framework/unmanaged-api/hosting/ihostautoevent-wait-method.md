---
title: "IHostAutoEvent::Wait 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent.Wait
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4646e0bd04d69e7fe0125740c9c6e0c1b014071
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="41bb8-102">IHostAutoEvent::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="41bb8-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="41bb8-103">造成目前[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)等候，直到它擁有的執行個體或指定的經過時間量。</span><span class="sxs-lookup"><span data-stu-id="41bb8-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41bb8-104">語法</span><span class="sxs-lookup"><span data-stu-id="41bb8-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41bb8-105">參數</span><span class="sxs-lookup"><span data-stu-id="41bb8-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="41bb8-106">[in]毫秒數目前`IHostAutoEvent`的執行個體應該等候後再傳回，如果沒有執行緒或 fiber 取得擁有權。</span><span class="sxs-lookup"><span data-stu-id="41bb8-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="41bb8-107">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指定主機應該的採取此作業的區塊。</span><span class="sxs-lookup"><span data-stu-id="41bb8-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41bb8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="41bb8-108">Return Value</span></span>  
  
|<span data-ttu-id="41bb8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41bb8-109">HRESULT</span></span>|<span data-ttu-id="41bb8-110">描述</span><span class="sxs-lookup"><span data-stu-id="41bb8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41bb8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="41bb8-111">S_OK</span></span>|<span data-ttu-id="41bb8-112">`Wait`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="41bb8-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="41bb8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41bb8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41bb8-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="41bb8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41bb8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41bb8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41bb8-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="41bb8-116">The call timed out.</span></span>|  
|<span data-ttu-id="41bb8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41bb8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41bb8-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="41bb8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41bb8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41bb8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41bb8-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="41bb8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41bb8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41bb8-121">E_FAIL</span></span>|<span data-ttu-id="41bb8-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="41bb8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41bb8-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="41bb8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41bb8-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="41bb8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="41bb8-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="41bb8-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="41bb8-126">主機的等候時間間隔內偵測到死結，並選擇代表由目前事件`IHostAutoEvent`為死結的犧牲者的執行個體。</span><span class="sxs-lookup"><span data-stu-id="41bb8-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41bb8-127">需求</span><span class="sxs-lookup"><span data-stu-id="41bb8-127">Requirements</span></span>  
 <span data-ttu-id="41bb8-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41bb8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41bb8-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41bb8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41bb8-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="41bb8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41bb8-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41bb8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bb8-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="41bb8-132">See Also</span></span>  
 [<span data-ttu-id="41bb8-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="41bb8-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="41bb8-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="41bb8-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="41bb8-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="41bb8-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="41bb8-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="41bb8-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
