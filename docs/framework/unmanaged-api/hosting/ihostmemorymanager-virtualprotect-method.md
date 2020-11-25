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
ms.openlocfilehash: 9822e5a1fb09e9d3bce541ff63cf766ae8611789
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731245"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="f5be2-102">IHostMemoryManager::VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="f5be2-102">IHostMemoryManager::VirtualProtect Method</span></span>

<span data-ttu-id="f5be2-103">作為對應 Win32 函數的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="f5be2-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="f5be2-104">的 Win32 執行會在 `VirtualProtect` 呼叫進程的虛擬位址空間中變更認可頁面區域的保護。</span><span class="sxs-lookup"><span data-stu-id="f5be2-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5be2-105">語法</span><span class="sxs-lookup"><span data-stu-id="f5be2-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5be2-106">參數</span><span class="sxs-lookup"><span data-stu-id="f5be2-106">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="f5be2-107">在要變更其保護屬性之虛擬記憶體的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="f5be2-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="f5be2-108">在要變更之記憶體頁面區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="f5be2-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="f5be2-109">在要套用的記憶體保護類型。</span><span class="sxs-lookup"><span data-stu-id="f5be2-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="f5be2-110">擴展先前記憶體保護值的指標。</span><span class="sxs-lookup"><span data-stu-id="f5be2-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5be2-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f5be2-111">Return Value</span></span>  
  
|<span data-ttu-id="f5be2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5be2-112">HRESULT</span></span>|<span data-ttu-id="f5be2-113">描述</span><span class="sxs-lookup"><span data-stu-id="f5be2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5be2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5be2-114">S_OK</span></span>|<span data-ttu-id="f5be2-115">`VirtualProtect` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="f5be2-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="f5be2-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5be2-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5be2-117">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f5be2-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5be2-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5be2-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5be2-119">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="f5be2-119">The call timed out.</span></span>|  
|<span data-ttu-id="f5be2-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5be2-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5be2-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f5be2-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5be2-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5be2-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5be2-123">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="f5be2-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5be2-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5be2-124">E_FAIL</span></span>|<span data-ttu-id="f5be2-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f5be2-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5be2-126">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f5be2-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5be2-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f5be2-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5be2-128">備註</span><span class="sxs-lookup"><span data-stu-id="f5be2-128">Remarks</span></span>  

 <span data-ttu-id="f5be2-129">的這個執行會傳回 `VirtualProtect` HRESULT 值，而 Win32 實值會傳回非零值以表示成功，並傳回零值表示失敗。</span><span class="sxs-lookup"><span data-stu-id="f5be2-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="f5be2-130">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="f5be2-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5be2-131">需求</span><span class="sxs-lookup"><span data-stu-id="f5be2-131">Requirements</span></span>  

 <span data-ttu-id="f5be2-132">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5be2-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5be2-133">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f5be2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5be2-134">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f5be2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5be2-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5be2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5be2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5be2-136">See also</span></span>

- [<span data-ttu-id="f5be2-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="f5be2-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
