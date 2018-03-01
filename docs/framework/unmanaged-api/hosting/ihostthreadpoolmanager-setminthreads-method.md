---
title: "IHostThreadPoolManager::SetMinThreads 方法"
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
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fccfeb616b7a1c6d797ad9d91f47e696c4f3599
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="a59a1-102">IHostThreadPoolManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a59a1-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="a59a1-103">預期的要求中設定主應用程式必須維護的閒置執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="a59a1-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="a59a1-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a59a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="a59a1-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="a59a1-106">[in]新的主應用程式必須維護執行緒的下限。</span><span class="sxs-lookup"><span data-stu-id="a59a1-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a59a1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a59a1-107">Return Value</span></span>  
  
|<span data-ttu-id="a59a1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a59a1-108">HRESULT</span></span>|<span data-ttu-id="a59a1-109">描述</span><span class="sxs-lookup"><span data-stu-id="a59a1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a59a1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a59a1-110">S_OK</span></span>|<span data-ttu-id="a59a1-111">`SetMinThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a59a1-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="a59a1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a59a1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a59a1-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a59a1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a59a1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a59a1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a59a1-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a59a1-115">The call timed out.</span></span>|  
|<span data-ttu-id="a59a1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a59a1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a59a1-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a59a1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a59a1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a59a1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a59a1-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a59a1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a59a1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a59a1-120">E_FAIL</span></span>|<span data-ttu-id="a59a1-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a59a1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a59a1-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a59a1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a59a1-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a59a1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a59a1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a59a1-124">E_NOTIMPL</span></span>|<span data-ttu-id="a59a1-125">主機並未提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="a59a1-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a59a1-126">備註</span><span class="sxs-lookup"><span data-stu-id="a59a1-126">Remarks</span></span>  
 <span data-ttu-id="a59a1-127">主機不需要提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="a59a1-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="a59a1-128">在此情況下，則會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="a59a1-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59a1-129">需求</span><span class="sxs-lookup"><span data-stu-id="a59a1-129">Requirements</span></span>  
 <span data-ttu-id="a59a1-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a59a1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59a1-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a59a1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a59a1-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a59a1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a59a1-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59a1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59a1-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="a59a1-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="a59a1-135">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a59a1-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="a59a1-136">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a59a1-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="a59a1-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="a59a1-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
