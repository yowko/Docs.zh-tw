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
ms.openlocfilehash: e98ae17d55c74d32844da96137c258d076ebc2db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691050"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="a24a9-102">ICLRTask::SwitchIn 方法</span><span class="sxs-lookup"><span data-stu-id="a24a9-102">ICLRTask::SwitchIn Method</span></span>

<span data-ttu-id="a24a9-103">通知 common language runtime (CLR) 目前 [ICLRTask](iclrtask-interface.md) 實例所代表的工作現在處於可操作的狀態。</span><span class="sxs-lookup"><span data-stu-id="a24a9-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a24a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="a24a9-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a24a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="a24a9-105">Parameters</span></span>  

 `threadHandle`  
 <span data-ttu-id="a24a9-106">在實體執行緒的控制碼，目前實例所代表的工作正在其上 `ICLRTask` 執行。</span><span class="sxs-lookup"><span data-stu-id="a24a9-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a24a9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a24a9-107">Return Value</span></span>  
  
|<span data-ttu-id="a24a9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a24a9-108">HRESULT</span></span>|<span data-ttu-id="a24a9-109">描述</span><span class="sxs-lookup"><span data-stu-id="a24a9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a24a9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a24a9-110">S_OK</span></span>|<span data-ttu-id="a24a9-111">`SwitchIn` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a24a9-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="a24a9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a24a9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a24a9-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a24a9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a24a9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a24a9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a24a9-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="a24a9-115">The call timed out.</span></span>|  
|<span data-ttu-id="a24a9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a24a9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a24a9-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a24a9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a24a9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a24a9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a24a9-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="a24a9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a24a9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a24a9-120">E_FAIL</span></span>|<span data-ttu-id="a24a9-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a24a9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a24a9-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="a24a9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a24a9-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a24a9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a24a9-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a24a9-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a24a9-125">`SwitchIn` 在沒有先前呼叫 [SwitchOut 方法](iclrtask-switchout-method.md)的情況下呼叫。</span><span class="sxs-lookup"><span data-stu-id="a24a9-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a24a9-126">備註</span><span class="sxs-lookup"><span data-stu-id="a24a9-126">Remarks</span></span>  

 <span data-ttu-id="a24a9-127">`threadHandle`參數代表作業系統執行緒的控制碼，此控制碼已排程目前實例所代表的工作 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="a24a9-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="a24a9-128">如果此執行緒上發生模擬，您必須先呼叫 [IHostSecurityManager：： RevertToSelf](ihostsecuritymanager-reverttoself-method.md) ，才能在工作中切換。</span><span class="sxs-lookup"><span data-stu-id="a24a9-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a24a9-129">`SwitchIn`沒有先前呼叫的呼叫 `SwitchOut` 會失敗，並出現 HOST_E_INVALIDOPERATION 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="a24a9-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a24a9-130">需求</span><span class="sxs-lookup"><span data-stu-id="a24a9-130">Requirements</span></span>  

 <span data-ttu-id="a24a9-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a24a9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a24a9-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a24a9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a24a9-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a24a9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a24a9-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a24a9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24a9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a24a9-135">See also</span></span>

- [<span data-ttu-id="a24a9-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a24a9-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a24a9-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a24a9-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a24a9-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a24a9-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a24a9-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a24a9-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
