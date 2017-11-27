---
title: "IHostIoCompletionManager::SetMaxThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 084cbf5509583a45f09bcf903e833f4890c5651e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="f4e4c-102">IHostIoCompletionManager::SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="f4e4c-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="f4e4c-103">來服務 I/O 要求中設定主應用程式指派的執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4e4c-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4e4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4e4c-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="f4e4c-106">[in]I/O 要求配置給執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4e4c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4e4c-107">Return Value</span></span>  
  
|<span data-ttu-id="f4e4c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4e4c-108">HRESULT</span></span>|<span data-ttu-id="f4e4c-109">描述</span><span class="sxs-lookup"><span data-stu-id="f4e4c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4e4c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4e4c-110">S_OK</span></span>|<span data-ttu-id="f4e4c-111">`SetMaxThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f4e4c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4e4c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4e4c-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4e4c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4e4c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4e4c-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-115">The call timed out.</span></span>|  
|<span data-ttu-id="f4e4c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4e4c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4e4c-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4e4c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4e4c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4e4c-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4e4c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4e4c-120">E_FAIL</span></span>|<span data-ttu-id="f4e4c-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4e4c-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4e4c-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f4e4c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f4e4c-124">E_NOTIMPL</span></span>|<span data-ttu-id="f4e4c-125">主機並未提供的實作`SetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4e4c-126">備註</span><span class="sxs-lookup"><span data-stu-id="f4e4c-126">Remarks</span></span>  
 <span data-ttu-id="f4e4c-127">`SetMaxThreads`提供 CLR，可以設定的可用的 I/O 連接埠上的服務要求的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="f4e4c-128">原因例如實作、 效能或延展性，主機可能需要的執行緒集區大小的專有控制權。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="f4e4c-129">基於這個理由，主應用程式不需要實作`SetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="f4e4c-130">在此情況下，主應用程式應該從這個方法會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e4c-131">需求</span><span class="sxs-lookup"><span data-stu-id="f4e4c-131">Requirements</span></span>  
 <span data-ttu-id="f4e4c-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4e4c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4e4c-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4e4c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4e4c-134">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f4e4c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4e4c-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4e4c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e4c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4e4c-136">See Also</span></span>  
 [<span data-ttu-id="f4e4c-137">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="f4e4c-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="f4e4c-138">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="f4e4c-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
