---
title: "IHostMemoryManager::VirtualFree 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualFree
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 468228101403c7ce3c123401e906e3ccbe301e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="6c5f8-102">IHostMemoryManager::VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="6c5f8-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="6c5f8-103">可做為對應的 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="6c5f8-104">Win32 實作`VirtualFree`釋放、 取消的認可，或釋出並取消認可呼叫的處理序的虛擬位址空間中的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c5f8-105">語法</span><span class="sxs-lookup"><span data-stu-id="6c5f8-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c5f8-106">參數</span><span class="sxs-lookup"><span data-stu-id="6c5f8-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="6c5f8-107">[in]要釋放的虛擬記憶體分頁的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="6c5f8-108">[in]以位元組為單位，要釋放的區域大小。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="6c5f8-109">[in]釋放作業類型。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c5f8-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c5f8-110">Return Value</span></span>  
  
|<span data-ttu-id="6c5f8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c5f8-111">HRESULT</span></span>|<span data-ttu-id="6c5f8-112">描述</span><span class="sxs-lookup"><span data-stu-id="6c5f8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c5f8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c5f8-113">S_OK</span></span>|<span data-ttu-id="6c5f8-114">`VirtualFree`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="6c5f8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c5f8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c5f8-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c5f8-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c5f8-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c5f8-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-118">The call timed out.</span></span>|  
|<span data-ttu-id="6c5f8-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c5f8-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c5f8-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c5f8-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c5f8-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c5f8-122">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c5f8-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c5f8-123">E_FAIL</span></span>|<span data-ttu-id="6c5f8-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c5f8-125">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c5f8-126">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c5f8-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6c5f8-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6c5f8-128">您嘗試釋放未配置到主機的記憶體。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c5f8-129">備註</span><span class="sxs-lookup"><span data-stu-id="6c5f8-129">Remarks</span></span>  
 <span data-ttu-id="6c5f8-130">`VirtualFree`釋放與相關聯的虛擬記憶體分頁`lpAddress`透過之前呼叫的參數[ihostmemorymanager:: Virtualalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)函式。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="6c5f8-131">嘗試釋放未配置到主機的記憶體應該傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="6c5f8-132">語意都完全相同的 Win32 實作`VirtualFree`。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="6c5f8-133">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c5f8-134">需求</span><span class="sxs-lookup"><span data-stu-id="6c5f8-134">Requirements</span></span>  
 <span data-ttu-id="6c5f8-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c5f8-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c5f8-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c5f8-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c5f8-137">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6c5f8-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c5f8-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c5f8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5f8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c5f8-139">See Also</span></span>  
 [<span data-ttu-id="6c5f8-140">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="6c5f8-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="6c5f8-141">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="6c5f8-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
