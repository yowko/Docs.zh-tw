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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d31aa0dfad70bed31bd72be5029c7bdff0925ba2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088546"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="429c9-102">IHostSecurityManager::SetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="429c9-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="429c9-103">設定目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="429c9-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="429c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="429c9-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="429c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="429c9-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="429c9-106">[in]其中一個[EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值，指出哪種類型的內容 common language runtime (CLR) 會放置在主機上。</span><span class="sxs-lookup"><span data-stu-id="429c9-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="429c9-107">[out]新的位址指標[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="429c9-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="429c9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="429c9-108">Return Value</span></span>  
  
|<span data-ttu-id="429c9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="429c9-109">HRESULT</span></span>|<span data-ttu-id="429c9-110">描述</span><span class="sxs-lookup"><span data-stu-id="429c9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="429c9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="429c9-111">S_OK</span></span>|`SetSecurityContext` <span data-ttu-id="429c9-112">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="429c9-112">returned successfully.</span></span>|  
|<span data-ttu-id="429c9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="429c9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="429c9-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="429c9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="429c9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="429c9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="429c9-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="429c9-116">The call timed out.</span></span>|  
|<span data-ttu-id="429c9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="429c9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="429c9-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="429c9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="429c9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="429c9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="429c9-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="429c9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="429c9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="429c9-121">E_FAIL</span></span>|<span data-ttu-id="429c9-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="429c9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="429c9-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="429c9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="429c9-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="429c9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="429c9-125">備註</span><span class="sxs-lookup"><span data-stu-id="429c9-125">Remarks</span></span>  
 <span data-ttu-id="429c9-126">CLR 會呼叫`SetSecurityContext`數種案例中。</span><span class="sxs-lookup"><span data-stu-id="429c9-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="429c9-127">類別和模組建構函式和完成項，它會執行之前，CLR 會呼叫`SetSecurityContext`來防禦執行失敗的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="429c9-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="429c9-128">它然後重設的安全性內容為其原始狀態後執行建構函式或完成項，使用另一個呼叫`SetSecurityContext`。</span><span class="sxs-lookup"><span data-stu-id="429c9-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="429c9-129">與 I/O 完成，就會發生類似的模式。</span><span class="sxs-lookup"><span data-stu-id="429c9-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="429c9-130">如果主應用程式實作[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)，CLR 會呼叫`SetSecurityContext`主機呼叫之後[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)。</span><span class="sxs-lookup"><span data-stu-id="429c9-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="429c9-131">在背景工作執行緒中的非同步點，CLR 會呼叫`SetSecurityContext`內<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>或是在[ihostthreadpoolmanager:: Queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)，取決於是否在主機或 CLR 正在實作執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="429c9-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="429c9-132">需求</span><span class="sxs-lookup"><span data-stu-id="429c9-132">Requirements</span></span>  
 <span data-ttu-id="429c9-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="429c9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="429c9-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="429c9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="429c9-135">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="429c9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="429c9-136">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="429c9-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="429c9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="429c9-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="429c9-138">EContextType 列舉</span><span class="sxs-lookup"><span data-stu-id="429c9-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="429c9-139">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="429c9-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="429c9-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="429c9-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="429c9-141">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="429c9-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="429c9-142">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="429c9-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="429c9-143">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="429c9-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
