---
title: "IHostThreadPoolManager::SetMinThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab0b107c050b1c4b686f761ede75ea2349825270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="20d66-102">IHostThreadPoolManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="20d66-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="20d66-103">預期的要求中設定主應用程式必須維護的閒置執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="20d66-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d66-104">語法</span><span class="sxs-lookup"><span data-stu-id="20d66-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20d66-105">參數</span><span class="sxs-lookup"><span data-stu-id="20d66-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="20d66-106">[in]新的主應用程式必須維護執行緒的下限。</span><span class="sxs-lookup"><span data-stu-id="20d66-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20d66-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="20d66-107">Return Value</span></span>  
  
|<span data-ttu-id="20d66-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20d66-108">HRESULT</span></span>|<span data-ttu-id="20d66-109">描述</span><span class="sxs-lookup"><span data-stu-id="20d66-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20d66-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="20d66-110">S_OK</span></span>|<span data-ttu-id="20d66-111">`SetMinThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="20d66-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="20d66-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20d66-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20d66-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="20d66-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20d66-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20d66-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20d66-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="20d66-115">The call timed out.</span></span>|  
|<span data-ttu-id="20d66-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20d66-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20d66-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="20d66-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20d66-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20d66-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20d66-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="20d66-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20d66-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20d66-120">E_FAIL</span></span>|<span data-ttu-id="20d66-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="20d66-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20d66-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="20d66-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20d66-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="20d66-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="20d66-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="20d66-124">E_NOTIMPL</span></span>|<span data-ttu-id="20d66-125">主機並未提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="20d66-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20d66-126">備註</span><span class="sxs-lookup"><span data-stu-id="20d66-126">Remarks</span></span>  
 <span data-ttu-id="20d66-127">主機不需要提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="20d66-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="20d66-128">在此情況下，則會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="20d66-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20d66-129">需求</span><span class="sxs-lookup"><span data-stu-id="20d66-129">Requirements</span></span>  
 <span data-ttu-id="20d66-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20d66-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20d66-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20d66-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20d66-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="20d66-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20d66-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20d66-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d66-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20d66-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="20d66-135">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="20d66-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="20d66-136">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="20d66-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="20d66-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="20d66-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
