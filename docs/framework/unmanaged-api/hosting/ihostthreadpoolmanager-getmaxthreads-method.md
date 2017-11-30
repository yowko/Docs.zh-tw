---
title: "IHostThreadPoolManager::GetMaxThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd15b1448c23785437b3dc62562b5d96abb3601c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="dab73-102">IHostThreadPoolManager::GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="dab73-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="dab73-103">執行緒集區中，同時取得主機維護執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="dab73-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab73-104">語法</span><span class="sxs-lookup"><span data-stu-id="dab73-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dab73-105">參數</span><span class="sxs-lookup"><span data-stu-id="dab73-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="dab73-106">[out]指向主機維護執行緒集區中的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="dab73-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dab73-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="dab73-107">Return Value</span></span>  
  
|<span data-ttu-id="dab73-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dab73-108">HRESULT</span></span>|<span data-ttu-id="dab73-109">描述</span><span class="sxs-lookup"><span data-stu-id="dab73-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dab73-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dab73-110">S_OK</span></span>|<span data-ttu-id="dab73-111">`GetMaxThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dab73-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="dab73-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dab73-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dab73-113">Common language runtime (CLR (尚未載入處理序，或 CLR 處於狀態中能執行以 managed 程式碼或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="dab73-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dab73-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dab73-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dab73-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dab73-115">The call timed out.</span></span>|  
|<span data-ttu-id="dab73-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dab73-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dab73-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dab73-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dab73-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dab73-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dab73-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dab73-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dab73-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dab73-120">E_FAIL</span></span>|<span data-ttu-id="dab73-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="dab73-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dab73-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="dab73-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dab73-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dab73-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dab73-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="dab73-124">E_NOTIMPL</span></span>|<span data-ttu-id="dab73-125">主機並未提供的實作`GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="dab73-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dab73-126">備註</span><span class="sxs-lookup"><span data-stu-id="dab73-126">Remarks</span></span>  
 <span data-ttu-id="dab73-127">CLR 會呼叫`GetMaxThreads`判斷執行緒集區中的執行緒總數。</span><span class="sxs-lookup"><span data-stu-id="dab73-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="dab73-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)方法會取得目前未處理的工作項目中的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="dab73-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="dab73-129">傳回值的所有要求`pdwMaxWorkerThreads`參數繼續佇列，直到執行緒變成可用。</span><span class="sxs-lookup"><span data-stu-id="dab73-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="dab73-130">如果主機並未提供的實作`GetMaxThreads`，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="dab73-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab73-131">需求</span><span class="sxs-lookup"><span data-stu-id="dab73-131">Requirements</span></span>  
 <span data-ttu-id="dab73-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dab73-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab73-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dab73-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dab73-134">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dab73-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dab73-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab73-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab73-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dab73-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="dab73-137">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="dab73-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="dab73-138">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="dab73-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="dab73-139">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="dab73-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
