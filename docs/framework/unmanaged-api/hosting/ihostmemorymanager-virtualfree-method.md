---
title: IHostMemoryManager::VirtualFree 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03cac2b8433d6491d1fa474a0d4064ef4e260d6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099907"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="36b58-102">IHostMemoryManager::VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="36b58-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="36b58-103">可做為對應的 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="36b58-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="36b58-104">Win32 實作`VirtualFree`釋放、 取消認可，或釋出並取消認可頁面呼叫處理序虛擬位址空間內的某個區域。</span><span class="sxs-lookup"><span data-stu-id="36b58-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36b58-105">語法</span><span class="sxs-lookup"><span data-stu-id="36b58-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36b58-106">參數</span><span class="sxs-lookup"><span data-stu-id="36b58-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="36b58-107">[in]要釋放虛擬記憶體分頁的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="36b58-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="36b58-108">[in]大小 （位元組），要釋放的區域。</span><span class="sxs-lookup"><span data-stu-id="36b58-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="36b58-109">[in]釋放作業類型。</span><span class="sxs-lookup"><span data-stu-id="36b58-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36b58-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="36b58-110">Return Value</span></span>  
  
|<span data-ttu-id="36b58-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36b58-111">HRESULT</span></span>|<span data-ttu-id="36b58-112">描述</span><span class="sxs-lookup"><span data-stu-id="36b58-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36b58-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="36b58-113">S_OK</span></span>|`VirtualFree` <span data-ttu-id="36b58-114">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="36b58-114">returned successfully.</span></span>|  
|<span data-ttu-id="36b58-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36b58-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36b58-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="36b58-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36b58-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36b58-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36b58-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="36b58-118">The call timed out.</span></span>|  
|<span data-ttu-id="36b58-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36b58-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36b58-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="36b58-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36b58-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36b58-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36b58-122">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="36b58-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36b58-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36b58-123">E_FAIL</span></span>|<span data-ttu-id="36b58-124">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="36b58-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36b58-125">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="36b58-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36b58-126">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="36b58-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="36b58-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="36b58-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="36b58-128">您嘗試釋出透過主機未配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="36b58-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36b58-129">備註</span><span class="sxs-lookup"><span data-stu-id="36b58-129">Remarks</span></span>  
 `VirtualFree` <span data-ttu-id="36b58-130">釋放相關聯的虛擬記憶體分頁`lpAddress`透過先前呼叫的參數[ihostmemorymanager:: Virtualalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)函式。</span><span class="sxs-lookup"><span data-stu-id="36b58-130">frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="36b58-131">嘗試釋出透過主機未配置的記憶體應傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="36b58-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="36b58-132">語意都完全相同的 Win32 實作`VirtualFree`。</span><span class="sxs-lookup"><span data-stu-id="36b58-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="36b58-133">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="36b58-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36b58-134">需求</span><span class="sxs-lookup"><span data-stu-id="36b58-134">Requirements</span></span>  
 <span data-ttu-id="36b58-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36b58-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36b58-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36b58-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36b58-137">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="36b58-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="36b58-138">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="36b58-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="36b58-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36b58-139">See also</span></span>

- [<span data-ttu-id="36b58-140">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="36b58-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="36b58-141">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="36b58-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
