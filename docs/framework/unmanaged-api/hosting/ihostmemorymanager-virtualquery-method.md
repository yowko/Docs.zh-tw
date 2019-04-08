---
title: IHostMemoryManager::VirtualQuery 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199618"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="6389d-102">IHostMemoryManager::VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="6389d-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="6389d-103">可做為對應的 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="6389d-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="6389d-104">Win32 實作`VirtualQuery`擷取呼叫處理序虛擬位址空間中的頁面範圍的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6389d-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6389d-105">語法</span><span class="sxs-lookup"><span data-stu-id="6389d-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6389d-106">參數</span><span class="sxs-lookup"><span data-stu-id="6389d-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="6389d-107">[in]要查詢的虛擬記憶體中的位址指標。</span><span class="sxs-lookup"><span data-stu-id="6389d-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="6389d-108">[out]包含指定的記憶體區域的相關資訊的結構指標。</span><span class="sxs-lookup"><span data-stu-id="6389d-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="6389d-109">[in]大小，以位元組為單位的緩衝區，`lpBuffer`指向。</span><span class="sxs-lookup"><span data-stu-id="6389d-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="6389d-110">[out]傳回的資訊緩衝區的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="6389d-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6389d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6389d-111">Return Value</span></span>  
  
|<span data-ttu-id="6389d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6389d-112">HRESULT</span></span>|<span data-ttu-id="6389d-113">描述</span><span class="sxs-lookup"><span data-stu-id="6389d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6389d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6389d-114">S_OK</span></span>|`VirtualQuery` <span data-ttu-id="6389d-115">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6389d-115">returned successfully.</span></span>|  
|<span data-ttu-id="6389d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6389d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6389d-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6389d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6389d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6389d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6389d-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6389d-119">The call timed out.</span></span>|  
|<span data-ttu-id="6389d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6389d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6389d-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6389d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6389d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6389d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6389d-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6389d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6389d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6389d-124">E_FAIL</span></span>|<span data-ttu-id="6389d-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="6389d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6389d-126">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="6389d-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6389d-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6389d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6389d-128">備註</span><span class="sxs-lookup"><span data-stu-id="6389d-128">Remarks</span></span>  
 `VirtualQuery` <span data-ttu-id="6389d-129">提供呼叫的處理序虛擬位址空間中的頁面範圍的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6389d-129">provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="6389d-130">此實作中設定的值`pResult`的位元組數目的參數傳回資訊的緩衝區，並傳回 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="6389d-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="6389d-131">在 Win32 中`VirtualQuery`函式，傳回的值是緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="6389d-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="6389d-132">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="6389d-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6389d-133">作業系統的實作`VirtualQuery`不會產生死結，並使用隨機使用者程式碼中暫止的執行緒可以執行到完成為止。</span><span class="sxs-lookup"><span data-stu-id="6389d-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="6389d-134">實作這個方法的裝載的版本時，請使用很棒的注意。</span><span class="sxs-lookup"><span data-stu-id="6389d-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6389d-135">需求</span><span class="sxs-lookup"><span data-stu-id="6389d-135">Requirements</span></span>  
 <span data-ttu-id="6389d-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6389d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6389d-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6389d-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6389d-138">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6389d-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6389d-139">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6389d-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6389d-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6389d-140">See also</span></span>

- [<span data-ttu-id="6389d-141">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="6389d-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
