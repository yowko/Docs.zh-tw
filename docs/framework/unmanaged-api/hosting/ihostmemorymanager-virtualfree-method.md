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
ms.openlocfilehash: be006afaf5966aa4e6d11c73b92004d676c97c7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731263"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="ac257-102">IHostMemoryManager::VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="ac257-102">IHostMemoryManager::VirtualFree Method</span></span>

<span data-ttu-id="ac257-103">作為對應 Win32 函數的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="ac257-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="ac257-104">在 `VirtualFree` 呼叫進程的虛擬位址空間內，釋放、解除或釋放和解除的頁面區域的 Win32 實作為。</span><span class="sxs-lookup"><span data-stu-id="ac257-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac257-105">語法</span><span class="sxs-lookup"><span data-stu-id="ac257-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac257-106">參數</span><span class="sxs-lookup"><span data-stu-id="ac257-106">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="ac257-107">在要釋放之虛擬記憶體頁面的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="ac257-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="ac257-108">在要釋放之區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ac257-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="ac257-109">在釋放作業的類型。</span><span class="sxs-lookup"><span data-stu-id="ac257-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac257-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ac257-110">Return Value</span></span>  
  
|<span data-ttu-id="ac257-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac257-111">HRESULT</span></span>|<span data-ttu-id="ac257-112">描述</span><span class="sxs-lookup"><span data-stu-id="ac257-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac257-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac257-113">S_OK</span></span>|<span data-ttu-id="ac257-114">`VirtualFree` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="ac257-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="ac257-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac257-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac257-116">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ac257-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac257-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac257-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac257-118">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="ac257-118">The call timed out.</span></span>|  
|<span data-ttu-id="ac257-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac257-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac257-120">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ac257-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac257-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac257-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac257-122">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="ac257-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac257-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac257-123">E_FAIL</span></span>|<span data-ttu-id="ac257-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ac257-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac257-125">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="ac257-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac257-126">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ac257-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ac257-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="ac257-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="ac257-128">嘗試釋放未透過主機配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ac257-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac257-129">備註</span><span class="sxs-lookup"><span data-stu-id="ac257-129">Remarks</span></span>  

 <span data-ttu-id="ac257-130">`VirtualFree``lpAddress`透過先前對[IHostMemoryManager：： VirtualAlloc](ihostmemorymanager-virtualalloc-method.md)函數的呼叫，釋出與參數相關聯的虛擬記憶體頁面。</span><span class="sxs-lookup"><span data-stu-id="ac257-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="ac257-131">嘗試釋放未透過主機配置的記憶體，應該會傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="ac257-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="ac257-132">此語義與的 Win32 實作為相同 `VirtualFree` 。</span><span class="sxs-lookup"><span data-stu-id="ac257-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="ac257-133">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="ac257-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac257-134">需求</span><span class="sxs-lookup"><span data-stu-id="ac257-134">Requirements</span></span>  

 <span data-ttu-id="ac257-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac257-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac257-136">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ac257-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac257-137">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ac257-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac257-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac257-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac257-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac257-139">See also</span></span>

- [<span data-ttu-id="ac257-140">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="ac257-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="ac257-141">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="ac257-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
