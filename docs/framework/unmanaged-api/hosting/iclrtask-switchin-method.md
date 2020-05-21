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
ms.openlocfilehash: d8f57af459d1bb3f338cfbfcbb29f69f533ea927
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762925"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="d3796-102">ICLRTask::SwitchIn 方法</span><span class="sxs-lookup"><span data-stu-id="d3796-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="d3796-103">通知 common language runtime （CLR）目前[ICLRTask](iclrtask-interface.md)實例所代表的工作現在處於可運作狀態。</span><span class="sxs-lookup"><span data-stu-id="d3796-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3796-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3796-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3796-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3796-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="d3796-106">在目前實例所代表之工作執行所在之實體執行緒的控制碼 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="d3796-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3796-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d3796-107">Return Value</span></span>  
  
|<span data-ttu-id="d3796-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3796-108">HRESULT</span></span>|<span data-ttu-id="d3796-109">Description</span><span class="sxs-lookup"><span data-stu-id="d3796-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3796-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3796-110">S_OK</span></span>|<span data-ttu-id="d3796-111">`SwitchIn`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d3796-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="d3796-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d3796-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d3796-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d3796-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d3796-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d3796-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d3796-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d3796-115">The call timed out.</span></span>|  
|<span data-ttu-id="d3796-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d3796-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d3796-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d3796-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d3796-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d3796-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d3796-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d3796-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d3796-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d3796-120">E_FAIL</span></span>|<span data-ttu-id="d3796-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d3796-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d3796-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d3796-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d3796-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d3796-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d3796-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="d3796-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="d3796-125">`SwitchIn`在沒有先前呼叫[SwitchOut 方法](iclrtask-switchout-method.md)的情況下呼叫。</span><span class="sxs-lookup"><span data-stu-id="d3796-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3796-126">備註</span><span class="sxs-lookup"><span data-stu-id="d3796-126">Remarks</span></span>  
 <span data-ttu-id="d3796-127">`threadHandle`參數代表已排程目前實例所代表之工作的作業系統執行緒控制碼 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="d3796-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="d3796-128">如果此執行緒發生模擬，您必須先呼叫[IHostSecurityManager：： RevertToSelf](ihostsecuritymanager-reverttoself-method.md) ，才能在工作中切換。</span><span class="sxs-lookup"><span data-stu-id="d3796-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3796-129">呼叫 `SwitchIn` 而不使用先前的呼叫 `SwitchOut` 會失敗，且 HRESULT 值為 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="d3796-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3796-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="d3796-130">Requirements</span></span>  
 <span data-ttu-id="d3796-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3796-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3796-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d3796-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3796-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3796-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3796-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3796-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3796-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3796-135">See also</span></span>

- [<span data-ttu-id="d3796-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d3796-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d3796-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d3796-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d3796-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d3796-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d3796-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d3796-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
