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
ms.openlocfilehash: 7c7af1bbf3d13c3f66d525dfce69d8b49fbe045c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675135"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="e23a7-102">IHostTaskManager::CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="e23a7-102">IHostTaskManager::CallNeedsHostHook Method</span></span>

<span data-ttu-id="e23a7-103">可讓主機指定 common language runtime (CLR) 是否可以將指定的呼叫內嵌至非受控函式。</span><span class="sxs-lookup"><span data-stu-id="e23a7-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e23a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e23a7-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e23a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e23a7-105">Parameters</span></span>  

 `target`  
 <span data-ttu-id="e23a7-106">在在對應的可執行檔中， (PE) 要呼叫之非受控函式的檔案內的位址。</span><span class="sxs-lookup"><span data-stu-id="e23a7-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="e23a7-107">擴展布林值的指標，指出主機是否需要連結呼叫。</span><span class="sxs-lookup"><span data-stu-id="e23a7-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e23a7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e23a7-108">Return Value</span></span>  
  
|<span data-ttu-id="e23a7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e23a7-109">HRESULT</span></span>|<span data-ttu-id="e23a7-110">描述</span><span class="sxs-lookup"><span data-stu-id="e23a7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e23a7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e23a7-111">S_OK</span></span>|<span data-ttu-id="e23a7-112">`CallNeedsHostHook` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="e23a7-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="e23a7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e23a7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e23a7-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e23a7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e23a7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e23a7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e23a7-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="e23a7-116">The call timed out.</span></span>|  
|<span data-ttu-id="e23a7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e23a7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e23a7-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e23a7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e23a7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e23a7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e23a7-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="e23a7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e23a7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e23a7-121">E_FAIL</span></span>|<span data-ttu-id="e23a7-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e23a7-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="e23a7-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="e23a7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e23a7-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e23a7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e23a7-125">備註</span><span class="sxs-lookup"><span data-stu-id="e23a7-125">Remarks</span></span>  

 <span data-ttu-id="e23a7-126">為了協助優化程式碼執行，CLR 會在編譯期間執行每個平台叫用呼叫的分析，以判斷呼叫是否可以內嵌。</span><span class="sxs-lookup"><span data-stu-id="e23a7-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="e23a7-127">`CallNeedsHostHook` 藉由要求呼叫非受控函式，讓主機覆寫該決策。</span><span class="sxs-lookup"><span data-stu-id="e23a7-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="e23a7-128">如果主機需要勾點，則執行時間不會內嵌呼叫。</span><span class="sxs-lookup"><span data-stu-id="e23a7-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="e23a7-129">主機通常需要有必須調整浮點數狀態的勾點，或是收到呼叫進入的通知，指出主機無法追蹤執行時間的記憶體要求或任何所採取的鎖定。</span><span class="sxs-lookup"><span data-stu-id="e23a7-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="e23a7-130">當主機需要呼叫的呼叫時，執行時間會使用 [EnterRuntime](ihosttaskmanager-enterruntime-method.md)、 [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)、 [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)和 [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)的呼叫，通知主機 managed 程式碼的轉換。</span><span class="sxs-lookup"><span data-stu-id="e23a7-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e23a7-131">需求</span><span class="sxs-lookup"><span data-stu-id="e23a7-131">Requirements</span></span>  

 <span data-ttu-id="e23a7-132">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e23a7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e23a7-133">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e23a7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e23a7-134">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e23a7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e23a7-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e23a7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23a7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e23a7-136">See also</span></span>

- [<span data-ttu-id="e23a7-137">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="e23a7-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e23a7-138">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e23a7-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e23a7-139">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="e23a7-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e23a7-140">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e23a7-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
