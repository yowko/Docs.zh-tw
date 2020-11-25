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
ms.openlocfilehash: 49de0398dd32970bd8ceb0fd24178e75df5d14b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713484"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="85315-102">IHostMAlloc::DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="85315-102">IHostMAlloc::DebugAlloc Method</span></span>

<span data-ttu-id="85315-103">要求主機從堆積配置指定的記憶體數量，並進一步追蹤配置記憶體的位置。</span><span class="sxs-lookup"><span data-stu-id="85315-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85315-104">語法</span><span class="sxs-lookup"><span data-stu-id="85315-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85315-105">參數</span><span class="sxs-lookup"><span data-stu-id="85315-105">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="85315-106">在目前記憶體配置要求的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="85315-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="85315-107">在其中一個 [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 值，表示配置失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="85315-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="85315-108">在正在進行調試之可執行檔的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="85315-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="85315-109">在 `pszFileName` 要求配置的行號。</span><span class="sxs-lookup"><span data-stu-id="85315-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="85315-110">擴展已配置之記憶體的指標，如果無法完成要求，則為 null。</span><span class="sxs-lookup"><span data-stu-id="85315-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85315-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="85315-111">Return Value</span></span>  
  
|<span data-ttu-id="85315-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85315-112">HRESULT</span></span>|<span data-ttu-id="85315-113">描述</span><span class="sxs-lookup"><span data-stu-id="85315-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85315-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="85315-114">S_OK</span></span>|<span data-ttu-id="85315-115">`DebugAlloc` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="85315-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="85315-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85315-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85315-117">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="85315-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85315-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85315-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85315-119">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="85315-119">The call timed out.</span></span>|  
|<span data-ttu-id="85315-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85315-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85315-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="85315-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85315-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85315-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85315-123">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="85315-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85315-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85315-124">E_FAIL</span></span>|<span data-ttu-id="85315-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="85315-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85315-126">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="85315-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85315-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="85315-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="85315-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="85315-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="85315-129">可用的記憶體不足，無法完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="85315-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85315-130">備註</span><span class="sxs-lookup"><span data-stu-id="85315-130">Remarks</span></span>  

 <span data-ttu-id="85315-131">CLR 會呼叫[IHostMemoryManager：： CreateMalloc](ihostmemorymanager-createmalloc-method.md)方法，以取得[IHostMalloc](ihostmalloc-interface.md)實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="85315-131">The CLR gets an interface pointer to an [IHostMalloc](ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="85315-132">`DebugAlloc` 允許執行時間取得程式碼檔案資訊，以便在進行偵錯工具時使用。</span><span class="sxs-lookup"><span data-stu-id="85315-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85315-133">需求</span><span class="sxs-lookup"><span data-stu-id="85315-133">Requirements</span></span>  

 <span data-ttu-id="85315-134">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85315-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85315-135">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="85315-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85315-136">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="85315-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85315-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85315-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85315-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85315-138">See also</span></span>

- [<span data-ttu-id="85315-139">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="85315-139">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="85315-140">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="85315-140">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
