---
title: "IHostThreadPoolManager::GetMinThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 393400c7a5d9d4d99431cbea4a3c3c82064218f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="42016-102">IHostThreadPoolManager::GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="42016-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="42016-103">取得主機維護的閒置執行緒數目最小執行緒集區要求的頁數。</span><span class="sxs-lookup"><span data-stu-id="42016-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42016-104">語法</span><span class="sxs-lookup"><span data-stu-id="42016-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42016-105">參數</span><span class="sxs-lookup"><span data-stu-id="42016-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="42016-106">[out]主機目前維護閒置工作者執行緒最小數目指標。</span><span class="sxs-lookup"><span data-stu-id="42016-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42016-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="42016-107">Return Value</span></span>  
  
|<span data-ttu-id="42016-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42016-108">HRESULT</span></span>|<span data-ttu-id="42016-109">描述</span><span class="sxs-lookup"><span data-stu-id="42016-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42016-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="42016-110">S_OK</span></span>|<span data-ttu-id="42016-111">`GetMinThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="42016-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="42016-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42016-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42016-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="42016-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42016-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42016-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42016-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="42016-115">The call timed out.</span></span>|  
|<span data-ttu-id="42016-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42016-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42016-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="42016-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42016-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42016-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42016-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="42016-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42016-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42016-120">E_FAIL</span></span>|<span data-ttu-id="42016-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="42016-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42016-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="42016-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42016-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="42016-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="42016-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="42016-124">E_NOTIMPL</span></span>|<span data-ttu-id="42016-125">主機並未提供的實作`GetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="42016-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42016-126">備註</span><span class="sxs-lookup"><span data-stu-id="42016-126">Remarks</span></span>  
 <span data-ttu-id="42016-127">主機不需要提供的實作`GetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="42016-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="42016-128">在此情況下，則會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="42016-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42016-129">需求</span><span class="sxs-lookup"><span data-stu-id="42016-129">Requirements</span></span>  
 <span data-ttu-id="42016-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42016-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42016-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42016-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42016-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="42016-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42016-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42016-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42016-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="42016-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="42016-135">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="42016-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="42016-136">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="42016-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="42016-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="42016-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
