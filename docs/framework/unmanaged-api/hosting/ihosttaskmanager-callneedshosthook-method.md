---
title: IHostTaskManager::CallNeedsHostHook 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176288"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="68572-102">IHostTaskManager::CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="68572-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="68572-103">使主機能夠指定通用語言運行時 （CLR） 是否可以將指定的調用內聯到非託管函數。</span><span class="sxs-lookup"><span data-stu-id="68572-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68572-104">語法</span><span class="sxs-lookup"><span data-stu-id="68572-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68572-105">參數</span><span class="sxs-lookup"><span data-stu-id="68572-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="68572-106">[在]要調用的非託管函數的映射的可移植可執行 （PE） 檔中的位址。</span><span class="sxs-lookup"><span data-stu-id="68572-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="68572-107">[出]指向布林值的指標，指示主機是否需要掛接調用。</span><span class="sxs-lookup"><span data-stu-id="68572-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68572-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="68572-108">Return Value</span></span>  
  
|<span data-ttu-id="68572-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68572-109">HRESULT</span></span>|<span data-ttu-id="68572-110">描述</span><span class="sxs-lookup"><span data-stu-id="68572-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68572-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="68572-111">S_OK</span></span>|<span data-ttu-id="68572-112">`CallNeedsHostHook`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="68572-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="68572-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68572-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68572-114">CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="68572-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="68572-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="68572-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="68572-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="68572-116">The call timed out.</span></span>|  
|<span data-ttu-id="68572-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="68572-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="68572-118">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="68572-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="68572-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="68572-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="68572-120">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="68572-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="68572-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68572-121">E_FAIL</span></span>|<span data-ttu-id="68572-122">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="68572-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="68572-123">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="68572-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="68572-124">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="68572-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68572-125">備註</span><span class="sxs-lookup"><span data-stu-id="68572-125">Remarks</span></span>  
 <span data-ttu-id="68572-126">為了説明優化代碼執行，CLR 在編譯期間對每個平台叫用調用執行分析，以確定調用是否可以內聯。</span><span class="sxs-lookup"><span data-stu-id="68572-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="68572-127">`CallNeedsHostHook`使主機通過要求對非託管函數的調用進行掛接來覆蓋該決策。</span><span class="sxs-lookup"><span data-stu-id="68572-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="68572-128">如果主機需要掛鉤，則運行時不會內聯呼叫。</span><span class="sxs-lookup"><span data-stu-id="68572-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="68572-129">主機通常需要一個掛鉤，它必須調整浮點狀態，或在收到通知時，呼叫正在進入一個狀態，其中主機無法跟蹤運行時的記憶體請求或獲取的任何鎖。</span><span class="sxs-lookup"><span data-stu-id="68572-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="68572-130">當主機要求掛接調用時，運行時通過使用對[EnterRuntime、](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)[離開運行時](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)、[反向EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)和[反向LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)的調用來通知主機與託管代碼轉換。</span><span class="sxs-lookup"><span data-stu-id="68572-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68572-131">需求</span><span class="sxs-lookup"><span data-stu-id="68572-131">Requirements</span></span>  
 <span data-ttu-id="68572-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68572-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68572-133">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="68572-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68572-134">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="68572-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68572-135">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68572-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68572-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68572-136">See also</span></span>

- [<span data-ttu-id="68572-137">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="68572-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="68572-138">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="68572-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="68572-139">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="68572-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="68572-140">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="68572-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
