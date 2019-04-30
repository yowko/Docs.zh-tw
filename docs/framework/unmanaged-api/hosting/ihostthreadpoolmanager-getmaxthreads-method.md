---
title: IHostThreadPoolManager::GetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4dce4efeb82f44e2c0d19e95551696b16e9f07ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961191"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="9af76-102">IHostThreadPoolManager::GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9af76-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="9af76-103">執行緒集區中，同時取得主機維護執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="9af76-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af76-104">語法</span><span class="sxs-lookup"><span data-stu-id="9af76-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9af76-105">參數</span><span class="sxs-lookup"><span data-stu-id="9af76-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="9af76-106">[out]指標的主控件保留在執行緒集區中的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="9af76-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9af76-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9af76-107">Return Value</span></span>  
  
|<span data-ttu-id="9af76-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9af76-108">HRESULT</span></span>|<span data-ttu-id="9af76-109">描述</span><span class="sxs-lookup"><span data-stu-id="9af76-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9af76-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9af76-110">S_OK</span></span>|<span data-ttu-id="9af76-111">`GetMaxThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9af76-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9af76-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9af76-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9af76-113">Common language runtime (CLR (尚未載入處理序，或 CLR 處於狀態在它無法執行 managed 程式碼或處理程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="9af76-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9af76-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9af76-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9af76-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="9af76-115">The call timed out.</span></span>|  
|<span data-ttu-id="9af76-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9af76-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9af76-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9af76-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9af76-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9af76-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9af76-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="9af76-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9af76-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9af76-120">E_FAIL</span></span>|<span data-ttu-id="9af76-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="9af76-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9af76-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="9af76-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9af76-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9af76-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9af76-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9af76-124">E_NOTIMPL</span></span>|<span data-ttu-id="9af76-125">主機並未提供的實作`GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="9af76-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9af76-126">備註</span><span class="sxs-lookup"><span data-stu-id="9af76-126">Remarks</span></span>  
 <span data-ttu-id="9af76-127">CLR 會呼叫`GetMaxThreads`來判斷執行緒集區中的執行緒總數。</span><span class="sxs-lookup"><span data-stu-id="9af76-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="9af76-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)方法會取得目前未處理的工作項目中的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="9af76-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="9af76-129">傳回值的所有要求`pdwMaxWorkerThreads`參數保留已排入佇列，直到執行緒變成可用。</span><span class="sxs-lookup"><span data-stu-id="9af76-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="9af76-130">如果主機並未提供的實作`GetMaxThreads`，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="9af76-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af76-131">需求</span><span class="sxs-lookup"><span data-stu-id="9af76-131">Requirements</span></span>  
 <span data-ttu-id="9af76-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9af76-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af76-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9af76-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9af76-134">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9af76-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9af76-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9af76-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af76-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9af76-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="9af76-137">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9af76-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="9af76-138">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9af76-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="9af76-139">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="9af76-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
