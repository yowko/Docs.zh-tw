---
title: "IHostMAlloc::Alloc 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Alloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d999425be2bc5963aaa9f15b82bd951f6f564af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="2ea41-102">IHostMAlloc::Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="2ea41-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="2ea41-103">要求主機從堆積配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="2ea41-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea41-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ea41-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ea41-105">參數</span><span class="sxs-lookup"><span data-stu-id="2ea41-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="2ea41-106">[in]以位元組為單位，目前的記憶體配置要求的大小。</span><span class="sxs-lookup"><span data-stu-id="2ea41-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="2ea41-107">[in]其中一個[EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，表示配置錯誤的影響。</span><span class="sxs-lookup"><span data-stu-id="2ea41-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="2ea41-108">[out]若要配置的記憶體或如果無法完成要求為 null 指標。</span><span class="sxs-lookup"><span data-stu-id="2ea41-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ea41-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="2ea41-109">Return Value</span></span>  
  
|<span data-ttu-id="2ea41-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ea41-110">HRESULT</span></span>|<span data-ttu-id="2ea41-111">描述</span><span class="sxs-lookup"><span data-stu-id="2ea41-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ea41-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ea41-112">S_OK</span></span>|<span data-ttu-id="2ea41-113">`Alloc`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2ea41-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="2ea41-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ea41-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ea41-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2ea41-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ea41-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ea41-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ea41-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2ea41-117">The call timed out.</span></span>|  
|<span data-ttu-id="2ea41-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ea41-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ea41-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2ea41-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ea41-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ea41-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ea41-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2ea41-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ea41-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ea41-122">E_FAIL</span></span>|<span data-ttu-id="2ea41-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2ea41-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ea41-124">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="2ea41-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ea41-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2ea41-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2ea41-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2ea41-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2ea41-127">記憶體不足，無法完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="2ea41-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ea41-128">備註</span><span class="sxs-lookup"><span data-stu-id="2ea41-128">Remarks</span></span>  
 <span data-ttu-id="2ea41-129">CLR 取得的介面指標`IHostMalloc`藉由呼叫的執行個體[ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2ea41-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea41-130">需求</span><span class="sxs-lookup"><span data-stu-id="2ea41-130">Requirements</span></span>  
 <span data-ttu-id="2ea41-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ea41-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea41-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ea41-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ea41-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2ea41-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ea41-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea41-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea41-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ea41-135">See Also</span></span>  
 [<span data-ttu-id="2ea41-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="2ea41-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="2ea41-137">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="2ea41-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
