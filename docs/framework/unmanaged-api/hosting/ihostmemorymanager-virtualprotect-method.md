---
title: IHostMemoryManager::VirtualProtect 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b712b7e88e6cb5693c0823799e0980d90e34ff0a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492604"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="fb7b6-102">IHostMemoryManager::VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="fb7b6-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="fb7b6-103">可做為對應的 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="fb7b6-104">Win32 實作`VirtualProtect`變更區域上的認可頁面呼叫處理序虛擬位址空間中的保護。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb7b6-105">語法</span><span class="sxs-lookup"><span data-stu-id="fb7b6-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb7b6-106">參數</span><span class="sxs-lookup"><span data-stu-id="fb7b6-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="fb7b6-107">[in]其保護的屬性會變更虛擬記憶體的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="fb7b6-108">[in]以位元組為單位的記憶體頁面變更的區域大小。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="fb7b6-109">[in]若要套用的記憶體保護類型。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="fb7b6-110">[out]先前的記憶體保護值的指標。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb7b6-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="fb7b6-111">Return Value</span></span>  
  
|<span data-ttu-id="fb7b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb7b6-112">HRESULT</span></span>|<span data-ttu-id="fb7b6-113">描述</span><span class="sxs-lookup"><span data-stu-id="fb7b6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb7b6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb7b6-114">S_OK</span></span>|<span data-ttu-id="fb7b6-115">`VirtualProtect` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="fb7b6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb7b6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb7b6-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb7b6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb7b6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb7b6-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-119">The call timed out.</span></span>|  
|<span data-ttu-id="fb7b6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb7b6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb7b6-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb7b6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb7b6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb7b6-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb7b6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb7b6-124">E_FAIL</span></span>|<span data-ttu-id="fb7b6-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb7b6-126">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb7b6-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb7b6-128">備註</span><span class="sxs-lookup"><span data-stu-id="fb7b6-128">Remarks</span></span>  
 <span data-ttu-id="fb7b6-129">這個實作`VirtualProtect`傳回 HRESULT 值，而 Win32 實作會傳回非零值，表示作業成功和零值表示失敗。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="fb7b6-130">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb7b6-131">需求</span><span class="sxs-lookup"><span data-stu-id="fb7b6-131">Requirements</span></span>  
 <span data-ttu-id="fb7b6-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb7b6-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb7b6-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb7b6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb7b6-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fb7b6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb7b6-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb7b6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7b6-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb7b6-136">See also</span></span>
- [<span data-ttu-id="fb7b6-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="fb7b6-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
