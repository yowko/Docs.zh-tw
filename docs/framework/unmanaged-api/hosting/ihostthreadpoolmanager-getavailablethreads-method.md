---
title: IHostThreadPoolManager::GetAvailableThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a727a5287f6eaad600fc37befc32790fc4cf26
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749307"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="9dc9f-102">IHostThreadPoolManager::GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9dc9f-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="9dc9f-103">取得目前未處理的工作項目之執行緒集區中的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc9f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9dc9f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dc9f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9dc9f-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="9dc9f-106">[out]執行緒集區中目前未處理的工作項目的執行緒數目的指標。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dc9f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9dc9f-107">Return Value</span></span>  
  
|<span data-ttu-id="9dc9f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9dc9f-108">HRESULT</span></span>|<span data-ttu-id="9dc9f-109">描述</span><span class="sxs-lookup"><span data-stu-id="9dc9f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9dc9f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9dc9f-110">S_OK</span></span>|<span data-ttu-id="9dc9f-111">`GetAvailableThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9dc9f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9dc9f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9dc9f-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9dc9f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9dc9f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9dc9f-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-115">The call timed out.</span></span>|  
|<span data-ttu-id="9dc9f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dc9f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9dc9f-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9dc9f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9dc9f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9dc9f-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9dc9f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9dc9f-120">E_FAIL</span></span>|<span data-ttu-id="9dc9f-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9dc9f-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9dc9f-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9dc9f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9dc9f-124">E_NOTIMPL</span></span>|<span data-ttu-id="9dc9f-125">主機並未提供的實作`GetAvailableThreads`。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dc9f-126">備註</span><span class="sxs-lookup"><span data-stu-id="9dc9f-126">Remarks</span></span>  
 <span data-ttu-id="9dc9f-127">如果主機並未提供的實作`GetAvailableThreads`，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc9f-128">需求</span><span class="sxs-lookup"><span data-stu-id="9dc9f-128">Requirements</span></span>  
 <span data-ttu-id="9dc9f-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc9f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc9f-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9dc9f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9dc9f-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9dc9f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dc9f-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc9f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc9f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dc9f-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="9dc9f-134">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="9dc9f-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
