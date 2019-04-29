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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8875fb24512ddfea57d5f9249e58de3c12b8c507
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796841"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="0cdf9-102">IHostIoCompletionManager::GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="0cdf9-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="0cdf9-103">取得服務 I/O 要求的主機可以配置的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cdf9-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cdf9-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cdf9-105">參數</span><span class="sxs-lookup"><span data-stu-id="0cdf9-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="0cdf9-106">[out]指向主機可以配置來服務 I/O 要求的執行緒集區中的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cdf9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0cdf9-107">Return Value</span></span>  
  
|<span data-ttu-id="0cdf9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0cdf9-108">HRESULT</span></span>|<span data-ttu-id="0cdf9-109">描述</span><span class="sxs-lookup"><span data-stu-id="0cdf9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cdf9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cdf9-110">S_OK</span></span>|<span data-ttu-id="0cdf9-111">`GetMaxThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0cdf9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0cdf9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0cdf9-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0cdf9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0cdf9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0cdf9-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-115">The call timed out.</span></span>|  
|<span data-ttu-id="0cdf9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0cdf9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0cdf9-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0cdf9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0cdf9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0cdf9-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0cdf9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0cdf9-120">E_FAIL</span></span>|<span data-ttu-id="0cdf9-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0cdf9-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0cdf9-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0cdf9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0cdf9-124">E_NOTIMPL</span></span>|<span data-ttu-id="0cdf9-125">主機並未提供的實作`GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cdf9-126">備註</span><span class="sxs-lookup"><span data-stu-id="0cdf9-126">Remarks</span></span>  
 <span data-ttu-id="0cdf9-127">主機可能會想處理 I/O 要求，例如實作、 效能或延展性的原因可以配置的執行緒數目的專有控制權。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0cdf9-128">基於這個理由，主應用程式不需要實作`GetMaxThreads`。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="0cdf9-129">在此情況下，主應用程式應該從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cdf9-130">需求</span><span class="sxs-lookup"><span data-stu-id="0cdf9-130">Requirements</span></span>  
 <span data-ttu-id="0cdf9-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cdf9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cdf9-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0cdf9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cdf9-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0cdf9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cdf9-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cdf9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdf9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cdf9-135">See also</span></span>

- [<span data-ttu-id="0cdf9-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0cdf9-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0cdf9-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0cdf9-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
