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
ms.openlocfilehash: 13e4119da7af4c54387c24ee576ff9577da56ca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438037"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="939db-102">ICLRTask::SwitchIn 方法</span><span class="sxs-lookup"><span data-stu-id="939db-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="939db-103">會告知 common language runtime (CLR) 的工作，目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體表示現在處於運作狀態。</span><span class="sxs-lookup"><span data-stu-id="939db-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="939db-104">語法</span><span class="sxs-lookup"><span data-stu-id="939db-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="939db-105">參數</span><span class="sxs-lookup"><span data-stu-id="939db-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="939db-106">[in]在實體執行緒代表由目前的工作的控制代碼`ICLRTask`執行個體正在執行。</span><span class="sxs-lookup"><span data-stu-id="939db-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="939db-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="939db-107">Return Value</span></span>  
  
|<span data-ttu-id="939db-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="939db-108">HRESULT</span></span>|<span data-ttu-id="939db-109">描述</span><span class="sxs-lookup"><span data-stu-id="939db-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="939db-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="939db-110">S_OK</span></span>|<span data-ttu-id="939db-111">`SwitchIn` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="939db-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="939db-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="939db-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="939db-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="939db-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="939db-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="939db-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="939db-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="939db-115">The call timed out.</span></span>|  
|<span data-ttu-id="939db-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="939db-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="939db-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="939db-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="939db-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="939db-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="939db-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="939db-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="939db-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="939db-120">E_FAIL</span></span>|<span data-ttu-id="939db-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="939db-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="939db-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="939db-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="939db-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="939db-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="939db-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="939db-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="939db-125">`SwitchIn` 呼叫之前呼叫未[SwitchOut 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)。</span><span class="sxs-lookup"><span data-stu-id="939db-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="939db-126">備註</span><span class="sxs-lookup"><span data-stu-id="939db-126">Remarks</span></span>  
 <span data-ttu-id="939db-127">`threadHandle`參數表示控制代碼所在工作由目前的作業系統執行緒`ICLRTask`已排程執行個體。</span><span class="sxs-lookup"><span data-stu-id="939db-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="939db-128">如果已在此執行緒上發生模擬，您必須呼叫[ihostsecuritymanager:: Reverttoself](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)之前切換移入工作。</span><span class="sxs-lookup"><span data-stu-id="939db-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="939db-129">呼叫`SwitchIn`之前呼叫沒有`SwitchOut`因 HOST_E_INVALIDOPERATION 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="939db-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="939db-130">需求</span><span class="sxs-lookup"><span data-stu-id="939db-130">Requirements</span></span>  
 <span data-ttu-id="939db-131">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="939db-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="939db-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="939db-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="939db-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="939db-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="939db-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="939db-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939db-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="939db-135">See Also</span></span>  
 [<span data-ttu-id="939db-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="939db-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="939db-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="939db-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="939db-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="939db-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="939db-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="939db-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
