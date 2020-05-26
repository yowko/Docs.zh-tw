---
title: IHostThreadPoolManager::GetMinThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: a05cfb43b5b4a328d22c4df04049a7fa156ca080
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841928"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="2dc67-102">IHostThreadPoolManager::GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="2dc67-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="2dc67-103">取得主機線上程集區中為了預期要求而維護的閒置執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="2dc67-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc67-104">語法</span><span class="sxs-lookup"><span data-stu-id="2dc67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dc67-105">參數</span><span class="sxs-lookup"><span data-stu-id="2dc67-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="2dc67-106">脫銷主機目前維護的閒置工作者執行緒最小數目的指標。</span><span class="sxs-lookup"><span data-stu-id="2dc67-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dc67-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2dc67-107">Return Value</span></span>  
  
|<span data-ttu-id="2dc67-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2dc67-108">HRESULT</span></span>|<span data-ttu-id="2dc67-109">描述</span><span class="sxs-lookup"><span data-stu-id="2dc67-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2dc67-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2dc67-110">S_OK</span></span>|<span data-ttu-id="2dc67-111">`GetMinThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2dc67-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2dc67-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2dc67-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2dc67-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2dc67-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2dc67-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2dc67-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2dc67-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2dc67-115">The call timed out.</span></span>|  
|<span data-ttu-id="2dc67-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2dc67-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2dc67-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2dc67-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2dc67-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2dc67-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2dc67-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2dc67-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2dc67-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2dc67-120">E_FAIL</span></span>|<span data-ttu-id="2dc67-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2dc67-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2dc67-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2dc67-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2dc67-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2dc67-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2dc67-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2dc67-124">E_NOTIMPL</span></span>|<span data-ttu-id="2dc67-125">主機未提供的執行 `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="2dc67-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dc67-126">備註</span><span class="sxs-lookup"><span data-stu-id="2dc67-126">Remarks</span></span>  
 <span data-ttu-id="2dc67-127">不需要主機來提供的執行 `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="2dc67-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="2dc67-128">在此情況下，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="2dc67-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dc67-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="2dc67-129">Requirements</span></span>  
 <span data-ttu-id="2dc67-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc67-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dc67-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2dc67-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2dc67-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2dc67-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2dc67-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dc67-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc67-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dc67-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="2dc67-135">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="2dc67-135">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="2dc67-136">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="2dc67-136">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="2dc67-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="2dc67-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
