---
title: "IHostTask::Join 方法"
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
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 85ee44fe9185364a6870b996ca98cfe6cc297bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="998e8-102">IHostTask::Join 方法</span><span class="sxs-lookup"><span data-stu-id="998e8-102">IHostTask::Join Method</span></span>
<span data-ttu-id="998e8-103">表示由目前的工作之前會封鎖呼叫工作[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體完成，已超過指定的時間間隔，或[ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="998e8-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="998e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="998e8-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="998e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="998e8-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="998e8-106">[in]時間間隔，以毫秒為單位，等候工作結束。</span><span class="sxs-lookup"><span data-stu-id="998e8-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="998e8-107">如果在工作結束之前，經過此間隔，會解除封鎖呼叫的工作。</span><span class="sxs-lookup"><span data-stu-id="998e8-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="998e8-108">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="998e8-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="998e8-109">WAIT_ALERTABLE 值會指示要喚醒工作，如果主機`Alert`之前，會呼叫`milliseconds`捨棄。</span><span class="sxs-lookup"><span data-stu-id="998e8-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="998e8-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="998e8-110">Return Value</span></span>  
  
|<span data-ttu-id="998e8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="998e8-111">HRESULT</span></span>|<span data-ttu-id="998e8-112">描述</span><span class="sxs-lookup"><span data-stu-id="998e8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="998e8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="998e8-113">S_OK</span></span>|<span data-ttu-id="998e8-114">`Join`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="998e8-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="998e8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="998e8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="998e8-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="998e8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="998e8-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="998e8-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="998e8-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="998e8-118">The call timed out.</span></span>|  
|<span data-ttu-id="998e8-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="998e8-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="998e8-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="998e8-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="998e8-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="998e8-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="998e8-122">事件已取消時封鎖的執行緒或 fiber，或目前等候`IHostTask`執行個體不是與工作相關聯。</span><span class="sxs-lookup"><span data-stu-id="998e8-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="998e8-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="998e8-123">E_FAIL</span></span>|<span data-ttu-id="998e8-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="998e8-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="998e8-125">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="998e8-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="998e8-126">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="998e8-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="998e8-127">需求</span><span class="sxs-lookup"><span data-stu-id="998e8-127">Requirements</span></span>  
 <span data-ttu-id="998e8-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="998e8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="998e8-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="998e8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="998e8-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="998e8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="998e8-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="998e8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998e8-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="998e8-132">See Also</span></span>  
 [<span data-ttu-id="998e8-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="998e8-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="998e8-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="998e8-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="998e8-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="998e8-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="998e8-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="998e8-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="998e8-137">WAIT_OPTION 列舉</span><span class="sxs-lookup"><span data-stu-id="998e8-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
