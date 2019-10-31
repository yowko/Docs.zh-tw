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
ms.openlocfilehash: fbfd44c8e20bc75638d6356fe405f02790da8ac7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124611"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="bba4e-102">ICLRTask::SwitchIn 方法</span><span class="sxs-lookup"><span data-stu-id="bba4e-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="bba4e-103">通知 common language runtime （CLR）目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例所代表的工作現在處於可運作狀態。</span><span class="sxs-lookup"><span data-stu-id="bba4e-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="bba4e-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bba4e-105">參數</span><span class="sxs-lookup"><span data-stu-id="bba4e-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="bba4e-106">在目前 `ICLRTask` 實例所代表之工作執行所在之實體執行緒的控制碼。</span><span class="sxs-lookup"><span data-stu-id="bba4e-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bba4e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bba4e-107">Return Value</span></span>  
  
|<span data-ttu-id="bba4e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bba4e-108">HRESULT</span></span>|<span data-ttu-id="bba4e-109">描述</span><span class="sxs-lookup"><span data-stu-id="bba4e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bba4e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bba4e-110">S_OK</span></span>|<span data-ttu-id="bba4e-111">已成功傳回 `SwitchIn`。</span><span class="sxs-lookup"><span data-stu-id="bba4e-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="bba4e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bba4e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bba4e-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="bba4e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bba4e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bba4e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bba4e-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="bba4e-115">The call timed out.</span></span>|  
|<span data-ttu-id="bba4e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bba4e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bba4e-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bba4e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bba4e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bba4e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bba4e-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="bba4e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bba4e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bba4e-120">E_FAIL</span></span>|<span data-ttu-id="bba4e-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="bba4e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bba4e-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="bba4e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bba4e-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bba4e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bba4e-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="bba4e-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="bba4e-125">在沒有先前呼叫[SwitchOut 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)的情況下，呼叫了 `SwitchIn`。</span><span class="sxs-lookup"><span data-stu-id="bba4e-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bba4e-126">備註</span><span class="sxs-lookup"><span data-stu-id="bba4e-126">Remarks</span></span>  
 <span data-ttu-id="bba4e-127">`threadHandle` 參數代表已排程目前 `ICLRTask` 實例所代表之工作的作業系統執行緒控制碼。</span><span class="sxs-lookup"><span data-stu-id="bba4e-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="bba4e-128">如果此執行緒發生模擬，您必須先呼叫[IHostSecurityManager：： RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) ，才能在工作中切換。</span><span class="sxs-lookup"><span data-stu-id="bba4e-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bba4e-129">呼叫沒有先前呼叫 `SwitchOut` 的 `SwitchIn` 會失敗，並出現 HOST_E_INVALIDOPERATION 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="bba4e-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba4e-130">需求</span><span class="sxs-lookup"><span data-stu-id="bba4e-130">Requirements</span></span>  
 <span data-ttu-id="bba4e-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bba4e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba4e-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="bba4e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bba4e-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bba4e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bba4e-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bba4e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba4e-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="bba4e-135">See also</span></span>

- [<span data-ttu-id="bba4e-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="bba4e-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bba4e-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bba4e-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bba4e-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="bba4e-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bba4e-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bba4e-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
