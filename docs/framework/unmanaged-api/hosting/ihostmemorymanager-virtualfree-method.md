---
title: IHostMemoryManager::VirtualFree 方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 663c01d7e4b551ecf18bdd85a63aefc43f9750e2
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="e25bb-102">IHostMemoryManager::VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="e25bb-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="e25bb-103">可做為對應的 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="e25bb-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="e25bb-104">Win32 實作`VirtualFree`釋放、 取消的認可，或釋出並取消認可呼叫的處理序的虛擬位址空間中的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="e25bb-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e25bb-105">語法</span><span class="sxs-lookup"><span data-stu-id="e25bb-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e25bb-106">參數</span><span class="sxs-lookup"><span data-stu-id="e25bb-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="e25bb-107">[in]要釋放的虛擬記憶體分頁的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="e25bb-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="e25bb-108">[in]以位元組為單位，要釋放的區域大小。</span><span class="sxs-lookup"><span data-stu-id="e25bb-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="e25bb-109">[in]釋放作業類型。</span><span class="sxs-lookup"><span data-stu-id="e25bb-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e25bb-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e25bb-110">Return Value</span></span>  
  
|<span data-ttu-id="e25bb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e25bb-111">HRESULT</span></span>|<span data-ttu-id="e25bb-112">描述</span><span class="sxs-lookup"><span data-stu-id="e25bb-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e25bb-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e25bb-113">S_OK</span></span>|<span data-ttu-id="e25bb-114">`VirtualFree` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e25bb-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="e25bb-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e25bb-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e25bb-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e25bb-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e25bb-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e25bb-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e25bb-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e25bb-118">The call timed out.</span></span>|  
|<span data-ttu-id="e25bb-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e25bb-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e25bb-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e25bb-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e25bb-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e25bb-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e25bb-122">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e25bb-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e25bb-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e25bb-123">E_FAIL</span></span>|<span data-ttu-id="e25bb-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e25bb-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e25bb-125">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="e25bb-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e25bb-126">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e25bb-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e25bb-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="e25bb-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="e25bb-128">您嘗試釋放未配置到主機的記憶體。</span><span class="sxs-lookup"><span data-stu-id="e25bb-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e25bb-129">備註</span><span class="sxs-lookup"><span data-stu-id="e25bb-129">Remarks</span></span>  
 <span data-ttu-id="e25bb-130">`VirtualFree` 釋放與相關聯的虛擬記憶體分頁`lpAddress`透過之前呼叫的參數[ihostmemorymanager:: Virtualalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)函式。</span><span class="sxs-lookup"><span data-stu-id="e25bb-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="e25bb-131">嘗試釋放未配置到主機的記憶體應該傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="e25bb-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="e25bb-132">語意都完全相同的 Win32 實作`VirtualFree`。</span><span class="sxs-lookup"><span data-stu-id="e25bb-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="e25bb-133">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="e25bb-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e25bb-134">需求</span><span class="sxs-lookup"><span data-stu-id="e25bb-134">Requirements</span></span>  
 <span data-ttu-id="e25bb-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e25bb-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e25bb-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e25bb-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e25bb-137">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e25bb-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e25bb-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e25bb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25bb-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e25bb-139">See Also</span></span>  
 [<span data-ttu-id="e25bb-140">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="e25bb-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="e25bb-141">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="e25bb-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
