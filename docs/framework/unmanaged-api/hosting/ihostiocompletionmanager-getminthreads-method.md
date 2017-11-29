---
title: "IHostIoCompletionManager::GetMinThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6fb9369b67cd79c6e83dc13e2a1090ae611a5e5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="0c8b6-102">IHostIoCompletionManager::GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="0c8b6-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="0c8b6-103">取得主應用程式提供處理 I/O 要求的執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c8b6-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c8b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c8b6-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="0c8b6-106">[out]主機會提供給程序 I/O 要求的執行緒的最小數目指標。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c8b6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0c8b6-107">Return Value</span></span>  
  
|<span data-ttu-id="0c8b6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c8b6-108">HRESULT</span></span>|<span data-ttu-id="0c8b6-109">描述</span><span class="sxs-lookup"><span data-stu-id="0c8b6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c8b6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c8b6-110">S_OK</span></span>|<span data-ttu-id="0c8b6-111">`GetMinThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0c8b6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c8b6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c8b6-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c8b6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c8b6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c8b6-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-115">The call timed out.</span></span>|  
|<span data-ttu-id="0c8b6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c8b6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c8b6-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c8b6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c8b6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c8b6-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c8b6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c8b6-120">E_FAIL</span></span>|<span data-ttu-id="0c8b6-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c8b6-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c8b6-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0c8b6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0c8b6-124">E_NOTIMPL</span></span>|<span data-ttu-id="0c8b6-125">主機並未提供的實作`GetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c8b6-126">備註</span><span class="sxs-lookup"><span data-stu-id="0c8b6-126">Remarks</span></span>  
 <span data-ttu-id="0c8b6-127">主機可以分配給服務 I/O 要求，例如實作、 效能或延展性原因的執行緒數目的專有控制權。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0c8b6-128">基於這個理由，主應用程式不需要實作`GetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="0c8b6-129">在此情況下，主應用程式應該從這個方法會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8b6-130">需求</span><span class="sxs-lookup"><span data-stu-id="0c8b6-130">Requirements</span></span>  
 <span data-ttu-id="0c8b6-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c8b6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8b6-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c8b6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c8b6-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0c8b6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c8b6-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8b6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8b6-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c8b6-135">See Also</span></span>  
 [<span data-ttu-id="0c8b6-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0c8b6-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="0c8b6-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0c8b6-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
