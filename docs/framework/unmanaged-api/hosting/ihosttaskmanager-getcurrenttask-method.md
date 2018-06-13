---
title: IHostTaskManager::GetCurrentTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2420ddb5cf9be2cfb08f89d27d9aa277305e7ffb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442688"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="f66a5-102">IHostTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="f66a5-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="f66a5-103">取得目前正在進行這個呼叫時之作業系統執行緒上執行工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f66a5-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f66a5-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f66a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="f66a5-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="f66a5-106">[out]位址指標[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)代表目前正在執行的工作或 null，如果沒有工作正在執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f66a5-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f66a5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f66a5-107">Return Value</span></span>  
  
|<span data-ttu-id="f66a5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f66a5-108">HRESULT</span></span>|<span data-ttu-id="f66a5-109">描述</span><span class="sxs-lookup"><span data-stu-id="f66a5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f66a5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f66a5-110">S_OK</span></span>|<span data-ttu-id="f66a5-111">`GetCurrentTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f66a5-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="f66a5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f66a5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f66a5-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f66a5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f66a5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f66a5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f66a5-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f66a5-115">The call timed out.</span></span>|  
|<span data-ttu-id="f66a5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f66a5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f66a5-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f66a5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f66a5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f66a5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f66a5-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f66a5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f66a5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f66a5-120">E_FAIL</span></span>|<span data-ttu-id="f66a5-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f66a5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f66a5-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f66a5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f66a5-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f66a5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f66a5-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="f66a5-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="f66a5-125">`GetCurrentTask` 主機的控制之外的作業系統執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="f66a5-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f66a5-126">備註</span><span class="sxs-lookup"><span data-stu-id="f66a5-126">Remarks</span></span>  
 <span data-ttu-id="f66a5-127">主機也可以設定`pTask`參數為 null 進入 CLR 時，防止它並未初始化工作。</span><span class="sxs-lookup"><span data-stu-id="f66a5-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f66a5-128">需求</span><span class="sxs-lookup"><span data-stu-id="f66a5-128">Requirements</span></span>  
 <span data-ttu-id="f66a5-129">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f66a5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f66a5-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f66a5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f66a5-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f66a5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f66a5-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f66a5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66a5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f66a5-133">See Also</span></span>  
 [<span data-ttu-id="f66a5-134">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f66a5-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f66a5-135">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f66a5-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f66a5-136">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f66a5-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f66a5-137">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f66a5-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
