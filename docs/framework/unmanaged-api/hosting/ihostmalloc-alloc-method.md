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
ms.openlocfilehash: dded37fdef02963f60883b289462aa6a96693b3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176301"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="07f0e-102">IHostMAlloc::Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="07f0e-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="07f0e-103">請求主機從堆分配指定的記憶體量。</span><span class="sxs-lookup"><span data-stu-id="07f0e-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f0e-104">語法</span><span class="sxs-lookup"><span data-stu-id="07f0e-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07f0e-105">參數</span><span class="sxs-lookup"><span data-stu-id="07f0e-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="07f0e-106">[在]當前記憶體分配請求的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="07f0e-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="07f0e-107">[在][EMemory臨界級別值](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)之一，指示分配失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="07f0e-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="07f0e-108">[出]指向已分配的記憶體的指標，如果無法完成請求，則為 null。</span><span class="sxs-lookup"><span data-stu-id="07f0e-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07f0e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="07f0e-109">Return Value</span></span>  
  
|<span data-ttu-id="07f0e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07f0e-110">HRESULT</span></span>|<span data-ttu-id="07f0e-111">描述</span><span class="sxs-lookup"><span data-stu-id="07f0e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07f0e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="07f0e-112">S_OK</span></span>|<span data-ttu-id="07f0e-113">`Alloc`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="07f0e-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="07f0e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07f0e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07f0e-115">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="07f0e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07f0e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07f0e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07f0e-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="07f0e-117">The call timed out.</span></span>|  
|<span data-ttu-id="07f0e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07f0e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07f0e-119">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="07f0e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07f0e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07f0e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07f0e-121">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="07f0e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07f0e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07f0e-122">E_FAIL</span></span>|<span data-ttu-id="07f0e-123">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="07f0e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07f0e-124">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="07f0e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07f0e-125">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="07f0e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="07f0e-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="07f0e-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="07f0e-127">沒有足夠的記憶體來完成分配請求。</span><span class="sxs-lookup"><span data-stu-id="07f0e-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07f0e-128">備註</span><span class="sxs-lookup"><span data-stu-id="07f0e-128">Remarks</span></span>  
 <span data-ttu-id="07f0e-129">CLR 通過調用`IHostMalloc`[IHostMemoryManager：：createMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法獲取指向實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="07f0e-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07f0e-130">需求</span><span class="sxs-lookup"><span data-stu-id="07f0e-130">Requirements</span></span>  
 <span data-ttu-id="07f0e-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07f0e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07f0e-132">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07f0e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07f0e-133">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="07f0e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07f0e-134">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f0e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f0e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07f0e-135">See also</span></span>

- [<span data-ttu-id="07f0e-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="07f0e-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="07f0e-137">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="07f0e-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
