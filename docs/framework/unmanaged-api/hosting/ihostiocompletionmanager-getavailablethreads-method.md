---
title: IHostIoCompletionManager::GetAvailableThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 2fa429979faa04518397cf58aaa62d3e45230a76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133838"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="e835f-102">IHostIoCompletionManager::GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="e835f-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="e835f-103">取得目前未服務要求的 i/o 完成執行緒數目，這是由主機管理的執行緒總數。</span><span class="sxs-lookup"><span data-stu-id="e835f-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e835f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e835f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e835f-105">參數</span><span class="sxs-lookup"><span data-stu-id="e835f-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="e835f-106">脫銷主機所管理的 i/o 完成執行緒數目指標，目前可供服務要求使用。</span><span class="sxs-lookup"><span data-stu-id="e835f-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e835f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e835f-107">Return Value</span></span>  
  
|<span data-ttu-id="e835f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e835f-108">HRESULT</span></span>|<span data-ttu-id="e835f-109">描述</span><span class="sxs-lookup"><span data-stu-id="e835f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e835f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e835f-110">S_OK</span></span>|<span data-ttu-id="e835f-111">已成功傳回 `GetAvailableThreads`。</span><span class="sxs-lookup"><span data-stu-id="e835f-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e835f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e835f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e835f-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e835f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e835f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e835f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e835f-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e835f-115">The call timed out.</span></span>|  
|<span data-ttu-id="e835f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e835f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e835f-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e835f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e835f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e835f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e835f-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e835f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e835f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e835f-120">E_FAIL</span></span>|<span data-ttu-id="e835f-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e835f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e835f-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="e835f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e835f-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e835f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e835f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e835f-124">E_NOTIMPL</span></span>|<span data-ttu-id="e835f-125">主機未提供 `GetAvailableThreads`的執行。</span><span class="sxs-lookup"><span data-stu-id="e835f-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e835f-126">備註</span><span class="sxs-lookup"><span data-stu-id="e835f-126">Remarks</span></span>  
 <span data-ttu-id="e835f-127">主機可能會想要獨佔控制 i/o 完成執行緒集區的大小，以因應執行、效能或擴充性等原因。</span><span class="sxs-lookup"><span data-stu-id="e835f-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e835f-128">因此，不需要主機來執行 `GetAvailableThreads`。</span><span class="sxs-lookup"><span data-stu-id="e835f-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="e835f-129">在此情況下，主機應該會從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="e835f-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e835f-130">需求</span><span class="sxs-lookup"><span data-stu-id="e835f-130">Requirements</span></span>  
 <span data-ttu-id="e835f-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e835f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e835f-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e835f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e835f-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e835f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e835f-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e835f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e835f-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="e835f-135">See also</span></span>

- [<span data-ttu-id="e835f-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="e835f-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e835f-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="e835f-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
