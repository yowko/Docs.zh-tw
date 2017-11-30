---
title: "IHostMemoryManager::VirtualAlloc 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc80de55efa8740497bdd455a24e3dafc518db6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="c8989-102">IHostMemoryManager::VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="c8989-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="c8989-103">可做為對應的 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="c8989-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="c8989-104">Win32 實作`VirtualAlloc`保留或認可呼叫的處理序的虛擬位址空間中的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="c8989-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8989-105">語法</span><span class="sxs-lookup"><span data-stu-id="c8989-105">Syntax</span></span>  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8989-106">參數</span><span class="sxs-lookup"><span data-stu-id="c8989-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="c8989-107">[in]要配置的區域的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="c8989-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="c8989-108">[in]以位元組為單位，區域的大小。</span><span class="sxs-lookup"><span data-stu-id="c8989-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="c8989-109">[in]記憶體配置的類型。</span><span class="sxs-lookup"><span data-stu-id="c8989-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="c8989-110">[in]記憶體保護區域的配置的頁數。</span><span class="sxs-lookup"><span data-stu-id="c8989-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="c8989-111">[in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，指出配置失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="c8989-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="c8989-112">[out]配置的記憶體或如果無法滿足要求為 null 的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="c8989-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8989-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8989-113">Return Value</span></span>  
  
|<span data-ttu-id="c8989-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8989-114">HRESULT</span></span>|<span data-ttu-id="c8989-115">描述</span><span class="sxs-lookup"><span data-stu-id="c8989-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8989-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8989-116">S_OK</span></span>|<span data-ttu-id="c8989-117">`VirtualAlloc`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c8989-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="c8989-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8989-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8989-119">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c8989-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8989-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8989-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8989-121">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c8989-121">The call timed out.</span></span>|  
|<span data-ttu-id="c8989-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8989-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8989-123">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c8989-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8989-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8989-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8989-125">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c8989-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8989-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8989-126">E_FAIL</span></span>|<span data-ttu-id="c8989-127">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c8989-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8989-128">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="c8989-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8989-129">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c8989-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c8989-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c8989-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c8989-131">沒有足夠的記憶體可完成配置要求。</span><span class="sxs-lookup"><span data-stu-id="c8989-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8989-132">備註</span><span class="sxs-lookup"><span data-stu-id="c8989-132">Remarks</span></span>  
 <span data-ttu-id="c8989-133">在您的處理序的位址空間保留區藉由呼叫`VirtualAlloc`。</span><span class="sxs-lookup"><span data-stu-id="c8989-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="c8989-134">`pAddress`參數包含您想要的記憶體區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="c8989-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="c8989-135">此參數通常設定為 null。</span><span class="sxs-lookup"><span data-stu-id="c8989-135">This parameter is typically set to null.</span></span> <span data-ttu-id="c8989-136">作業系統會保留您的程序可使用可用的位址範圍的記錄。</span><span class="sxs-lookup"><span data-stu-id="c8989-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="c8989-137">A `pAddress` null 值會指示保留區域，只要得以透過適當的系統。</span><span class="sxs-lookup"><span data-stu-id="c8989-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="c8989-138">或者，您可以提供特定的起始位址的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="c8989-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="c8989-139">在這兩種情況下，輸出參數`ppMem`傳回的指標至配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c8989-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="c8989-140">函式本身傳回的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="c8989-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="c8989-141">Win32`VirtualAlloc`函式沒有`ppMem`參數，並改為傳回配置的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="c8989-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="c8989-142">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="c8989-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8989-143">需求</span><span class="sxs-lookup"><span data-stu-id="c8989-143">Requirements</span></span>  
 <span data-ttu-id="c8989-144">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8989-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8989-145">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8989-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8989-146">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c8989-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8989-147">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8989-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8989-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8989-148">See Also</span></span>  
 [<span data-ttu-id="c8989-149">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="c8989-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
