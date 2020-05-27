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
ms.openlocfilehash: 89c1d7b043d4369bf16a851924711c3c9d75791e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804522"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="95478-102">IHostMemoryManager::CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="95478-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="95478-103">取得[IHostMAlloc](ihostmalloc-interface.md)實例的介面指標，用來從主機建立的堆積建立配置要求。</span><span class="sxs-lookup"><span data-stu-id="95478-103">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95478-104">語法</span><span class="sxs-lookup"><span data-stu-id="95478-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95478-105">參數</span><span class="sxs-lookup"><span data-stu-id="95478-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="95478-106">在[MALLOC_TYPE](malloc-type-enumeration.md)旗標的組合，可指定所配置記憶體的特性。</span><span class="sxs-lookup"><span data-stu-id="95478-106">[in] A combination of [MALLOC_TYPE](malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="95478-107">脫銷主機所提供之實例位址的指標 `IHostMAlloc` 。</span><span class="sxs-lookup"><span data-stu-id="95478-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95478-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="95478-108">Return Value</span></span>  
  
|<span data-ttu-id="95478-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95478-109">HRESULT</span></span>|<span data-ttu-id="95478-110">描述</span><span class="sxs-lookup"><span data-stu-id="95478-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95478-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="95478-111">S_OK</span></span>|<span data-ttu-id="95478-112">`CreateMAlloc`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="95478-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="95478-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95478-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95478-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="95478-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95478-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95478-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95478-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="95478-116">The call timed out.</span></span>|  
|<span data-ttu-id="95478-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95478-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95478-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="95478-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95478-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95478-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95478-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="95478-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95478-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95478-121">E_FAIL</span></span>|<span data-ttu-id="95478-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="95478-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95478-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="95478-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95478-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="95478-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95478-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="95478-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="95478-126">可用的實體記憶體不足，無法完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="95478-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95478-127">備註</span><span class="sxs-lookup"><span data-stu-id="95478-127">Remarks</span></span>  
 <span data-ttu-id="95478-128">`CreateMAlloc`傳回物件，允許 CLR 透過主機提出配置要求，而不是使用標準的 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="95478-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95478-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="95478-129">Requirements</span></span>  
 <span data-ttu-id="95478-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95478-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95478-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="95478-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95478-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95478-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95478-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95478-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95478-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95478-134">See also</span></span>

- [<span data-ttu-id="95478-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="95478-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="95478-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="95478-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
