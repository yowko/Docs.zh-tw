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
ms.openlocfilehash: a2deabc5f1c7ea0f42b6d8ec3944d984854ae571
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731276"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="1bbf8-102">IHostMemoryManager::VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="1bbf8-102">IHostMemoryManager::VirtualAlloc Method</span></span>

<span data-ttu-id="1bbf8-103">作為對應 Win32 函數的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="1bbf8-104">的 Win32 執行會 `VirtualAlloc` 保留或認可呼叫進程之虛擬位址空間中的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bbf8-105">語法</span><span class="sxs-lookup"><span data-stu-id="1bbf8-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1bbf8-106">參數</span><span class="sxs-lookup"><span data-stu-id="1bbf8-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="1bbf8-107">在要配置之區域的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="1bbf8-108">在區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="1bbf8-109">在記憶體配置的類型。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="1bbf8-110">在要配置之頁面區域的記憶體保護。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="1bbf8-111">在 [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 值，表示配置失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-111">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="1bbf8-112">擴展配置的記憶體之起始位址的指標，如果無法滿足要求，則為 null。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bbf8-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="1bbf8-113">Return Value</span></span>  
  
|<span data-ttu-id="1bbf8-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bbf8-114">HRESULT</span></span>|<span data-ttu-id="1bbf8-115">描述</span><span class="sxs-lookup"><span data-stu-id="1bbf8-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bbf8-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bbf8-116">S_OK</span></span>|<span data-ttu-id="1bbf8-117">`VirtualAlloc` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="1bbf8-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1bbf8-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1bbf8-119">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1bbf8-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1bbf8-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1bbf8-121">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-121">The call timed out.</span></span>|  
|<span data-ttu-id="1bbf8-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1bbf8-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1bbf8-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1bbf8-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1bbf8-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1bbf8-125">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1bbf8-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1bbf8-126">E_FAIL</span></span>|<span data-ttu-id="1bbf8-127">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1bbf8-128">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1bbf8-129">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1bbf8-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1bbf8-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1bbf8-131">可用的記憶體不足，無法完成配置要求</span><span class="sxs-lookup"><span data-stu-id="1bbf8-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bbf8-132">備註</span><span class="sxs-lookup"><span data-stu-id="1bbf8-132">Remarks</span></span>  

 <span data-ttu-id="1bbf8-133">您可以藉由呼叫，在進程的位址空間中保留一個區域 `VirtualAlloc` 。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="1bbf8-134">`pAddress`參數包含您想要之記憶體區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="1bbf8-135">此參數通常會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-135">This parameter is typically set to null.</span></span> <span data-ttu-id="1bbf8-136">作業系統會保留您的進程可用的免費位址範圍記錄。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="1bbf8-137">若 `pAddress` 值為 null，則會指示系統保留區域以符合的位置。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="1bbf8-138">或者，您可以為記憶體區塊提供特定的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="1bbf8-139">在這兩種情況下，輸出參數 `ppMem` 會以指標的形式傳回給配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="1bbf8-140">函數本身會傳回 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="1bbf8-141">Win32 `VirtualAlloc` 函數沒有 `ppMem` 參數，而是改為將指標傳回給配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="1bbf8-142">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bbf8-143">需求</span><span class="sxs-lookup"><span data-stu-id="1bbf8-143">Requirements</span></span>  

 <span data-ttu-id="1bbf8-144">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbf8-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bbf8-145">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1bbf8-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bbf8-146">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1bbf8-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bbf8-147">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bbf8-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbf8-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bbf8-148">See also</span></span>

- [<span data-ttu-id="1bbf8-149">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="1bbf8-149">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
