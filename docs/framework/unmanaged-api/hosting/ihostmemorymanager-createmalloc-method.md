---
title: IHostMemoryManager::CreateMAlloc 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 194e9b73610ccb7282babf266eea2968a4f035ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951734"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="e0065-102">IHostMemoryManager::CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="e0065-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="e0065-103">取得的介面指標[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)用來進行從主應用程式所建立的堆積配置要求的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0065-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0065-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0065-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0065-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0065-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="e0065-106">[in]組合[MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md)旗標，指定要配置的記憶體的特性。</span><span class="sxs-lookup"><span data-stu-id="e0065-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="e0065-107">[out]位址指標`IHostMAlloc`主應用程式所提供的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0065-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0065-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e0065-108">Return Value</span></span>  
  
|<span data-ttu-id="e0065-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0065-109">HRESULT</span></span>|<span data-ttu-id="e0065-110">描述</span><span class="sxs-lookup"><span data-stu-id="e0065-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0065-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0065-111">S_OK</span></span>|<span data-ttu-id="e0065-112">`CreateMAlloc` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e0065-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="e0065-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0065-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0065-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e0065-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0065-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0065-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0065-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e0065-116">The call timed out.</span></span>|  
|<span data-ttu-id="e0065-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0065-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0065-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e0065-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0065-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0065-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0065-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e0065-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0065-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0065-121">E_FAIL</span></span>|<span data-ttu-id="e0065-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0065-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0065-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="e0065-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0065-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e0065-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e0065-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e0065-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e0065-126">實體記憶體不足，無法完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="e0065-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0065-127">備註</span><span class="sxs-lookup"><span data-stu-id="e0065-127">Remarks</span></span>  
 <span data-ttu-id="e0065-128">`CreateMAlloc` 傳回可讓 CLR 提出配置要求，透過的主機，而不是使用標準的 Win32 函式的物件。</span><span class="sxs-lookup"><span data-stu-id="e0065-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0065-129">需求</span><span class="sxs-lookup"><span data-stu-id="e0065-129">Requirements</span></span>  
 <span data-ttu-id="e0065-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0065-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0065-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0065-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0065-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e0065-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0065-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0065-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0065-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0065-134">See also</span></span>

- [<span data-ttu-id="e0065-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="e0065-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="e0065-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="e0065-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
