---
title: IHostMAlloc::DebugAlloc 方法
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178029"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="5b52f-102">IHostMAlloc::DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="5b52f-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="5b52f-103">請求主機從堆中分配指定數量的記憶體，並另外跟蹤記憶體的分配位置。</span><span class="sxs-lookup"><span data-stu-id="5b52f-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b52f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b52f-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b52f-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b52f-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="5b52f-106">[在]當前記憶體分配請求的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="5b52f-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="5b52f-107">[在][EMemory臨界級別值](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)之一，指示分配失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="5b52f-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="5b52f-108">[在]正在調試的可執行檔的代碼檔。</span><span class="sxs-lookup"><span data-stu-id="5b52f-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="5b52f-109">[在]請求分配`pszFileName`中的行號。</span><span class="sxs-lookup"><span data-stu-id="5b52f-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="5b52f-110">[出]指向已分配的記憶體的指標，如果無法完成請求，則為 null。</span><span class="sxs-lookup"><span data-stu-id="5b52f-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b52f-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="5b52f-111">Return Value</span></span>  
  
|<span data-ttu-id="5b52f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b52f-112">HRESULT</span></span>|<span data-ttu-id="5b52f-113">描述</span><span class="sxs-lookup"><span data-stu-id="5b52f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b52f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b52f-114">S_OK</span></span>|<span data-ttu-id="5b52f-115">`DebugAlloc`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="5b52f-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="5b52f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b52f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b52f-117">CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="5b52f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b52f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b52f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b52f-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="5b52f-119">The call timed out.</span></span>|  
|<span data-ttu-id="5b52f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b52f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b52f-121">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="5b52f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b52f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b52f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b52f-123">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="5b52f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b52f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b52f-124">E_FAIL</span></span>|<span data-ttu-id="5b52f-125">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="5b52f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b52f-126">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="5b52f-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b52f-127">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5b52f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5b52f-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5b52f-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5b52f-129">沒有足夠的記憶體來完成分配請求。</span><span class="sxs-lookup"><span data-stu-id="5b52f-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b52f-130">備註</span><span class="sxs-lookup"><span data-stu-id="5b52f-130">Remarks</span></span>  
 <span data-ttu-id="5b52f-131">CLR 通過調用[IHostMemoryManagerManager：：createMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法獲取指向[IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="5b52f-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="5b52f-132">`DebugAlloc`允許運行時獲取代碼檔資訊，供調試期間使用。</span><span class="sxs-lookup"><span data-stu-id="5b52f-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b52f-133">需求</span><span class="sxs-lookup"><span data-stu-id="5b52f-133">Requirements</span></span>  
 <span data-ttu-id="5b52f-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b52f-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b52f-135">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b52f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b52f-136">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5b52f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b52f-137">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b52f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b52f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b52f-138">See also</span></span>

- [<span data-ttu-id="5b52f-139">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="5b52f-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="5b52f-140">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="5b52f-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
