---
title: IHostThreadPoolManager::SetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 442e4566749aade5a7f8164fcc43baad902928c0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749124"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="b4942-102">IHostThreadPoolManager::SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b4942-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="b4942-103">設定主應用程式可以維護執行緒集區中的執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="b4942-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4942-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4942-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4942-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4942-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="b4942-106">執行緒集區中的背景工作執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="b4942-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4942-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b4942-107">Return Value</span></span>  
  
|<span data-ttu-id="b4942-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4942-108">HRESULT</span></span>|<span data-ttu-id="b4942-109">描述</span><span class="sxs-lookup"><span data-stu-id="b4942-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4942-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4942-110">S_OK</span></span>|<span data-ttu-id="b4942-111">`SetMaxThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b4942-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b4942-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4942-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4942-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b4942-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b4942-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4942-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b4942-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b4942-115">The call timed out.</span></span>|  
|<span data-ttu-id="b4942-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4942-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b4942-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b4942-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b4942-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b4942-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b4942-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b4942-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b4942-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4942-120">E_FAIL</span></span>|<span data-ttu-id="b4942-121">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="b4942-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b4942-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b4942-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b4942-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b4942-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b4942-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b4942-124">E_NOTIMPL</span></span>|<span data-ttu-id="b4942-125">主機並未提供的實作`SetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="b4942-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4942-126">備註</span><span class="sxs-lookup"><span data-stu-id="b4942-126">Remarks</span></span>  
 <span data-ttu-id="b4942-127">主機不需要讓 CLR 設定執行緒集區的大小。</span><span class="sxs-lookup"><span data-stu-id="b4942-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="b4942-128">某些主機可能會想專有控制權的執行緒集區中，例如實作、 效能或延展性的原因。</span><span class="sxs-lookup"><span data-stu-id="b4942-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="b4942-129">在此情況下，主應用程式應該傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="b4942-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4942-130">需求</span><span class="sxs-lookup"><span data-stu-id="b4942-130">Requirements</span></span>  
 <span data-ttu-id="b4942-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4942-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4942-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4942-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4942-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b4942-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4942-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4942-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4942-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4942-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="b4942-136">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b4942-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="b4942-137">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b4942-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="b4942-138">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="b4942-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
