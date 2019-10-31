---
title: IHostMemoryManager 介面
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128654"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="6b20e-102">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="6b20e-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="6b20e-103">提供的方法可讓 common language runtime （CLR）透過主機提出虛擬記憶體要求，而不是使用標準的 Win32 虛擬記憶體函式。</span><span class="sxs-lookup"><span data-stu-id="6b20e-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b20e-104">方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-104">Methods</span></span>  
  
|<span data-ttu-id="6b20e-105">方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-105">Method</span></span>|<span data-ttu-id="6b20e-106">描述</span><span class="sxs-lookup"><span data-stu-id="6b20e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b20e-107">AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="6b20e-108">通知主機 common language runtime （CLR）已從作業系統取得指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="6b20e-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="6b20e-109">CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="6b20e-110">取得[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)實例的介面指標，用來向主機所建立的堆積要求記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="6b20e-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="6b20e-111">GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="6b20e-112">取得目前正在使用的實體記憶體數量（由主機所報告）。</span><span class="sxs-lookup"><span data-stu-id="6b20e-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="6b20e-113">NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="6b20e-114">通知主機 CLR 即將嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="6b20e-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="6b20e-115">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="6b20e-116">註冊主機所叫用的回呼函式指標，以通知 CLR 目前電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="6b20e-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="6b20e-117">ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="6b20e-118">通知主機 CLR 已使用指定的記憶體完成。</span><span class="sxs-lookup"><span data-stu-id="6b20e-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="6b20e-119">VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="6b20e-120">作為對應 Win32 函式的邏輯包裝函式，它會保留或認可呼叫進程之虛擬位址空間中的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="6b20e-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6b20e-121">VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="6b20e-122">做為對應的 Win32 函式的邏輯包裝函式，它會釋放、解除或釋放和解除呼叫進程之虛擬位址空間內的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="6b20e-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6b20e-123">VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="6b20e-124">做為對應的 Win32 函式的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中變更已認可頁面區域的保護。</span><span class="sxs-lookup"><span data-stu-id="6b20e-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6b20e-125">VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="6b20e-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="6b20e-126">做為對應的 Win32 函式的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中，抓取某個頁面範圍的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6b20e-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b20e-127">備註</span><span class="sxs-lookup"><span data-stu-id="6b20e-127">Remarks</span></span>  
 <span data-ttu-id="6b20e-128">`IHostMemoryManager` 也會提供方法，讓 CLR 取得要在堆積上進行記憶體要求的指標，以及取得進程中的記憶體壓力層級（由主機所報告）。</span><span class="sxs-lookup"><span data-stu-id="6b20e-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b20e-129">需求</span><span class="sxs-lookup"><span data-stu-id="6b20e-129">Requirements</span></span>  
 <span data-ttu-id="6b20e-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b20e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b20e-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6b20e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b20e-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6b20e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b20e-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b20e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b20e-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b20e-134">See also</span></span>

- [<span data-ttu-id="6b20e-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="6b20e-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="6b20e-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6b20e-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
