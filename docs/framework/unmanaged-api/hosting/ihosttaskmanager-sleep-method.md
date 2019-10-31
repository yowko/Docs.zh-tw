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
ms.openlocfilehash: 7eedf052b6f2285799940b394d9891975230cb72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132934"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="8d934-102">IHostTaskManager::Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="8d934-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="8d934-103">通知主機目前的工作即將進入睡眠狀態。</span><span class="sxs-lookup"><span data-stu-id="8d934-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d934-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d934-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d934-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d934-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="8d934-106">在執行緒將進入睡眠狀態的時間間隔（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="8d934-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="8d934-107">在其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)列舉值，指出當此動作封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="8d934-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d934-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8d934-108">Return Value</span></span>  
  
|<span data-ttu-id="8d934-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d934-109">HRESULT</span></span>|<span data-ttu-id="8d934-110">描述</span><span class="sxs-lookup"><span data-stu-id="8d934-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d934-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d934-111">S_OK</span></span>|<span data-ttu-id="8d934-112">已成功傳回 `Sleep`。</span><span class="sxs-lookup"><span data-stu-id="8d934-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="8d934-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d934-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d934-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8d934-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d934-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d934-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d934-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8d934-116">The call timed out.</span></span>|  
|<span data-ttu-id="8d934-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d934-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d934-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8d934-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d934-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d934-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d934-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8d934-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d934-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d934-121">E_FAIL</span></span>|<span data-ttu-id="8d934-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8d934-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d934-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="8d934-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d934-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8d934-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d934-125">備註</span><span class="sxs-lookup"><span data-stu-id="8d934-125">Remarks</span></span>  
 <span data-ttu-id="8d934-126">在從使用者程式碼呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 時，CLR 通常會呼叫 `IHostTaskManager::Sleep`。</span><span class="sxs-lookup"><span data-stu-id="8d934-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d934-127">需求</span><span class="sxs-lookup"><span data-stu-id="8d934-127">Requirements</span></span>  
 <span data-ttu-id="8d934-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d934-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d934-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8d934-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d934-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d934-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d934-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d934-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d934-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d934-132">See also</span></span>

- [<span data-ttu-id="8d934-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="8d934-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8d934-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8d934-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8d934-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="8d934-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8d934-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8d934-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
