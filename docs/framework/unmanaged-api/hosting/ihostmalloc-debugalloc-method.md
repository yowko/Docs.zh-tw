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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8447f6fa2771128c1bdf424cb9aac141b2dfd486
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439722"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="5aa87-102">IHostMAlloc::DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="5aa87-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="5aa87-103">要求主機從堆積中，配置指定的記憶體數量，並額外追蹤記憶體配置的位置。</span><span class="sxs-lookup"><span data-stu-id="5aa87-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa87-104">語法</span><span class="sxs-lookup"><span data-stu-id="5aa87-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5aa87-105">參數</span><span class="sxs-lookup"><span data-stu-id="5aa87-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="5aa87-106">[in]以位元組為單位，目前的記憶體配置要求的大小。</span><span class="sxs-lookup"><span data-stu-id="5aa87-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="5aa87-107">[in]其中一個[EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，表示配置錯誤的影響。</span><span class="sxs-lookup"><span data-stu-id="5aa87-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="5aa87-108">[in]可執行檔進行偵錯程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="5aa87-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="5aa87-109">[in]中的行號`pszFileName`其中要求配置。</span><span class="sxs-lookup"><span data-stu-id="5aa87-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="5aa87-110">[out]若要配置的記憶體或如果無法完成要求為 null 指標。</span><span class="sxs-lookup"><span data-stu-id="5aa87-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aa87-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="5aa87-111">Return Value</span></span>  
  
|<span data-ttu-id="5aa87-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5aa87-112">HRESULT</span></span>|<span data-ttu-id="5aa87-113">描述</span><span class="sxs-lookup"><span data-stu-id="5aa87-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5aa87-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5aa87-114">S_OK</span></span>|<span data-ttu-id="5aa87-115">`DebugAlloc` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5aa87-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="5aa87-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5aa87-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5aa87-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5aa87-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5aa87-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5aa87-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5aa87-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5aa87-119">The call timed out.</span></span>|  
|<span data-ttu-id="5aa87-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5aa87-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5aa87-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5aa87-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5aa87-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5aa87-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5aa87-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5aa87-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5aa87-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5aa87-124">E_FAIL</span></span>|<span data-ttu-id="5aa87-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5aa87-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5aa87-126">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="5aa87-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5aa87-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5aa87-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5aa87-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5aa87-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5aa87-129">記憶體不足，無法完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="5aa87-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aa87-130">備註</span><span class="sxs-lookup"><span data-stu-id="5aa87-130">Remarks</span></span>  
 <span data-ttu-id="5aa87-131">CLR 取得的介面指標[IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)藉由呼叫的執行個體[ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5aa87-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="5aa87-132">`DebugAlloc` 讓執行階段取得偵錯期間使用的程式碼檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="5aa87-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aa87-133">需求</span><span class="sxs-lookup"><span data-stu-id="5aa87-133">Requirements</span></span>  
 <span data-ttu-id="5aa87-134">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5aa87-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aa87-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5aa87-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5aa87-136">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5aa87-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5aa87-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aa87-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa87-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aa87-138">See Also</span></span>  
 [<span data-ttu-id="5aa87-139">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="5aa87-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="5aa87-140">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="5aa87-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
