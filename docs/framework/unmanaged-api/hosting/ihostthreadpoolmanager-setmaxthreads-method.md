---
title: IHostThreadPoolManager::SetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 53d42afda6668acc6462c419fcefd6bc1435a34c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842448"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="3a42b-102">IHostThreadPoolManager::SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="3a42b-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="3a42b-103">設定主機可以線上程集區中維護的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="3a42b-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a42b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a42b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a42b-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a42b-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="3a42b-106">執行緒集區中的背景工作執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="3a42b-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a42b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a42b-107">Return Value</span></span>  
  
|<span data-ttu-id="3a42b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a42b-108">HRESULT</span></span>|<span data-ttu-id="3a42b-109">描述</span><span class="sxs-lookup"><span data-stu-id="3a42b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a42b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a42b-110">S_OK</span></span>|<span data-ttu-id="3a42b-111">`SetMaxThreads`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3a42b-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="3a42b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a42b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a42b-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3a42b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a42b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a42b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a42b-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="3a42b-115">The call timed out.</span></span>|  
|<span data-ttu-id="3a42b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a42b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a42b-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3a42b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a42b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a42b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a42b-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="3a42b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a42b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a42b-120">E_FAIL</span></span>|<span data-ttu-id="3a42b-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3a42b-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3a42b-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="3a42b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a42b-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3a42b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3a42b-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3a42b-124">E_NOTIMPL</span></span>|<span data-ttu-id="3a42b-125">主機未提供的執行 `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="3a42b-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a42b-126">備註</span><span class="sxs-lookup"><span data-stu-id="3a42b-126">Remarks</span></span>  
 <span data-ttu-id="3a42b-127">主機不需要允許 CLR 設定執行緒集區的大小。</span><span class="sxs-lookup"><span data-stu-id="3a42b-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="3a42b-128">某些主機可能會想要獨佔控制執行緒集區，原因包括執行、效能或擴充性。</span><span class="sxs-lookup"><span data-stu-id="3a42b-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="3a42b-129">在此情況下，主機應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="3a42b-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a42b-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="3a42b-130">Requirements</span></span>  
 <span data-ttu-id="3a42b-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a42b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a42b-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3a42b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a42b-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3a42b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a42b-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a42b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a42b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a42b-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="3a42b-136">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="3a42b-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="3a42b-137">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="3a42b-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="3a42b-138">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="3a42b-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
