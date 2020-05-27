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
ms.openlocfilehash: 5bc5752d4d2b772b1d18f438c4daaa1b8938da9e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842344"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="307a7-102">IHostTaskManager::CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="307a7-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="307a7-103">可讓主機指定 common language runtime （CLR）是否可以將指定的呼叫內嵌至非受控函式。</span><span class="sxs-lookup"><span data-stu-id="307a7-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="307a7-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="307a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="307a7-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="307a7-106">在要呼叫之非受控函式的對應可移植執行檔（PE）中的位址。</span><span class="sxs-lookup"><span data-stu-id="307a7-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="307a7-107">脫銷布林值的指標，指出主機是否需要連接呼叫。</span><span class="sxs-lookup"><span data-stu-id="307a7-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="307a7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="307a7-108">Return Value</span></span>  
  
|<span data-ttu-id="307a7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="307a7-109">HRESULT</span></span>|<span data-ttu-id="307a7-110">描述</span><span class="sxs-lookup"><span data-stu-id="307a7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="307a7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="307a7-111">S_OK</span></span>|<span data-ttu-id="307a7-112">`CallNeedsHostHook`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="307a7-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="307a7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="307a7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="307a7-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="307a7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="307a7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="307a7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="307a7-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="307a7-116">The call timed out.</span></span>|  
|<span data-ttu-id="307a7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="307a7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="307a7-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="307a7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="307a7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="307a7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="307a7-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="307a7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="307a7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="307a7-121">E_FAIL</span></span>|<span data-ttu-id="307a7-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="307a7-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="307a7-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="307a7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="307a7-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="307a7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="307a7-125">備註</span><span class="sxs-lookup"><span data-stu-id="307a7-125">Remarks</span></span>  
 <span data-ttu-id="307a7-126">為了協助優化程式碼執行，CLR 會在編譯期間執行每個平台叫用呼叫的分析，以判斷呼叫是否可以內嵌。</span><span class="sxs-lookup"><span data-stu-id="307a7-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="307a7-127">`CallNeedsHostHook`藉由要求對非受控函式的呼叫進行連結，讓主機覆寫該決策。</span><span class="sxs-lookup"><span data-stu-id="307a7-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="307a7-128">如果主機需要勾點，執行時間就不會內嵌呼叫。</span><span class="sxs-lookup"><span data-stu-id="307a7-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="307a7-129">主機通常需要進行攔截，其中必須調整浮點狀態，或收到通知，指出呼叫正在進入狀態，其中主機無法追蹤執行時間的記憶體要求或所採取的任何鎖定。</span><span class="sxs-lookup"><span data-stu-id="307a7-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="307a7-130">當主機要求呼叫必須進行連結時，執行時間會使用[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)、 [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)、 [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)和[ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)的呼叫，來通知主機與 managed 程式碼之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="307a7-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="307a7-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="307a7-131">Requirements</span></span>  
 <span data-ttu-id="307a7-132">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="307a7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="307a7-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="307a7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="307a7-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="307a7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="307a7-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="307a7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307a7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="307a7-136">See also</span></span>

- [<span data-ttu-id="307a7-137">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="307a7-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="307a7-138">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="307a7-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="307a7-139">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="307a7-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="307a7-140">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="307a7-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
