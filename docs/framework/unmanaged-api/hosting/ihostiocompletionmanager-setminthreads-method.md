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
ms.openlocfilehash: 61f1938b114aee6d9084ccc68dce123b4924d1fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439464"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="f3988-102">IHostIoCompletionManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="f3988-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="f3988-103">將主應用程式應該配置的執行緒的最小數目設定為 I/O 完成。</span><span class="sxs-lookup"><span data-stu-id="f3988-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3988-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3988-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3988-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3988-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="f3988-106">[in]主機應該建立的 I/O 完成執行緒最小數目。</span><span class="sxs-lookup"><span data-stu-id="f3988-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3988-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f3988-107">Return Value</span></span>  
  
|<span data-ttu-id="f3988-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3988-108">HRESULT</span></span>|<span data-ttu-id="f3988-109">描述</span><span class="sxs-lookup"><span data-stu-id="f3988-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3988-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3988-110">S_OK</span></span>|<span data-ttu-id="f3988-111">`SetMinThreads` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f3988-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f3988-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f3988-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f3988-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f3988-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f3988-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3988-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f3988-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f3988-115">The call timed out.</span></span>|  
|<span data-ttu-id="f3988-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3988-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f3988-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f3988-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f3988-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f3988-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f3988-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f3988-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f3988-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f3988-120">E_FAIL</span></span>|<span data-ttu-id="f3988-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f3988-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f3988-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f3988-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f3988-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f3988-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f3988-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f3988-124">E_NOTIMPL</span></span>|<span data-ttu-id="f3988-125">主機並未提供的實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="f3988-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3988-126">備註</span><span class="sxs-lookup"><span data-stu-id="f3988-126">Remarks</span></span>  
 <span data-ttu-id="f3988-127">主機可能會想以處理 I/O 要求，例如實作、 效能或延展性原因可以配置的執行緒數目的專有控制權。</span><span class="sxs-lookup"><span data-stu-id="f3988-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="f3988-128">基於這個理由，主應用程式不需要實作`SetMinThreads`。</span><span class="sxs-lookup"><span data-stu-id="f3988-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="f3988-129">在此情況下，主應用程式應該從這個方法會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="f3988-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3988-130">需求</span><span class="sxs-lookup"><span data-stu-id="f3988-130">Requirements</span></span>  
 <span data-ttu-id="f3988-131">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3988-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3988-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3988-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3988-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f3988-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3988-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3988-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3988-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3988-135">See Also</span></span>  
 [<span data-ttu-id="f3988-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="f3988-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="f3988-137">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="f3988-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="f3988-138">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="f3988-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
