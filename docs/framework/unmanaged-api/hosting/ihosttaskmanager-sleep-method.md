---
title: IHostTaskManager::Sleep 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e4be8681cd32b91a9084cda14651ac253507356
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498753"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="b6d2c-102">IHostTaskManager::Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="b6d2c-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="b6d2c-103">將目前的工作會進入睡眠會告知主應用程式。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6d2c-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6d2c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6d2c-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="b6d2c-106">[in]時間間隔，以毫秒為單位，執行緒會進入睡眠狀態。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="b6d2c-107">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)列舉值，表示如果這個，主應用程式應執行的動作動作區塊。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6d2c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6d2c-108">Return Value</span></span>  
  
|<span data-ttu-id="b6d2c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6d2c-109">HRESULT</span></span>|<span data-ttu-id="b6d2c-110">描述</span><span class="sxs-lookup"><span data-stu-id="b6d2c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6d2c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6d2c-111">S_OK</span></span>|<span data-ttu-id="b6d2c-112">`Sleep` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="b6d2c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6d2c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6d2c-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b6d2c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b6d2c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b6d2c-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-116">The call timed out.</span></span>|  
|<span data-ttu-id="b6d2c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b6d2c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b6d2c-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b6d2c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b6d2c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b6d2c-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b6d2c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6d2c-121">E_FAIL</span></span>|<span data-ttu-id="b6d2c-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b6d2c-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b6d2c-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6d2c-125">備註</span><span class="sxs-lookup"><span data-stu-id="b6d2c-125">Remarks</span></span>  
 <span data-ttu-id="b6d2c-126">CLR 通常會呼叫`IHostTaskManager::Sleep`當<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>從使用者程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d2c-127">需求</span><span class="sxs-lookup"><span data-stu-id="b6d2c-127">Requirements</span></span>  
 <span data-ttu-id="b6d2c-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d2c-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6d2c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6d2c-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6d2c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6d2c-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d2c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d2c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d2c-132">See also</span></span>
- [<span data-ttu-id="b6d2c-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b6d2c-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b6d2c-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6d2c-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b6d2c-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b6d2c-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b6d2c-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6d2c-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
