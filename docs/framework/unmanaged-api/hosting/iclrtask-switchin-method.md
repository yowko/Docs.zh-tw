---
title: ICLRTask::SwitchIn 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f36a963417aba082667bb9fb609e0d1dcad7b09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763447"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="fc140-102">ICLRTask::SwitchIn 方法</span><span class="sxs-lookup"><span data-stu-id="fc140-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="fc140-103">會告知 common language runtime (CLR)，工作的目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體表示現在處於運作狀態。</span><span class="sxs-lookup"><span data-stu-id="fc140-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc140-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc140-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc140-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc140-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="fc140-106">[in]實體代表由目前的工作的執行緒的控制代碼`ICLRTask`執行個體正在執行。</span><span class="sxs-lookup"><span data-stu-id="fc140-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc140-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc140-107">Return Value</span></span>  
  
|<span data-ttu-id="fc140-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc140-108">HRESULT</span></span>|<span data-ttu-id="fc140-109">描述</span><span class="sxs-lookup"><span data-stu-id="fc140-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc140-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc140-110">S_OK</span></span>|<span data-ttu-id="fc140-111">`SwitchIn` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fc140-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="fc140-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc140-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc140-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fc140-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc140-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc140-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc140-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fc140-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc140-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc140-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc140-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fc140-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc140-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc140-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc140-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fc140-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc140-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc140-120">E_FAIL</span></span>|<span data-ttu-id="fc140-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc140-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc140-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="fc140-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc140-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fc140-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fc140-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="fc140-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="fc140-125">`SwitchIn` 呼叫之前呼叫[SwitchOut 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)。</span><span class="sxs-lookup"><span data-stu-id="fc140-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc140-126">備註</span><span class="sxs-lookup"><span data-stu-id="fc140-126">Remarks</span></span>  
 <span data-ttu-id="fc140-127">`threadHandle`參數表示的控制代碼，以工作表示由目前所在之作業系統執行緒`ICLRTask`已排定執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc140-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="fc140-128">如果這個執行緒上已發生模擬，您必須呼叫[ihostsecuritymanager:: Reverttoself](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)之前切換移入工作。</span><span class="sxs-lookup"><span data-stu-id="fc140-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc140-129">呼叫`SwitchIn`而不需要先前呼叫`SwitchOut`因 HOST_E_INVALIDOPERATION HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="fc140-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc140-130">需求</span><span class="sxs-lookup"><span data-stu-id="fc140-130">Requirements</span></span>  
 <span data-ttu-id="fc140-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc140-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc140-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc140-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc140-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fc140-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc140-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc140-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc140-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc140-135">See also</span></span>

- [<span data-ttu-id="fc140-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fc140-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fc140-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fc140-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fc140-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fc140-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fc140-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fc140-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
