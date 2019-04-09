---
title: IHostThreadPoolManager::GetMinThreads 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1230a72d06677b4d36d10a8a31d63638c1fcd41
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170686"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="977a1-102">IHostThreadPoolManager::GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="977a1-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="977a1-103">執行緒集區預期的要求中取得主控件保留的閒置執行緒的數目下限。</span><span class="sxs-lookup"><span data-stu-id="977a1-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="977a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="977a1-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="977a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="977a1-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="977a1-106">[out]主控件目前保留閒置的工作者執行緒的最小數目指標。</span><span class="sxs-lookup"><span data-stu-id="977a1-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="977a1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="977a1-107">Return Value</span></span>  
  
|<span data-ttu-id="977a1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="977a1-108">HRESULT</span></span>|<span data-ttu-id="977a1-109">描述</span><span class="sxs-lookup"><span data-stu-id="977a1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="977a1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="977a1-110">S_OK</span></span>|`GetMinThreads` <span data-ttu-id="977a1-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="977a1-111">returned successfully.</span></span>|  
|<span data-ttu-id="977a1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="977a1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="977a1-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="977a1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="977a1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="977a1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="977a1-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="977a1-115">The call timed out.</span></span>|  
|<span data-ttu-id="977a1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="977a1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="977a1-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="977a1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="977a1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="977a1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="977a1-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="977a1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="977a1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="977a1-120">E_FAIL</span></span>|<span data-ttu-id="977a1-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="977a1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="977a1-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="977a1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="977a1-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="977a1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="977a1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="977a1-124">E_NOTIMPL</span></span>|<span data-ttu-id="977a1-125">主機並未提供的實作`GetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="977a1-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="977a1-126">備註</span><span class="sxs-lookup"><span data-stu-id="977a1-126">Remarks</span></span>  
 <span data-ttu-id="977a1-127">主應用程式不需要提供的實作`GetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="977a1-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="977a1-128">在此情況下，它應該傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="977a1-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="977a1-129">需求</span><span class="sxs-lookup"><span data-stu-id="977a1-129">Requirements</span></span>  
 <span data-ttu-id="977a1-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="977a1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="977a1-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="977a1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="977a1-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="977a1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="977a1-133">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="977a1-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="977a1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="977a1-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="977a1-135">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="977a1-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="977a1-136">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="977a1-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="977a1-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="977a1-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
