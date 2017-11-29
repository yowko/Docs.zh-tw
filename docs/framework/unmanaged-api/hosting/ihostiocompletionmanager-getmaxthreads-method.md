---
title: "IHostIoCompletionManager::GetMaxThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e7df4acd435c767a1d0c3ae4484a236359cfb38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="3b94b-102">IHostIoCompletionManager::GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="3b94b-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="3b94b-103">取得服務 I/O 要求的主機可以配置的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="3b94b-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b94b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b94b-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b94b-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b94b-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="3b94b-106">[out]指向主機可以指派來服務 I/O 要求在執行緒集區中的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="3b94b-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b94b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3b94b-107">Return Value</span></span>  
  
|<span data-ttu-id="3b94b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b94b-108">HRESULT</span></span>|<span data-ttu-id="3b94b-109">描述</span><span class="sxs-lookup"><span data-stu-id="3b94b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b94b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b94b-110">S_OK</span></span>|<span data-ttu-id="3b94b-111">`GetMaxThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3b94b-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="3b94b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b94b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b94b-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3b94b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b94b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b94b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b94b-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3b94b-115">The call timed out.</span></span>|  
|<span data-ttu-id="3b94b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b94b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b94b-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3b94b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b94b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b94b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b94b-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3b94b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b94b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b94b-120">E_FAIL</span></span>|<span data-ttu-id="3b94b-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3b94b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3b94b-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="3b94b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b94b-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3b94b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3b94b-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3b94b-124">E_NOTIMPL</span></span>|<span data-ttu-id="3b94b-125">主機並未提供的實作`GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="3b94b-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b94b-126">備註</span><span class="sxs-lookup"><span data-stu-id="3b94b-126">Remarks</span></span>  
 <span data-ttu-id="3b94b-127">主機可能會想以處理 I/O 要求，例如實作、 效能或延展性原因可以配置的執行緒數目的專有控制權。</span><span class="sxs-lookup"><span data-stu-id="3b94b-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="3b94b-128">基於這個理由，主應用程式不需要實作`GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="3b94b-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="3b94b-129">在此情況下，主應用程式應該從這個方法會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="3b94b-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b94b-130">需求</span><span class="sxs-lookup"><span data-stu-id="3b94b-130">Requirements</span></span>  
 <span data-ttu-id="3b94b-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b94b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b94b-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3b94b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b94b-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3b94b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b94b-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b94b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b94b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b94b-135">See Also</span></span>  
 [<span data-ttu-id="3b94b-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="3b94b-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="3b94b-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="3b94b-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
