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
ms.openlocfilehash: 6f58e2290afa166d48306c0bbb50edd1df36888b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804651"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="707c2-102">IHostMAlloc::Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="707c2-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="707c2-103">要求主機從堆積配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="707c2-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="707c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="707c2-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="707c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="707c2-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="707c2-106">在目前記憶體配置要求的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="707c2-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="707c2-107">在其中一個[EMemoryCriticalLevel](ememorycriticallevel-enumeration.md)值，表示配置失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="707c2-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="707c2-108">脫銷已配置記憶體的指標，如果無法完成要求，則為 null。</span><span class="sxs-lookup"><span data-stu-id="707c2-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="707c2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="707c2-109">Return Value</span></span>  
  
|<span data-ttu-id="707c2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="707c2-110">HRESULT</span></span>|<span data-ttu-id="707c2-111">描述</span><span class="sxs-lookup"><span data-stu-id="707c2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="707c2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="707c2-112">S_OK</span></span>|<span data-ttu-id="707c2-113">`Alloc`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="707c2-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="707c2-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="707c2-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="707c2-115">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="707c2-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="707c2-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="707c2-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="707c2-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="707c2-117">The call timed out.</span></span>|  
|<span data-ttu-id="707c2-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="707c2-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="707c2-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="707c2-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="707c2-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="707c2-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="707c2-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="707c2-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="707c2-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="707c2-122">E_FAIL</span></span>|<span data-ttu-id="707c2-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="707c2-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="707c2-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="707c2-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="707c2-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="707c2-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="707c2-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="707c2-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="707c2-127">沒有足夠的記憶體可用來完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="707c2-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="707c2-128">備註</span><span class="sxs-lookup"><span data-stu-id="707c2-128">Remarks</span></span>  
 <span data-ttu-id="707c2-129">CLR 會藉 `IHostMalloc` 由呼叫[IHostMemoryManager：： CreateMalloc](ihostmemorymanager-createmalloc-method.md)方法來取得實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="707c2-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707c2-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="707c2-130">Requirements</span></span>  
 <span data-ttu-id="707c2-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="707c2-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="707c2-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="707c2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="707c2-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="707c2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="707c2-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="707c2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707c2-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="707c2-135">See also</span></span>

- [<span data-ttu-id="707c2-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="707c2-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="707c2-137">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="707c2-137">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
