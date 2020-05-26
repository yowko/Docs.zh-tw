---
title: IHostMemoryManager::VirtualAlloc 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: de41b5e0aaf835ee2d4e4f32696fe104d5830b57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804455"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="aef8f-102">IHostMemoryManager::VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="aef8f-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="aef8f-103">作為對應 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="aef8f-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="aef8f-104">的 Win32 執行會 `VirtualAlloc` 保留或認可呼叫進程之虛擬位址空間中的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="aef8f-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef8f-105">語法</span><span class="sxs-lookup"><span data-stu-id="aef8f-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef8f-106">參數</span><span class="sxs-lookup"><span data-stu-id="aef8f-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="aef8f-107">在要配置之區域的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="aef8f-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="aef8f-108">在區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="aef8f-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="aef8f-109">在記憶體配置的類型。</span><span class="sxs-lookup"><span data-stu-id="aef8f-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="aef8f-110">在要配置之頁面區域的記憶體保護。</span><span class="sxs-lookup"><span data-stu-id="aef8f-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="aef8f-111">在[EMemoryCriticalLevel](ememorycriticallevel-enumeration.md)值，表示配置失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="aef8f-111">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="aef8f-112">脫銷已配置記憶體之起始位址的指標，如果無法滿足要求，則為 null。</span><span class="sxs-lookup"><span data-stu-id="aef8f-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aef8f-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="aef8f-113">Return Value</span></span>  
  
|<span data-ttu-id="aef8f-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aef8f-114">HRESULT</span></span>|<span data-ttu-id="aef8f-115">描述</span><span class="sxs-lookup"><span data-stu-id="aef8f-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aef8f-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="aef8f-116">S_OK</span></span>|<span data-ttu-id="aef8f-117">`VirtualAlloc`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="aef8f-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="aef8f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aef8f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aef8f-119">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="aef8f-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aef8f-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aef8f-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aef8f-121">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="aef8f-121">The call timed out.</span></span>|  
|<span data-ttu-id="aef8f-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aef8f-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aef8f-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="aef8f-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aef8f-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aef8f-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aef8f-125">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="aef8f-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aef8f-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aef8f-126">E_FAIL</span></span>|<span data-ttu-id="aef8f-127">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="aef8f-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aef8f-128">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="aef8f-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aef8f-129">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="aef8f-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aef8f-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aef8f-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aef8f-131">沒有足夠的記憶體可用來完成配置要求</span><span class="sxs-lookup"><span data-stu-id="aef8f-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aef8f-132">備註</span><span class="sxs-lookup"><span data-stu-id="aef8f-132">Remarks</span></span>  
 <span data-ttu-id="aef8f-133">藉由呼叫，您可以在處理常式的位址空間中保留一個區域 `VirtualAlloc` 。</span><span class="sxs-lookup"><span data-stu-id="aef8f-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="aef8f-134">`pAddress`參數包含您想要的記憶體區塊的開頭位址。</span><span class="sxs-lookup"><span data-stu-id="aef8f-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="aef8f-135">這個參數通常會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="aef8f-135">This parameter is typically set to null.</span></span> <span data-ttu-id="aef8f-136">作業系統會保留您的進程可用的免費位址範圍記錄。</span><span class="sxs-lookup"><span data-stu-id="aef8f-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="aef8f-137">`pAddress`Null 值會指示系統保留區域，不論其是否適合。</span><span class="sxs-lookup"><span data-stu-id="aef8f-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="aef8f-138">或者，您可以為記憶體區塊提供特定的起始位址。</span><span class="sxs-lookup"><span data-stu-id="aef8f-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="aef8f-139">在這兩種情況下，輸出參數 `ppMem` 都會以指標的形式傳回給配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="aef8f-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="aef8f-140">函數本身會傳回 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="aef8f-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="aef8f-141">Win32 函式沒有 `VirtualAlloc` `ppMem` 參數，而是改為傳回已配置記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="aef8f-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="aef8f-142">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="aef8f-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef8f-143">規格需求</span><span class="sxs-lookup"><span data-stu-id="aef8f-143">Requirements</span></span>  
 <span data-ttu-id="aef8f-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aef8f-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef8f-145">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="aef8f-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aef8f-146">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="aef8f-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aef8f-147">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef8f-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef8f-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aef8f-148">See also</span></span>

- [<span data-ttu-id="aef8f-149">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="aef8f-149">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
