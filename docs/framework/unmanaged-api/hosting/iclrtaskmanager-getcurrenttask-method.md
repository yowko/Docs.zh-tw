---
title: ICLRTaskManager::GetCurrentTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: a57610d1b41d80d54a245b9744aafd78a1e88177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195901"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="b2c62-102">ICLRTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="b2c62-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="b2c62-103">取得目前在執行方法呼叫之作業系統執行緒上執行的[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="b2c62-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c62-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2c62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2c62-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2c62-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="b2c62-106">脫銷目前在呼叫來源的作業系統執行緒上執行之 `ICLRTask` 實例的位址指標，如果此執行緒上目前沒有任何工作正在執行，則為 null。</span><span class="sxs-lookup"><span data-stu-id="b2c62-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2c62-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b2c62-107">Return Value</span></span>  
  
|<span data-ttu-id="b2c62-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2c62-108">HRESULT</span></span>|<span data-ttu-id="b2c62-109">描述</span><span class="sxs-lookup"><span data-stu-id="b2c62-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2c62-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2c62-110">S_OK</span></span>|<span data-ttu-id="b2c62-111">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="b2c62-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="b2c62-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2c62-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2c62-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2c62-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2c62-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2c62-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2c62-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b2c62-115">The call timed out.</span></span>|  
|<span data-ttu-id="b2c62-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2c62-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2c62-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b2c62-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2c62-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2c62-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2c62-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b2c62-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2c62-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2c62-120">E_FAIL</span></span>|<span data-ttu-id="b2c62-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b2c62-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2c62-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="b2c62-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2c62-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b2c62-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2c62-124">備註</span><span class="sxs-lookup"><span data-stu-id="b2c62-124">Remarks</span></span>  
 <span data-ttu-id="b2c62-125">`ppTask` 參數所指向的 `ICLRTask` 實例，代表 CLR 目前正在執行的工作。</span><span class="sxs-lookup"><span data-stu-id="b2c62-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="b2c62-126">`ICLRTask` 實例會與代表主機工作的對應[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例相關聯。</span><span class="sxs-lookup"><span data-stu-id="b2c62-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c62-127">需求</span><span class="sxs-lookup"><span data-stu-id="b2c62-127">Requirements</span></span>  
 <span data-ttu-id="b2c62-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2c62-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c62-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b2c62-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2c62-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b2c62-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2c62-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c62-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c62-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2c62-132">See also</span></span>

- [<span data-ttu-id="b2c62-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b2c62-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b2c62-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b2c62-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b2c62-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b2c62-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b2c62-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b2c62-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
