---
title: "IHostSecurityManager::SetSecurityContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29a7652e20c08b9de584a9e11ac343ad92f40653
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="9dcd3-102">IHostSecurityManager::SetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="9dcd3-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="9dcd3-103">設定目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dcd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="9dcd3-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9dcd3-105">參數</span><span class="sxs-lookup"><span data-stu-id="9dcd3-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="9dcd3-106">[in]其中一個[EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值，指出哪種類型的內容 common language runtime (CLR) 會放置在主機上。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="9dcd3-107">[out]新的位址指標[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dcd3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9dcd3-108">Return Value</span></span>  
  
|<span data-ttu-id="9dcd3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9dcd3-109">HRESULT</span></span>|<span data-ttu-id="9dcd3-110">描述</span><span class="sxs-lookup"><span data-stu-id="9dcd3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9dcd3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9dcd3-111">S_OK</span></span>|<span data-ttu-id="9dcd3-112">`SetSecurityContext`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="9dcd3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9dcd3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9dcd3-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9dcd3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9dcd3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9dcd3-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-116">The call timed out.</span></span>|  
|<span data-ttu-id="9dcd3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dcd3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9dcd3-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9dcd3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9dcd3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9dcd3-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9dcd3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9dcd3-121">E_FAIL</span></span>|<span data-ttu-id="9dcd3-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9dcd3-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9dcd3-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dcd3-125">備註</span><span class="sxs-lookup"><span data-stu-id="9dcd3-125">Remarks</span></span>  
 <span data-ttu-id="9dcd3-126">CLR 會呼叫`SetSecurityContext`數種案例中。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="9dcd3-127">類別和模組建構函式與完成項，它會執行之前，CLR 會呼叫`SetSecurityContext`以避免執行失敗的主機。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="9dcd3-128">它然後重設的安全性內容為其原始狀態的建構函式或完成項，執行後使用另一個呼叫`SetSecurityContext`。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="9dcd3-129">與 I/O 完成，就會發生類似的模式。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="9dcd3-130">如果主機實作[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)，CLR 會呼叫`SetSecurityContext`主機呼叫之後[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="9dcd3-131">在非同步背景工作執行緒中的點，CLR 會呼叫`SetSecurityContext`內<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>或[ihostthreadpoolmanager:: Queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)，取決於是否在主機或 CLR 會實作在執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dcd3-132">需求</span><span class="sxs-lookup"><span data-stu-id="9dcd3-132">Requirements</span></span>  
 <span data-ttu-id="9dcd3-133">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9dcd3-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dcd3-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9dcd3-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9dcd3-135">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9dcd3-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dcd3-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dcd3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dcd3-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="9dcd3-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="9dcd3-138">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="9dcd3-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="9dcd3-139">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="9dcd3-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="9dcd3-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="9dcd3-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="9dcd3-141">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="9dcd3-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="9dcd3-142">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="9dcd3-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="9dcd3-143">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="9dcd3-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
