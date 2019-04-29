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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db333cd97963ca8ef26673c0ba5cbf352fa331b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763408"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="68a03-102">ICLRTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="68a03-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="68a03-103">取得[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)目前方法呼叫所起始的作業系統執行緒執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68a03-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68a03-104">語法</span><span class="sxs-lookup"><span data-stu-id="68a03-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68a03-105">參數</span><span class="sxs-lookup"><span data-stu-id="68a03-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="68a03-106">[out]位址指標`ICLRTask`從中產生呼叫，作業系統執行緒目前正在執行的執行個體或 null，如果沒有工作正在執行這個執行緒上。</span><span class="sxs-lookup"><span data-stu-id="68a03-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68a03-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="68a03-107">Return Value</span></span>  
  
|<span data-ttu-id="68a03-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68a03-108">HRESULT</span></span>|<span data-ttu-id="68a03-109">描述</span><span class="sxs-lookup"><span data-stu-id="68a03-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68a03-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="68a03-110">S_OK</span></span>|<span data-ttu-id="68a03-111">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="68a03-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="68a03-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68a03-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68a03-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="68a03-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="68a03-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="68a03-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="68a03-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="68a03-115">The call timed out.</span></span>|  
|<span data-ttu-id="68a03-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="68a03-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="68a03-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="68a03-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="68a03-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="68a03-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="68a03-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="68a03-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="68a03-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68a03-120">E_FAIL</span></span>|<span data-ttu-id="68a03-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="68a03-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="68a03-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="68a03-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="68a03-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="68a03-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68a03-124">備註</span><span class="sxs-lookup"><span data-stu-id="68a03-124">Remarks</span></span>  
 <span data-ttu-id="68a03-125">`ICLRTask`執行個體`ppTask`參數指向表示目前執行之工作的 CLR。</span><span class="sxs-lookup"><span data-stu-id="68a03-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="68a03-126">`ICLRTask`執行個體是否與對應相關聯[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)表示工作主機的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68a03-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68a03-127">需求</span><span class="sxs-lookup"><span data-stu-id="68a03-127">Requirements</span></span>  
 <span data-ttu-id="68a03-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68a03-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68a03-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="68a03-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68a03-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="68a03-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68a03-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68a03-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a03-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68a03-132">See also</span></span>

- [<span data-ttu-id="68a03-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="68a03-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="68a03-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="68a03-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="68a03-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="68a03-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="68a03-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="68a03-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
