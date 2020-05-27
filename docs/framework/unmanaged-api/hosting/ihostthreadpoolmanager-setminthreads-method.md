---
title: IHostThreadPoolManager::SetMinThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: c5b150b161acba3820ced367049f08153dd091aa
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842426"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="be483-102">IHostThreadPoolManager::SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="be483-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="be483-103">設定主機必須在要求中維持的最小閒置執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="be483-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be483-104">語法</span><span class="sxs-lookup"><span data-stu-id="be483-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be483-105">參數</span><span class="sxs-lookup"><span data-stu-id="be483-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="be483-106">在主機必須維護的新執行緒最小數目。</span><span class="sxs-lookup"><span data-stu-id="be483-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be483-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="be483-107">Return Value</span></span>  
  
|<span data-ttu-id="be483-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be483-108">HRESULT</span></span>|<span data-ttu-id="be483-109">描述</span><span class="sxs-lookup"><span data-stu-id="be483-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be483-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="be483-110">S_OK</span></span>|<span data-ttu-id="be483-111">`SetMinThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="be483-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="be483-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be483-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be483-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="be483-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be483-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be483-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be483-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="be483-115">The call timed out.</span></span>|  
|<span data-ttu-id="be483-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be483-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be483-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="be483-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be483-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be483-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be483-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="be483-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be483-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be483-120">E_FAIL</span></span>|<span data-ttu-id="be483-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="be483-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be483-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="be483-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be483-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="be483-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="be483-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="be483-124">E_NOTIMPL</span></span>|<span data-ttu-id="be483-125">主機未提供的執行 `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="be483-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be483-126">備註</span><span class="sxs-lookup"><span data-stu-id="be483-126">Remarks</span></span>  
 <span data-ttu-id="be483-127">不需要主機來提供的執行 `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="be483-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="be483-128">在此情況下，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="be483-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be483-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="be483-129">Requirements</span></span>  
 <span data-ttu-id="be483-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be483-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be483-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="be483-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be483-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="be483-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be483-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be483-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be483-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be483-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="be483-135">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="be483-135">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="be483-136">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="be483-136">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="be483-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="be483-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
