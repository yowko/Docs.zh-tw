---
title: IHostTask::Join 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4373fc4e8a4c414c40e8d3c5547b5998b9300348
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170753"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="2638d-102">IHostTask::Join 方法</span><span class="sxs-lookup"><span data-stu-id="2638d-102">IHostTask::Join Method</span></span>
<span data-ttu-id="2638d-103">表示由目前的工作之前會封鎖呼叫的工作[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體完成後，將指定的時間間隔過去後，或[ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="2638d-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2638d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2638d-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2638d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2638d-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="2638d-106">[in]時間間隔，以毫秒為單位，等候工作結束。</span><span class="sxs-lookup"><span data-stu-id="2638d-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="2638d-107">如果在工作結束之前，經過此間隔，會解除封鎖呼叫的工作。</span><span class="sxs-lookup"><span data-stu-id="2638d-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="2638d-108">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="2638d-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="2638d-109">WAIT_ALERTABLE 值會指示要喚醒工作，如果主機`Alert`之前，會呼叫`milliseconds`耗盡。</span><span class="sxs-lookup"><span data-stu-id="2638d-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2638d-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="2638d-110">Return Value</span></span>  
  
|<span data-ttu-id="2638d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2638d-111">HRESULT</span></span>|<span data-ttu-id="2638d-112">描述</span><span class="sxs-lookup"><span data-stu-id="2638d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2638d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2638d-113">S_OK</span></span>|<span data-ttu-id="2638d-114">`Join` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2638d-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="2638d-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2638d-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2638d-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2638d-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2638d-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2638d-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2638d-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2638d-118">The call timed out.</span></span>|  
|<span data-ttu-id="2638d-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2638d-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2638d-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2638d-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2638d-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2638d-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2638d-122">事件已取消時已封鎖的執行緒或 fiber 等候它，或目前`IHostTask`執行個體不是與工作相關聯。</span><span class="sxs-lookup"><span data-stu-id="2638d-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="2638d-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2638d-123">E_FAIL</span></span>|<span data-ttu-id="2638d-124">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="2638d-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2638d-125">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="2638d-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2638d-126">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2638d-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2638d-127">需求</span><span class="sxs-lookup"><span data-stu-id="2638d-127">Requirements</span></span>  
 <span data-ttu-id="2638d-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2638d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2638d-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2638d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2638d-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2638d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2638d-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2638d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2638d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2638d-132">See also</span></span>

- [<span data-ttu-id="2638d-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="2638d-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2638d-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2638d-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2638d-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="2638d-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2638d-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2638d-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="2638d-137">WAIT_OPTION 列舉</span><span class="sxs-lookup"><span data-stu-id="2638d-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
