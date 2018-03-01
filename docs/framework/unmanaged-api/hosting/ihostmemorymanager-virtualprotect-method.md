---
title: "IHostMemoryManager::VirtualProtect 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77e8e163a16752934d0a1d826cc8463b3d3281bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="2d6d8-102">IHostMemoryManager::VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="2d6d8-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="2d6d8-103">可做為對應的 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="2d6d8-104">Win32 實作`VirtualProtect`變更呼叫的處理序的虛擬位址空間中的認可頁面區域上的保護。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d6d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="2d6d8-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d6d8-106">參數</span><span class="sxs-lookup"><span data-stu-id="2d6d8-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="2d6d8-107">[in]基底的保護屬性是要變更的虛擬記憶體位址指標。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="2d6d8-108">[in]以位元組為單位的記憶體頁面變更區域大小。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="2d6d8-109">[in]若要套用的記憶體保護類型。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="2d6d8-110">[out]先前的記憶體保護值的指標。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d6d8-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d6d8-111">Return Value</span></span>  
  
|<span data-ttu-id="2d6d8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d6d8-112">HRESULT</span></span>|<span data-ttu-id="2d6d8-113">描述</span><span class="sxs-lookup"><span data-stu-id="2d6d8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d6d8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d6d8-114">S_OK</span></span>|<span data-ttu-id="2d6d8-115">`VirtualProtect`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="2d6d8-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d6d8-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d6d8-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d6d8-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d6d8-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d6d8-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-119">The call timed out.</span></span>|  
|<span data-ttu-id="2d6d8-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d6d8-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d6d8-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d6d8-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d6d8-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d6d8-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d6d8-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d6d8-124">E_FAIL</span></span>|<span data-ttu-id="2d6d8-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d6d8-126">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d6d8-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d6d8-128">備註</span><span class="sxs-lookup"><span data-stu-id="2d6d8-128">Remarks</span></span>  
 <span data-ttu-id="2d6d8-129">這項實作`VirtualProtect`傳回 HRESULT 值，而 Win32 實作會傳回非零值，表示作業成功和零值表示失敗。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="2d6d8-130">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d6d8-131">需求</span><span class="sxs-lookup"><span data-stu-id="2d6d8-131">Requirements</span></span>  
 <span data-ttu-id="2d6d8-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d6d8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d6d8-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d6d8-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d6d8-134">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2d6d8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d6d8-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d6d8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d6d8-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d6d8-136">See Also</span></span>  
 [<span data-ttu-id="2d6d8-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="2d6d8-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
