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
ms.openlocfilehash: e53265556de026e84af7ca345a5f82be3c5ff812
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122049"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="eead7-102">IHostThreadPoolManager::GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="eead7-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="eead7-103">取得主機線上程集區中同時維護的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="eead7-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eead7-104">語法</span><span class="sxs-lookup"><span data-stu-id="eead7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eead7-105">參數</span><span class="sxs-lookup"><span data-stu-id="eead7-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="eead7-106">脫銷主機線上程集區中維護的最大執行緒數目的指標。</span><span class="sxs-lookup"><span data-stu-id="eead7-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eead7-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="eead7-107">Return Value</span></span>  
  
|<span data-ttu-id="eead7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eead7-108">HRESULT</span></span>|<span data-ttu-id="eead7-109">描述</span><span class="sxs-lookup"><span data-stu-id="eead7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eead7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eead7-110">S_OK</span></span>|<span data-ttu-id="eead7-111">已成功傳回 `GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="eead7-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="eead7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eead7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eead7-113">通用語言執行平臺（CLR （尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eead7-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eead7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eead7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eead7-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="eead7-115">The call timed out.</span></span>|  
|<span data-ttu-id="eead7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eead7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eead7-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eead7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eead7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eead7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eead7-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="eead7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eead7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eead7-120">E_FAIL</span></span>|<span data-ttu-id="eead7-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eead7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eead7-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="eead7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eead7-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eead7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eead7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="eead7-124">E_NOTIMPL</span></span>|<span data-ttu-id="eead7-125">主機未提供 `GetMaxThreads`的執行。</span><span class="sxs-lookup"><span data-stu-id="eead7-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eead7-126">備註</span><span class="sxs-lookup"><span data-stu-id="eead7-126">Remarks</span></span>  
 <span data-ttu-id="eead7-127">CLR 會呼叫 `GetMaxThreads` 來判斷線程集區中的執行緒總數。</span><span class="sxs-lookup"><span data-stu-id="eead7-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="eead7-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)方法會取得目前未處理工作專案的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="eead7-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="eead7-129">超過 `pdwMaxWorkerThreads` 參數傳回值的所有要求都會繼續排入佇列，直到執行緒變成可用為止。</span><span class="sxs-lookup"><span data-stu-id="eead7-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="eead7-130">如果主機未提供 `GetMaxThreads`的執行，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="eead7-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eead7-131">需求</span><span class="sxs-lookup"><span data-stu-id="eead7-131">Requirements</span></span>  
 <span data-ttu-id="eead7-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eead7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eead7-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="eead7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eead7-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eead7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eead7-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eead7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eead7-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="eead7-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="eead7-137">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="eead7-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="eead7-138">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="eead7-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="eead7-139">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="eead7-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
