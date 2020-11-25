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
ms.openlocfilehash: 3cb001db74587beb5417bf57738c5efb9a274591
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724815"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="b0335-102">IHostIoCompletionManager::SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b0335-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>

<span data-ttu-id="b0335-103">設定主機 allots 至服務 i/o 要求的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="b0335-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0335-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0335-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0335-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0335-105">Parameters</span></span>  

 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="b0335-106">在要為 i/o 要求進行分配的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="b0335-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0335-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b0335-107">Return Value</span></span>  
  
|<span data-ttu-id="b0335-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0335-108">HRESULT</span></span>|<span data-ttu-id="b0335-109">描述</span><span class="sxs-lookup"><span data-stu-id="b0335-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0335-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0335-110">S_OK</span></span>|<span data-ttu-id="b0335-111">`SetMaxThreads` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="b0335-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b0335-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b0335-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b0335-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b0335-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b0335-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b0335-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b0335-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="b0335-115">The call timed out.</span></span>|  
|<span data-ttu-id="b0335-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0335-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b0335-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b0335-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b0335-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b0335-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b0335-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="b0335-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b0335-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b0335-120">E_FAIL</span></span>|<span data-ttu-id="b0335-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b0335-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b0335-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b0335-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b0335-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b0335-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b0335-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b0335-124">E_NOTIMPL</span></span>|<span data-ttu-id="b0335-125">主機未提供的實作為 `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="b0335-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0335-126">備註</span><span class="sxs-lookup"><span data-stu-id="b0335-126">Remarks</span></span>  

 <span data-ttu-id="b0335-127">`SetMaxThreads` 提供 CLR 有機會設定可以在 i/o 埠上服務要求的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="b0335-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="b0335-128">主機可能需要獨佔控制執行緒集區的大小，例如執行、效能或擴充性之類的原因。</span><span class="sxs-lookup"><span data-stu-id="b0335-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="b0335-129">基於這個理由，主機不需要執行 `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="b0335-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="b0335-130">在此情況下，主機應該會從此方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="b0335-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0335-131">需求</span><span class="sxs-lookup"><span data-stu-id="b0335-131">Requirements</span></span>  

 <span data-ttu-id="b0335-132">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0335-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0335-133">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b0335-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0335-134">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b0335-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0335-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0335-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0335-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0335-136">See also</span></span>

- [<span data-ttu-id="b0335-137">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0335-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b0335-138">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0335-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
