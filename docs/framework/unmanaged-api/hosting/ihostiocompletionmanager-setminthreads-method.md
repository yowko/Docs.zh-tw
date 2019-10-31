---
title: IHostIoCompletionManager::SetMinThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: 8b1fc936b601d327ce6306f22dbec2c1078718da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133740"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="a64a3-102">IHostIoCompletionManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a64a3-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="a64a3-103">設定主機應該為 i/o 完成所配置的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="a64a3-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a64a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="a64a3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a64a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="a64a3-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="a64a3-106">在主機應該建立的 i/o 完成執行緒最小數目。</span><span class="sxs-lookup"><span data-stu-id="a64a3-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a64a3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a64a3-107">Return Value</span></span>  
  
|<span data-ttu-id="a64a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a64a3-108">HRESULT</span></span>|<span data-ttu-id="a64a3-109">描述</span><span class="sxs-lookup"><span data-stu-id="a64a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a64a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a64a3-110">S_OK</span></span>|<span data-ttu-id="a64a3-111">已成功傳回 `SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="a64a3-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="a64a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a64a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a64a3-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a64a3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a64a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a64a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a64a3-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a64a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="a64a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a64a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a64a3-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a64a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a64a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a64a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a64a3-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a64a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a64a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a64a3-120">E_FAIL</span></span>|<span data-ttu-id="a64a3-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a64a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a64a3-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="a64a3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a64a3-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a64a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a64a3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a64a3-124">E_NOTIMPL</span></span>|<span data-ttu-id="a64a3-125">主機未提供 `SetMinThreads`的執行。</span><span class="sxs-lookup"><span data-stu-id="a64a3-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a64a3-126">備註</span><span class="sxs-lookup"><span data-stu-id="a64a3-126">Remarks</span></span>  
 <span data-ttu-id="a64a3-127">主機可能會想要獨佔控制可配置給處理 i/o 要求的執行緒數目，原因包括執行、效能或擴充性。</span><span class="sxs-lookup"><span data-stu-id="a64a3-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="a64a3-128">基於這個理由，不需要主機來執行 `SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="a64a3-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="a64a3-129">在此情況下，主機應該會從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="a64a3-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a64a3-130">需求</span><span class="sxs-lookup"><span data-stu-id="a64a3-130">Requirements</span></span>  
 <span data-ttu-id="a64a3-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a64a3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a64a3-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a64a3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a64a3-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a64a3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a64a3-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a64a3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a64a3-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="a64a3-135">See also</span></span>

- [<span data-ttu-id="a64a3-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a64a3-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a64a3-137">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a64a3-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="a64a3-138">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a64a3-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
