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
ms.openlocfilehash: 0b16305bc88854f1ab2ab89ab6b0d4d3e6881cf1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689467"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="0af29-102">IHostIoCompletionManager::GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="0af29-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>

<span data-ttu-id="0af29-103">取得主機可為服務 i/o 要求所分配的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="0af29-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af29-104">語法</span><span class="sxs-lookup"><span data-stu-id="0af29-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0af29-105">參數</span><span class="sxs-lookup"><span data-stu-id="0af29-105">Parameters</span></span>  

 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="0af29-106">擴展執行緒集區中的執行緒數目上限指標，該執行緒可供主機針對服務 i/o 要求進行分配。</span><span class="sxs-lookup"><span data-stu-id="0af29-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0af29-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0af29-107">Return Value</span></span>  
  
|<span data-ttu-id="0af29-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0af29-108">HRESULT</span></span>|<span data-ttu-id="0af29-109">描述</span><span class="sxs-lookup"><span data-stu-id="0af29-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0af29-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0af29-110">S_OK</span></span>|<span data-ttu-id="0af29-111">`GetMaxThreads` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="0af29-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0af29-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0af29-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0af29-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0af29-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0af29-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0af29-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0af29-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="0af29-115">The call timed out.</span></span>|  
|<span data-ttu-id="0af29-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0af29-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0af29-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0af29-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0af29-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0af29-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0af29-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="0af29-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0af29-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0af29-120">E_FAIL</span></span>|<span data-ttu-id="0af29-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0af29-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0af29-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="0af29-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0af29-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0af29-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0af29-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0af29-124">E_NOTIMPL</span></span>|<span data-ttu-id="0af29-125">主機未提供的實作為 `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="0af29-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0af29-126">備註</span><span class="sxs-lookup"><span data-stu-id="0af29-126">Remarks</span></span>  

 <span data-ttu-id="0af29-127">主機可能想要獨佔控制可分配來處理 i/o 要求的執行緒數目，例如實值、效能或擴充性。</span><span class="sxs-lookup"><span data-stu-id="0af29-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0af29-128">基於這個理由，主機不需要執行 `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="0af29-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="0af29-129">在此情況下，主機應該會從此方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="0af29-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0af29-130">需求</span><span class="sxs-lookup"><span data-stu-id="0af29-130">Requirements</span></span>  

 <span data-ttu-id="0af29-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0af29-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0af29-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0af29-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0af29-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0af29-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0af29-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0af29-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af29-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af29-135">See also</span></span>

- [<span data-ttu-id="0af29-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0af29-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0af29-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0af29-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
