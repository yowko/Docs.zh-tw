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
ms.openlocfilehash: 8bcb01f4a19e6043bd59fe6f1565cdf35ed1f77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136717"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="45cb1-102">IHostMemoryManager::CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="45cb1-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="45cb1-103">取得[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)實例的介面指標，用來從主機建立的堆積建立配置要求。</span><span class="sxs-lookup"><span data-stu-id="45cb1-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cb1-104">語法</span><span class="sxs-lookup"><span data-stu-id="45cb1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45cb1-105">參數</span><span class="sxs-lookup"><span data-stu-id="45cb1-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="45cb1-106">在[MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md)旗標的組合，可指定所配置記憶體的特性。</span><span class="sxs-lookup"><span data-stu-id="45cb1-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="45cb1-107">脫銷主機所提供的 `IHostMAlloc` 實例位址的指標。</span><span class="sxs-lookup"><span data-stu-id="45cb1-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45cb1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="45cb1-108">Return Value</span></span>  
  
|<span data-ttu-id="45cb1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45cb1-109">HRESULT</span></span>|<span data-ttu-id="45cb1-110">描述</span><span class="sxs-lookup"><span data-stu-id="45cb1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45cb1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="45cb1-111">S_OK</span></span>|<span data-ttu-id="45cb1-112">已成功傳回 `CreateMAlloc`。</span><span class="sxs-lookup"><span data-stu-id="45cb1-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="45cb1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45cb1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45cb1-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="45cb1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45cb1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45cb1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45cb1-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="45cb1-116">The call timed out.</span></span>|  
|<span data-ttu-id="45cb1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45cb1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45cb1-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="45cb1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45cb1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45cb1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45cb1-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="45cb1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45cb1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45cb1-121">E_FAIL</span></span>|<span data-ttu-id="45cb1-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="45cb1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45cb1-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="45cb1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45cb1-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="45cb1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="45cb1-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="45cb1-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="45cb1-126">可用的實體記憶體不足，無法完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="45cb1-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45cb1-127">備註</span><span class="sxs-lookup"><span data-stu-id="45cb1-127">Remarks</span></span>  
 <span data-ttu-id="45cb1-128">`CreateMAlloc` 會傳回物件，允許 CLR 透過主機進行配置要求，而不是使用標準的 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="45cb1-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45cb1-129">需求</span><span class="sxs-lookup"><span data-stu-id="45cb1-129">Requirements</span></span>  
 <span data-ttu-id="45cb1-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45cb1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45cb1-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="45cb1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45cb1-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="45cb1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45cb1-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45cb1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cb1-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="45cb1-134">See also</span></span>

- [<span data-ttu-id="45cb1-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="45cb1-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="45cb1-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="45cb1-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
