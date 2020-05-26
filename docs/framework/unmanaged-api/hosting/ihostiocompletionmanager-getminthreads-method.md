---
title: IHostIoCompletionManager::GetMinThreads 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: e748a731f2c6934f58a1cd838cc40ce4fd0e4652
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804726"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="15124-102">IHostIoCompletionManager::GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="15124-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="15124-103">取得主機為處理 i/o 要求所提供的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="15124-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15124-104">語法</span><span class="sxs-lookup"><span data-stu-id="15124-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15124-105">參數</span><span class="sxs-lookup"><span data-stu-id="15124-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="15124-106">脫銷主機為處理 i/o 要求所提供的最小線程數目指標。</span><span class="sxs-lookup"><span data-stu-id="15124-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15124-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="15124-107">Return Value</span></span>  
  
|<span data-ttu-id="15124-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15124-108">HRESULT</span></span>|<span data-ttu-id="15124-109">描述</span><span class="sxs-lookup"><span data-stu-id="15124-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15124-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="15124-110">S_OK</span></span>|<span data-ttu-id="15124-111">`GetMinThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="15124-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="15124-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15124-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15124-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="15124-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15124-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15124-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15124-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="15124-115">The call timed out.</span></span>|  
|<span data-ttu-id="15124-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15124-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15124-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="15124-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15124-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15124-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15124-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="15124-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15124-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15124-120">E_FAIL</span></span>|<span data-ttu-id="15124-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="15124-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15124-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="15124-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15124-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="15124-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="15124-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="15124-124">E_NOTIMPL</span></span>|<span data-ttu-id="15124-125">主機未提供的執行 `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="15124-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15124-126">備註</span><span class="sxs-lookup"><span data-stu-id="15124-126">Remarks</span></span>  
 <span data-ttu-id="15124-127">主機可能會想要獨佔控制配置給服務 i/o 要求的執行緒數目，原因包括執行、效能或擴充性。</span><span class="sxs-lookup"><span data-stu-id="15124-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="15124-128">基於這個理由，主機不需要執行 `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="15124-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="15124-129">在此情況下，主機應該會從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="15124-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15124-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="15124-130">Requirements</span></span>  
 <span data-ttu-id="15124-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15124-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15124-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="15124-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15124-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="15124-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15124-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15124-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15124-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15124-135">See also</span></span>

- [<span data-ttu-id="15124-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="15124-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="15124-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="15124-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
