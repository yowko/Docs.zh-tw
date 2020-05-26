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
ms.openlocfilehash: 473a52b55f793abc76883b0a5cd5b2a04756d9f7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804361"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="90168-102">IHostMemoryManager::VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="90168-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="90168-103">作為對應 Win32 函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="90168-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="90168-104">的 Win32 執行會在 `VirtualProtect` 呼叫進程的虛擬位址空間中，變更已認可頁面區域的保護。</span><span class="sxs-lookup"><span data-stu-id="90168-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90168-105">語法</span><span class="sxs-lookup"><span data-stu-id="90168-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90168-106">參數</span><span class="sxs-lookup"><span data-stu-id="90168-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="90168-107">在要變更其保護屬性之虛擬記憶體基底位址的指標。</span><span class="sxs-lookup"><span data-stu-id="90168-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="90168-108">在要變更之記憶體頁面區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="90168-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="90168-109">在要套用的記憶體保護類型。</span><span class="sxs-lookup"><span data-stu-id="90168-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="90168-110">脫銷先前記憶體保護值的指標。</span><span class="sxs-lookup"><span data-stu-id="90168-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90168-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="90168-111">Return Value</span></span>  
  
|<span data-ttu-id="90168-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90168-112">HRESULT</span></span>|<span data-ttu-id="90168-113">描述</span><span class="sxs-lookup"><span data-stu-id="90168-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90168-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="90168-114">S_OK</span></span>|<span data-ttu-id="90168-115">`VirtualProtect`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="90168-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="90168-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="90168-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="90168-117">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="90168-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="90168-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="90168-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="90168-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="90168-119">The call timed out.</span></span>|  
|<span data-ttu-id="90168-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="90168-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="90168-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="90168-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="90168-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="90168-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="90168-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="90168-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="90168-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="90168-124">E_FAIL</span></span>|<span data-ttu-id="90168-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="90168-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="90168-126">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="90168-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="90168-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="90168-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90168-128">備註</span><span class="sxs-lookup"><span data-stu-id="90168-128">Remarks</span></span>  
 <span data-ttu-id="90168-129">的這個執行會傳回 `VirtualProtect` HRESULT 值，而 Win32 執行會傳回非零值來表示成功，而零值則表示失敗。</span><span class="sxs-lookup"><span data-stu-id="90168-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="90168-130">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="90168-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90168-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="90168-131">Requirements</span></span>  
 <span data-ttu-id="90168-132">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90168-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90168-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="90168-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90168-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="90168-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90168-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90168-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90168-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90168-136">See also</span></span>

- [<span data-ttu-id="90168-137">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="90168-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
