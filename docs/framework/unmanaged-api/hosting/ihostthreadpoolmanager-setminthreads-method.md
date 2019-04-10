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
ms.openlocfilehash: e290f20feacc59944bb1cafded327f4316ab88d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174157"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="491bd-102">IHostThreadPoolManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="491bd-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="491bd-103">預期的要求中設定主應用程式必須維護的閒置執行緒的數目下限。</span><span class="sxs-lookup"><span data-stu-id="491bd-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="491bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="491bd-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="491bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="491bd-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="491bd-106">[in]新執行緒的數目下限必須維護主機。</span><span class="sxs-lookup"><span data-stu-id="491bd-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="491bd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="491bd-107">Return Value</span></span>  
  
|<span data-ttu-id="491bd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="491bd-108">HRESULT</span></span>|<span data-ttu-id="491bd-109">描述</span><span class="sxs-lookup"><span data-stu-id="491bd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="491bd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="491bd-110">S_OK</span></span>|`SetMinThreads` <span data-ttu-id="491bd-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="491bd-111">returned successfully.</span></span>|  
|<span data-ttu-id="491bd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="491bd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="491bd-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="491bd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="491bd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="491bd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="491bd-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="491bd-115">The call timed out.</span></span>|  
|<span data-ttu-id="491bd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="491bd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="491bd-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="491bd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="491bd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="491bd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="491bd-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="491bd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="491bd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="491bd-120">E_FAIL</span></span>|<span data-ttu-id="491bd-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="491bd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="491bd-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="491bd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="491bd-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="491bd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="491bd-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="491bd-124">E_NOTIMPL</span></span>|<span data-ttu-id="491bd-125">主機並未提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="491bd-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="491bd-126">備註</span><span class="sxs-lookup"><span data-stu-id="491bd-126">Remarks</span></span>  
 <span data-ttu-id="491bd-127">主機不需要提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="491bd-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="491bd-128">在此情況下，它應該傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="491bd-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491bd-129">需求</span><span class="sxs-lookup"><span data-stu-id="491bd-129">Requirements</span></span>  
 <span data-ttu-id="491bd-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="491bd-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491bd-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="491bd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="491bd-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="491bd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="491bd-133">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="491bd-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="491bd-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="491bd-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="491bd-135">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="491bd-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="491bd-136">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="491bd-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="491bd-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="491bd-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
