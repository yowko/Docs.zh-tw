---
title: IHostIoCompletionManager::SetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 345c7b88b6967773a185538943591383a686748c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224059"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="4815d-102">IHostIoCompletionManager::SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="4815d-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="4815d-103">I/O 要求提供服務設定主應用程式指派的執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="4815d-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4815d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4815d-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4815d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4815d-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="4815d-106">[in]I/O 要求配置給執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="4815d-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4815d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4815d-107">Return Value</span></span>  
  
|<span data-ttu-id="4815d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4815d-108">HRESULT</span></span>|<span data-ttu-id="4815d-109">描述</span><span class="sxs-lookup"><span data-stu-id="4815d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4815d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4815d-110">S_OK</span></span>|<span data-ttu-id="4815d-111">`SetMaxThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4815d-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4815d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4815d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4815d-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4815d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4815d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4815d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4815d-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="4815d-115">The call timed out.</span></span>|  
|<span data-ttu-id="4815d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4815d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4815d-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4815d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4815d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4815d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4815d-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="4815d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4815d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4815d-120">E_FAIL</span></span>|<span data-ttu-id="4815d-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="4815d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4815d-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="4815d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4815d-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4815d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4815d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4815d-124">E_NOTIMPL</span></span>|<span data-ttu-id="4815d-125">主機並未提供的實作`SetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="4815d-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4815d-126">備註</span><span class="sxs-lookup"><span data-stu-id="4815d-126">Remarks</span></span>  
 <span data-ttu-id="4815d-127">`SetMaxThreads` CLR 提供的機會，可以設定最大的 I/O 連接埠上的服務要求可用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="4815d-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="4815d-128">主機可能需要的執行緒集區大小的專有控制權的原因，例如實作、 效能或延展性。</span><span class="sxs-lookup"><span data-stu-id="4815d-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="4815d-129">基於這個理由，主應用程式不需要實作`SetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="4815d-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="4815d-130">在此情況下，主應用程式應該從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="4815d-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4815d-131">需求</span><span class="sxs-lookup"><span data-stu-id="4815d-131">Requirements</span></span>  
 <span data-ttu-id="4815d-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4815d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4815d-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4815d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4815d-134">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4815d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4815d-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4815d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4815d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4815d-136">See also</span></span>

- [<span data-ttu-id="4815d-137">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="4815d-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4815d-138">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="4815d-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
