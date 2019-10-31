---
title: IHostTask::SetCLRTask 方法
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: bbb563a304e3ff7cdba3dfe7e394da9cf138ff10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121361"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="3b4cb-102">IHostTask::SetCLRTask 方法</span><span class="sxs-lookup"><span data-stu-id="3b4cb-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="3b4cb-103">將 `ICLRTask` 實例與目前的[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b4cb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b4cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b4cb-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="3b4cb-106">在要與目前 `IHostTask` 實例相關聯之 `ICLRTask` 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b4cb-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3b4cb-107">Return Value</span></span>  
  
|<span data-ttu-id="3b4cb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b4cb-108">HRESULT</span></span>|<span data-ttu-id="3b4cb-109">描述</span><span class="sxs-lookup"><span data-stu-id="3b4cb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b4cb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b4cb-110">S_OK</span></span>|<span data-ttu-id="3b4cb-111">已成功傳回 `SetCLRTask`。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="3b4cb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b4cb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b4cb-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b4cb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b4cb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b4cb-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-115">The call timed out.</span></span>|  
|<span data-ttu-id="3b4cb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b4cb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b4cb-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b4cb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b4cb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b4cb-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b4cb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b4cb-120">E_FAIL</span></span>|<span data-ttu-id="3b4cb-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3b4cb-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b4cb-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b4cb-124">備註</span><span class="sxs-lookup"><span data-stu-id="3b4cb-124">Remarks</span></span>  
 <span data-ttu-id="3b4cb-125">CLR 會呼叫 `SetCLRTask`，讓 `ICLRTask` 實例與目前的 `IHostTask` 實例產生關聯，這是由呼叫[IHostTaskManager：： CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)所建立。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b4cb-126">需求</span><span class="sxs-lookup"><span data-stu-id="3b4cb-126">Requirements</span></span>  
 <span data-ttu-id="3b4cb-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b4cb-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3b4cb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b4cb-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3b4cb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b4cb-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b4cb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4cb-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b4cb-131">See also</span></span>

- [<span data-ttu-id="3b4cb-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="3b4cb-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3b4cb-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="3b4cb-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3b4cb-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="3b4cb-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3b4cb-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="3b4cb-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
