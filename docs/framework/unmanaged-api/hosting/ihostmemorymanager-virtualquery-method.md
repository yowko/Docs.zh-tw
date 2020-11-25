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
ms.openlocfilehash: 6e3cb5bcec831f143d45f733c9e2f977390aade6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731237"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="505bc-102">IHostMemoryManager::VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="505bc-102">IHostMemoryManager::VirtualQuery Method</span></span>

<span data-ttu-id="505bc-103">作為對應 Win32 函數的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="505bc-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="505bc-104">的 Win32 實 `VirtualQuery` 址會在呼叫進程的虛擬位址空間中，抓取頁面範圍的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="505bc-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505bc-105">語法</span><span class="sxs-lookup"><span data-stu-id="505bc-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="505bc-106">參數</span><span class="sxs-lookup"><span data-stu-id="505bc-106">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="505bc-107">在要查詢之虛擬記憶體中的位址指標。</span><span class="sxs-lookup"><span data-stu-id="505bc-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="505bc-108">擴展結構的指標，其中包含指定之記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="505bc-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="505bc-109">在指向的緩衝區大小（以位元組為單位） `lpBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="505bc-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="505bc-110">擴展資訊緩衝區傳回的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="505bc-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="505bc-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="505bc-111">Return Value</span></span>  
  
|<span data-ttu-id="505bc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="505bc-112">HRESULT</span></span>|<span data-ttu-id="505bc-113">描述</span><span class="sxs-lookup"><span data-stu-id="505bc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="505bc-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="505bc-114">S_OK</span></span>|<span data-ttu-id="505bc-115">`VirtualQuery` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="505bc-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="505bc-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="505bc-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="505bc-117">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="505bc-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="505bc-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="505bc-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="505bc-119">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="505bc-119">The call timed out.</span></span>|  
|<span data-ttu-id="505bc-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="505bc-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="505bc-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="505bc-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="505bc-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="505bc-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="505bc-123">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="505bc-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="505bc-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="505bc-124">E_FAIL</span></span>|<span data-ttu-id="505bc-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="505bc-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="505bc-126">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="505bc-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="505bc-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="505bc-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="505bc-128">備註</span><span class="sxs-lookup"><span data-stu-id="505bc-128">Remarks</span></span>  

 <span data-ttu-id="505bc-129">`VirtualQuery` 提供有關呼叫進程的虛擬位址空間中的頁面範圍的資訊。</span><span class="sxs-lookup"><span data-stu-id="505bc-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="505bc-130">這個實值會將參數的值設定 `pResult` 為資訊緩衝區中傳回的位元組數，並傳回 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="505bc-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="505bc-131">在 Win32 `VirtualQuery` 函數中，傳回值是緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="505bc-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="505bc-132">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="505bc-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="505bc-133">作業系統的執行 `VirtualQuery` 不會產生鎖死，而且可以執行至完成，並在使用者程式碼中暫停隨機執行緒。</span><span class="sxs-lookup"><span data-stu-id="505bc-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="505bc-134">在實作為此方法的裝載版本時，請特別小心。</span><span class="sxs-lookup"><span data-stu-id="505bc-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="505bc-135">需求</span><span class="sxs-lookup"><span data-stu-id="505bc-135">Requirements</span></span>  

 <span data-ttu-id="505bc-136">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="505bc-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="505bc-137">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="505bc-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="505bc-138">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="505bc-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="505bc-139">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="505bc-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505bc-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="505bc-140">See also</span></span>

- [<span data-ttu-id="505bc-141">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="505bc-141">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
