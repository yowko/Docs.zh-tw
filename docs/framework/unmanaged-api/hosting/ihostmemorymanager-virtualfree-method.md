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
ms.openlocfilehash: 4d37b7d803509ebfa861b7502d419f868bd12e11
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804380"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="58bb5-102">IHostMemoryManager::VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="58bb5-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="58bb5-103">作為對應 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="58bb5-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="58bb5-104">在 `VirtualFree` 呼叫進程的虛擬位址空間內，版本、解除或釋放和解除頁面區域的 Win32 執行。</span><span class="sxs-lookup"><span data-stu-id="58bb5-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58bb5-105">語法</span><span class="sxs-lookup"><span data-stu-id="58bb5-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58bb5-106">參數</span><span class="sxs-lookup"><span data-stu-id="58bb5-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="58bb5-107">在要釋放之虛擬記憶體頁面的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="58bb5-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="58bb5-108">在要釋放之區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="58bb5-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="58bb5-109">在釋放作業的類型。</span><span class="sxs-lookup"><span data-stu-id="58bb5-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58bb5-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="58bb5-110">Return Value</span></span>  
  
|<span data-ttu-id="58bb5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58bb5-111">HRESULT</span></span>|<span data-ttu-id="58bb5-112">描述</span><span class="sxs-lookup"><span data-stu-id="58bb5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58bb5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="58bb5-113">S_OK</span></span>|<span data-ttu-id="58bb5-114">`VirtualFree`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="58bb5-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="58bb5-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58bb5-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58bb5-116">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="58bb5-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58bb5-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58bb5-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58bb5-118">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="58bb5-118">The call timed out.</span></span>|  
|<span data-ttu-id="58bb5-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58bb5-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58bb5-120">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="58bb5-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58bb5-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58bb5-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58bb5-122">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="58bb5-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58bb5-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58bb5-123">E_FAIL</span></span>|<span data-ttu-id="58bb5-124">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="58bb5-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58bb5-125">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="58bb5-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58bb5-126">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="58bb5-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="58bb5-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="58bb5-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="58bb5-128">嘗試釋放未透過主機所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="58bb5-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58bb5-129">備註</span><span class="sxs-lookup"><span data-stu-id="58bb5-129">Remarks</span></span>  
 <span data-ttu-id="58bb5-130">`VirtualFree``lpAddress`透過先前對[IHostMemoryManager：： VirtualAlloc](ihostmemorymanager-virtualalloc-method.md)函數的呼叫，釋出與參數相關聯的虛擬記憶體頁面。</span><span class="sxs-lookup"><span data-stu-id="58bb5-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="58bb5-131">嘗試釋放未透過主機配置的記憶體，應該會傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="58bb5-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="58bb5-132">此語義與的 Win32 執行方式相同 `VirtualFree` 。</span><span class="sxs-lookup"><span data-stu-id="58bb5-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="58bb5-133">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="58bb5-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58bb5-134">規格需求</span><span class="sxs-lookup"><span data-stu-id="58bb5-134">Requirements</span></span>  
 <span data-ttu-id="58bb5-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58bb5-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58bb5-136">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="58bb5-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58bb5-137">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="58bb5-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58bb5-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58bb5-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bb5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58bb5-139">See also</span></span>

- [<span data-ttu-id="58bb5-140">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="58bb5-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="58bb5-141">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="58bb5-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
