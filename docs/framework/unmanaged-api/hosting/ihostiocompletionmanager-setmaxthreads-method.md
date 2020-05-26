---
title: IHostIoCompletionManager::SetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 55727903a7f3c798e7472de6de5249de98af7ae7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804665"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="873b6-102">IHostIoCompletionManager::SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="873b6-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="873b6-103">設定主機 allots 至服務 i/o 要求的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="873b6-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="873b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="873b6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="873b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="873b6-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="873b6-106">在要為 i/o 要求所分配的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="873b6-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="873b6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="873b6-107">Return Value</span></span>  
  
|<span data-ttu-id="873b6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="873b6-108">HRESULT</span></span>|<span data-ttu-id="873b6-109">描述</span><span class="sxs-lookup"><span data-stu-id="873b6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="873b6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="873b6-110">S_OK</span></span>|<span data-ttu-id="873b6-111">`SetMaxThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="873b6-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="873b6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="873b6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="873b6-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="873b6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="873b6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="873b6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="873b6-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="873b6-115">The call timed out.</span></span>|  
|<span data-ttu-id="873b6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="873b6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="873b6-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="873b6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="873b6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="873b6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="873b6-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="873b6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="873b6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="873b6-120">E_FAIL</span></span>|<span data-ttu-id="873b6-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="873b6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="873b6-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="873b6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="873b6-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="873b6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="873b6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="873b6-124">E_NOTIMPL</span></span>|<span data-ttu-id="873b6-125">主機未提供的執行 `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="873b6-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="873b6-126">備註</span><span class="sxs-lookup"><span data-stu-id="873b6-126">Remarks</span></span>  
 <span data-ttu-id="873b6-127">`SetMaxThreads`提供 CLR 有機會設定 i/o 埠上服務要求可用的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="873b6-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="873b6-128">主機可能需要獨佔控制執行緒集區的大小，原因包括執行、效能或擴充性。</span><span class="sxs-lookup"><span data-stu-id="873b6-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="873b6-129">基於這個理由，主機不需要執行 `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="873b6-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="873b6-130">在此情況下，主機應該會從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="873b6-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="873b6-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="873b6-131">Requirements</span></span>  
 <span data-ttu-id="873b6-132">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="873b6-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="873b6-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="873b6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="873b6-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="873b6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="873b6-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="873b6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873b6-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="873b6-136">See also</span></span>

- [<span data-ttu-id="873b6-137">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="873b6-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="873b6-138">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="873b6-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
