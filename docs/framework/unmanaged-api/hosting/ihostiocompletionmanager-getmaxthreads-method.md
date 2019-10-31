---
title: IHostIoCompletionManager::GetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: d35fd91f2a28c392176a6dd87bd21baa964ee9a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133806"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="b2b53-102">IHostIoCompletionManager::GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b2b53-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="b2b53-103">取得主機可以為服務 i/o 要求所分配的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="b2b53-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b53-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2b53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2b53-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2b53-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="b2b53-106">脫銷執行緒集區中的執行緒最大數目的指標，可讓主機為服務 i/o 要求進行分配。</span><span class="sxs-lookup"><span data-stu-id="b2b53-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2b53-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b2b53-107">Return Value</span></span>  
  
|<span data-ttu-id="b2b53-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2b53-108">HRESULT</span></span>|<span data-ttu-id="b2b53-109">描述</span><span class="sxs-lookup"><span data-stu-id="b2b53-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2b53-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2b53-110">S_OK</span></span>|<span data-ttu-id="b2b53-111">已成功傳回 `GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="b2b53-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b2b53-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2b53-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2b53-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2b53-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2b53-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2b53-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2b53-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b2b53-115">The call timed out.</span></span>|  
|<span data-ttu-id="b2b53-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2b53-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2b53-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b2b53-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2b53-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2b53-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2b53-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b2b53-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2b53-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2b53-120">E_FAIL</span></span>|<span data-ttu-id="b2b53-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b2b53-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2b53-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="b2b53-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2b53-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b2b53-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b2b53-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b2b53-124">E_NOTIMPL</span></span>|<span data-ttu-id="b2b53-125">主機未提供 `GetMaxThreads`的執行。</span><span class="sxs-lookup"><span data-stu-id="b2b53-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2b53-126">備註</span><span class="sxs-lookup"><span data-stu-id="b2b53-126">Remarks</span></span>  
 <span data-ttu-id="b2b53-127">主機可能會想要獨佔控制可配置給處理 i/o 要求的執行緒數目，原因包括執行、效能或擴充性。</span><span class="sxs-lookup"><span data-stu-id="b2b53-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="b2b53-128">基於這個理由，不需要主機來執行 `GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="b2b53-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="b2b53-129">在此情況下，主機應該會從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="b2b53-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2b53-130">需求</span><span class="sxs-lookup"><span data-stu-id="b2b53-130">Requirements</span></span>  
 <span data-ttu-id="b2b53-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b53-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b53-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b2b53-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2b53-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b2b53-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2b53-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b53-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b53-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2b53-135">See also</span></span>

- [<span data-ttu-id="b2b53-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b2b53-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b2b53-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b2b53-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
