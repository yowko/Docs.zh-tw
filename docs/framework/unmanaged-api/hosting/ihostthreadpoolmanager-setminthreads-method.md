---
title: IHostThreadPoolManager::SetMinThreads 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c79f18c1deec4183a5a736c5acf88e9a1fd8021
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749088"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="1216e-102">IHostThreadPoolManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1216e-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="1216e-103">預期的要求中設定主應用程式必須維護的閒置執行緒的數目下限。</span><span class="sxs-lookup"><span data-stu-id="1216e-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1216e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1216e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1216e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1216e-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="1216e-106">[in]新執行緒的數目下限必須維護主機。</span><span class="sxs-lookup"><span data-stu-id="1216e-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1216e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1216e-107">Return Value</span></span>  
  
|<span data-ttu-id="1216e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1216e-108">HRESULT</span></span>|<span data-ttu-id="1216e-109">描述</span><span class="sxs-lookup"><span data-stu-id="1216e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1216e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1216e-110">S_OK</span></span>|<span data-ttu-id="1216e-111">`SetMinThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1216e-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="1216e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1216e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1216e-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="1216e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1216e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1216e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1216e-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="1216e-115">The call timed out.</span></span>|  
|<span data-ttu-id="1216e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1216e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1216e-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1216e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1216e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1216e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1216e-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="1216e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1216e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1216e-120">E_FAIL</span></span>|<span data-ttu-id="1216e-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="1216e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1216e-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="1216e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1216e-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1216e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1216e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1216e-124">E_NOTIMPL</span></span>|<span data-ttu-id="1216e-125">主機並未提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="1216e-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1216e-126">備註</span><span class="sxs-lookup"><span data-stu-id="1216e-126">Remarks</span></span>  
 <span data-ttu-id="1216e-127">主機不需要提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="1216e-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="1216e-128">在此情況下，它應該傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="1216e-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1216e-129">需求</span><span class="sxs-lookup"><span data-stu-id="1216e-129">Requirements</span></span>  
 <span data-ttu-id="1216e-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1216e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1216e-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1216e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1216e-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1216e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1216e-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1216e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1216e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1216e-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="1216e-135">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1216e-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="1216e-136">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1216e-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="1216e-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="1216e-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
