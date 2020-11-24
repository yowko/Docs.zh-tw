---
title: IHostSecurityManager::SetSecurityContext 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: dadacaea2b8741afc7b8c51404e2604dc759a629
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680374"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="e2b22-102">IHostSecurityManager::SetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="e2b22-102">IHostSecurityManager::SetSecurityContext Method</span></span>

<span data-ttu-id="e2b22-103">設定目前執行中線程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="e2b22-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b22-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2b22-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2b22-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2b22-105">Parameters</span></span>  

 `eContextType`  
 <span data-ttu-id="e2b22-106">在其中一個 [ECoNtextType](econtexttype-enumeration.md) 值，指出 common language RUNTIME (CLR) 放置在主機上的內容類型。</span><span class="sxs-lookup"><span data-stu-id="e2b22-106">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="e2b22-107">擴展新 [IHostSecurityCoNtext](ihostsecuritycontext-interface.md) 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e2b22-107">[out] A pointer to the address of a new [IHostSecurityContext](ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2b22-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e2b22-108">Return Value</span></span>  
  
|<span data-ttu-id="e2b22-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2b22-109">HRESULT</span></span>|<span data-ttu-id="e2b22-110">描述</span><span class="sxs-lookup"><span data-stu-id="e2b22-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2b22-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2b22-111">S_OK</span></span>|<span data-ttu-id="e2b22-112">`SetSecurityContext` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="e2b22-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="e2b22-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e2b22-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e2b22-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e2b22-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e2b22-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e2b22-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e2b22-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="e2b22-116">The call timed out.</span></span>|  
|<span data-ttu-id="e2b22-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e2b22-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e2b22-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e2b22-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e2b22-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e2b22-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e2b22-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="e2b22-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e2b22-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2b22-121">E_FAIL</span></span>|<span data-ttu-id="e2b22-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e2b22-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e2b22-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="e2b22-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e2b22-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e2b22-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2b22-125">備註</span><span class="sxs-lookup"><span data-stu-id="e2b22-125">Remarks</span></span>  

 <span data-ttu-id="e2b22-126">CLR 會 `SetSecurityContext` 在數個案例中呼叫。</span><span class="sxs-lookup"><span data-stu-id="e2b22-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="e2b22-127">在執行類別和模組的函式和完成項之前，CLR 會呼叫 `SetSecurityContext` 以防止主機執行失敗。</span><span class="sxs-lookup"><span data-stu-id="e2b22-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="e2b22-128">然後，它會在執行函式或完成項之後，使用的另一個呼叫，將安全性內容重設為其原始狀態 `SetSecurityContext` 。</span><span class="sxs-lookup"><span data-stu-id="e2b22-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="e2b22-129">I/o 完成時，會發生類似的模式。</span><span class="sxs-lookup"><span data-stu-id="e2b22-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="e2b22-130">如果主機執行 [IHostIoCompletionManager](ihostiocompletionmanager-interface.md)，則 CLR 會在 `SetSecurityContext` 主機呼叫 [ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md)之後呼叫。</span><span class="sxs-lookup"><span data-stu-id="e2b22-130">If the host implements [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="e2b22-131">在背景工作執行緒的非同步點上，CLR `SetSecurityContext` <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> 會在 [IHostThreadPoolManager：： QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)內或內部呼叫，視主機或 CLR 是否正在執行執行緒集區而定。</span><span class="sxs-lookup"><span data-stu-id="e2b22-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2b22-132">需求</span><span class="sxs-lookup"><span data-stu-id="e2b22-132">Requirements</span></span>  

 <span data-ttu-id="e2b22-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b22-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2b22-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e2b22-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2b22-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e2b22-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2b22-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2b22-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b22-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2b22-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="e2b22-138">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="e2b22-138">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="e2b22-139">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="e2b22-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e2b22-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="e2b22-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="e2b22-141">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="e2b22-141">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="e2b22-142">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="e2b22-142">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="e2b22-143">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="e2b22-143">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
