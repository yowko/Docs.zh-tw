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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fd37546c63ef5e5f25686e105247555dfeb132a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222779"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="cef44-102">IHostIoCompletionManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="cef44-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="cef44-103">I/O 完成設定主應用程式應該配置的執行緒最小數目。</span><span class="sxs-lookup"><span data-stu-id="cef44-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cef44-104">語法</span><span class="sxs-lookup"><span data-stu-id="cef44-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cef44-105">參數</span><span class="sxs-lookup"><span data-stu-id="cef44-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="cef44-106">[in]應該建立主應用程式的 I/O 完成執行緒的數目下限。</span><span class="sxs-lookup"><span data-stu-id="cef44-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cef44-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cef44-107">Return Value</span></span>  
  
|<span data-ttu-id="cef44-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cef44-108">HRESULT</span></span>|<span data-ttu-id="cef44-109">描述</span><span class="sxs-lookup"><span data-stu-id="cef44-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cef44-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cef44-110">S_OK</span></span>|`SetMinThreads` <span data-ttu-id="cef44-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="cef44-111">returned successfully.</span></span>|  
|<span data-ttu-id="cef44-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cef44-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cef44-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cef44-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cef44-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cef44-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cef44-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="cef44-115">The call timed out.</span></span>|  
|<span data-ttu-id="cef44-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cef44-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cef44-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="cef44-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cef44-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cef44-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cef44-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="cef44-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cef44-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cef44-120">E_FAIL</span></span>|<span data-ttu-id="cef44-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="cef44-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cef44-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="cef44-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cef44-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cef44-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cef44-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="cef44-124">E_NOTIMPL</span></span>|<span data-ttu-id="cef44-125">主機並未提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="cef44-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cef44-126">備註</span><span class="sxs-lookup"><span data-stu-id="cef44-126">Remarks</span></span>  
 <span data-ttu-id="cef44-127">主機可能會想處理 I/O 要求，例如實作、 效能或延展性的原因可以配置的執行緒數目的專有控制權。</span><span class="sxs-lookup"><span data-stu-id="cef44-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="cef44-128">基於這個理由，主應用程式不需要實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="cef44-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="cef44-129">在此情況下，主應用程式應該從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="cef44-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cef44-130">需求</span><span class="sxs-lookup"><span data-stu-id="cef44-130">Requirements</span></span>  
 <span data-ttu-id="cef44-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cef44-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cef44-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cef44-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cef44-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cef44-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cef44-134">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="cef44-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cef44-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cef44-135">See also</span></span>

- [<span data-ttu-id="cef44-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="cef44-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="cef44-137">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="cef44-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="cef44-138">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="cef44-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
