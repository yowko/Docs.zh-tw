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
ms.openlocfilehash: ce1abb75c5135a9bb23f1ad2d2acbd40d9111b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122073"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="fe30f-102">IHostThreadPoolManager::GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="fe30f-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="fe30f-103">取得主機線上程集區中為了預期要求而維護的閒置執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="fe30f-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe30f-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe30f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe30f-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe30f-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="fe30f-106">脫銷主機目前維護的閒置工作者執行緒最小數目的指標。</span><span class="sxs-lookup"><span data-stu-id="fe30f-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe30f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe30f-107">Return Value</span></span>  
  
|<span data-ttu-id="fe30f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe30f-108">HRESULT</span></span>|<span data-ttu-id="fe30f-109">描述</span><span class="sxs-lookup"><span data-stu-id="fe30f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe30f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe30f-110">S_OK</span></span>|<span data-ttu-id="fe30f-111">已成功傳回 `GetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="fe30f-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="fe30f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe30f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe30f-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="fe30f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe30f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe30f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe30f-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="fe30f-115">The call timed out.</span></span>|  
|<span data-ttu-id="fe30f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe30f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe30f-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fe30f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe30f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe30f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe30f-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="fe30f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe30f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe30f-120">E_FAIL</span></span>|<span data-ttu-id="fe30f-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fe30f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe30f-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="fe30f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe30f-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fe30f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fe30f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fe30f-124">E_NOTIMPL</span></span>|<span data-ttu-id="fe30f-125">主機未提供 `GetMinThreads`的執行。</span><span class="sxs-lookup"><span data-stu-id="fe30f-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe30f-126">備註</span><span class="sxs-lookup"><span data-stu-id="fe30f-126">Remarks</span></span>  
 <span data-ttu-id="fe30f-127">不需要主機來提供 `GetMinThreads`的執行。</span><span class="sxs-lookup"><span data-stu-id="fe30f-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="fe30f-128">在此情況下，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="fe30f-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe30f-129">需求</span><span class="sxs-lookup"><span data-stu-id="fe30f-129">Requirements</span></span>  
 <span data-ttu-id="fe30f-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe30f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe30f-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="fe30f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe30f-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fe30f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe30f-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe30f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe30f-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe30f-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="fe30f-135">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="fe30f-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="fe30f-136">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="fe30f-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="fe30f-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="fe30f-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
