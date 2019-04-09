---
title: IHostMAlloc::Alloc 方法
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32499e74e8af9a865347bd800d3db4c303a7344c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126382"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="5ddfd-102">IHostMAlloc::Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="5ddfd-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="5ddfd-103">主應用程式從堆積配置指定的記憶體數量的要求。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ddfd-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ddfd-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ddfd-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ddfd-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="5ddfd-106">[in]以位元組為單位，目前的記憶體配置要求的大小。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="5ddfd-107">[in]其中一個[EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，表示配置失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="5ddfd-108">[out]配置的記憶體或如果無法完成要求為 null 指標。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ddfd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5ddfd-109">Return Value</span></span>  
  
|<span data-ttu-id="5ddfd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ddfd-110">HRESULT</span></span>|<span data-ttu-id="5ddfd-111">描述</span><span class="sxs-lookup"><span data-stu-id="5ddfd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ddfd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ddfd-112">S_OK</span></span>|`Alloc` <span data-ttu-id="5ddfd-113">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-113">returned successfully.</span></span>|  
|<span data-ttu-id="5ddfd-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ddfd-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ddfd-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ddfd-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ddfd-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ddfd-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-117">The call timed out.</span></span>|  
|<span data-ttu-id="5ddfd-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ddfd-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ddfd-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ddfd-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ddfd-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ddfd-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ddfd-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ddfd-122">E_FAIL</span></span>|<span data-ttu-id="5ddfd-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ddfd-124">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ddfd-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5ddfd-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5ddfd-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5ddfd-127">記憶體不足，無法完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ddfd-128">備註</span><span class="sxs-lookup"><span data-stu-id="5ddfd-128">Remarks</span></span>  
 <span data-ttu-id="5ddfd-129">CLR 取得的介面指標`IHostMalloc`藉由呼叫的執行個體[ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ddfd-130">需求</span><span class="sxs-lookup"><span data-stu-id="5ddfd-130">Requirements</span></span>  
 <span data-ttu-id="5ddfd-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ddfd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ddfd-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ddfd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ddfd-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5ddfd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5ddfd-134">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5ddfd-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ddfd-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ddfd-135">See also</span></span>

- [<span data-ttu-id="5ddfd-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="5ddfd-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="5ddfd-137">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="5ddfd-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
