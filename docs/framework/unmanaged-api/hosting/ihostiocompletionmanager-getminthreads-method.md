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
ms.openlocfilehash: d321ce08edf4780fc5f26ac627849b9129c2f283
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673209"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="32306-102">IHostIoCompletionManager::GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="32306-102">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="32306-103">取得主機提供來處理 i/o 要求的最小線程數目。</span><span class="sxs-lookup"><span data-stu-id="32306-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32306-104">語法</span><span class="sxs-lookup"><span data-stu-id="32306-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32306-105">參數</span><span class="sxs-lookup"><span data-stu-id="32306-105">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="32306-106">擴展主機提供來處理 i/o 要求的最小線程數目的指標。</span><span class="sxs-lookup"><span data-stu-id="32306-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32306-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="32306-107">Return Value</span></span>  
  
|<span data-ttu-id="32306-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32306-108">HRESULT</span></span>|<span data-ttu-id="32306-109">描述</span><span class="sxs-lookup"><span data-stu-id="32306-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32306-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="32306-110">S_OK</span></span>|<span data-ttu-id="32306-111">`GetMinThreads` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="32306-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="32306-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32306-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32306-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="32306-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="32306-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32306-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32306-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="32306-115">The call timed out.</span></span>|  
|<span data-ttu-id="32306-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32306-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32306-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="32306-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32306-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32306-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32306-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="32306-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32306-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32306-120">E_FAIL</span></span>|<span data-ttu-id="32306-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="32306-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32306-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="32306-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32306-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="32306-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="32306-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="32306-124">E_NOTIMPL</span></span>|<span data-ttu-id="32306-125">主機未提供的實作為 `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="32306-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32306-126">備註</span><span class="sxs-lookup"><span data-stu-id="32306-126">Remarks</span></span>  

 <span data-ttu-id="32306-127">主機可能會想要對配置給服務 i/o 要求的執行緒數目進行獨佔控制權，例如，執行、效能或擴充性等原因。</span><span class="sxs-lookup"><span data-stu-id="32306-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="32306-128">基於這個理由，主機不需要執行 `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="32306-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="32306-129">在此情況下，主機應該會從此方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="32306-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32306-130">需求</span><span class="sxs-lookup"><span data-stu-id="32306-130">Requirements</span></span>  

 <span data-ttu-id="32306-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32306-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32306-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="32306-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32306-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="32306-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32306-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32306-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32306-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32306-135">See also</span></span>

- [<span data-ttu-id="32306-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="32306-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="32306-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="32306-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
