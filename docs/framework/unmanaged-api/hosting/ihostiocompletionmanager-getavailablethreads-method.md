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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4316412cec26ae5698918ff65b2da65de9f36ff2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779622"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="115f3-102">IHostIoCompletionManager::GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="115f3-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="115f3-103">取得 I/O 完成執行緒、 執行緒管理的主機，目前不會服務要求總數的數目。</span><span class="sxs-lookup"><span data-stu-id="115f3-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="115f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="115f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="115f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="115f3-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="115f3-106">[out]I/O 完成執行緒主機所管理目前可供服務要求的數目指標。</span><span class="sxs-lookup"><span data-stu-id="115f3-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="115f3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="115f3-107">Return Value</span></span>  
  
|<span data-ttu-id="115f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="115f3-108">HRESULT</span></span>|<span data-ttu-id="115f3-109">描述</span><span class="sxs-lookup"><span data-stu-id="115f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="115f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="115f3-110">S_OK</span></span>|<span data-ttu-id="115f3-111">`GetAvailableThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="115f3-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="115f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="115f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="115f3-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="115f3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="115f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="115f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="115f3-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="115f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="115f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="115f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="115f3-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="115f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="115f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="115f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="115f3-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="115f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="115f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="115f3-120">E_FAIL</span></span>|<span data-ttu-id="115f3-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="115f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="115f3-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="115f3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="115f3-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="115f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="115f3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="115f3-124">E_NOTIMPL</span></span>|<span data-ttu-id="115f3-125">主機並未提供的實作`GetAvailableThreads`。</span><span class="sxs-lookup"><span data-stu-id="115f3-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="115f3-126">備註</span><span class="sxs-lookup"><span data-stu-id="115f3-126">Remarks</span></span>  
 <span data-ttu-id="115f3-127">主機可能會想的 I/O 完成執行緒集區大小的專有控制權，例如實作、 效能或延展性的原因。</span><span class="sxs-lookup"><span data-stu-id="115f3-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="115f3-128">因此，如果主應用程式不需要實作`GetAvailableThreads`。</span><span class="sxs-lookup"><span data-stu-id="115f3-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="115f3-129">在此情況下，主應用程式應該從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="115f3-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="115f3-130">需求</span><span class="sxs-lookup"><span data-stu-id="115f3-130">Requirements</span></span>  
 <span data-ttu-id="115f3-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="115f3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="115f3-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="115f3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="115f3-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="115f3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="115f3-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="115f3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115f3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="115f3-135">See also</span></span>

- [<span data-ttu-id="115f3-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="115f3-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="115f3-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="115f3-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
