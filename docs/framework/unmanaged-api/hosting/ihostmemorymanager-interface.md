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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3edae4cb112f46643734c5f1612d9df36ad47e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441320"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="580ee-102">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="580ee-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="580ee-103">提供方法讓 common language runtime (CLR) 進行透過主機的虛擬記憶體要求，而不是使用標準 Win32 虛擬記憶體函式。</span><span class="sxs-lookup"><span data-stu-id="580ee-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="580ee-104">方法</span><span class="sxs-lookup"><span data-stu-id="580ee-104">Methods</span></span>  
  
|<span data-ttu-id="580ee-105">方法</span><span class="sxs-lookup"><span data-stu-id="580ee-105">Method</span></span>|<span data-ttu-id="580ee-106">描述</span><span class="sxs-lookup"><span data-stu-id="580ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="580ee-107">AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="580ee-108">通知主機 common language runtime (CLR) 已取得作業系統中指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="580ee-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="580ee-109">CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="580ee-110">取得的介面指標[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)用來要求從主應用程式所建立的堆積記憶體配置的執行個體。</span><span class="sxs-lookup"><span data-stu-id="580ee-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="580ee-111">GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="580ee-112">主應用程式報告，取得目前正在使用的實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="580ee-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="580ee-113">NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="580ee-114">通知主機在 CLR 會嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="580ee-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="580ee-115">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="580ee-116">註冊通知的電腦上目前的記憶體負載 CLR 的主機會叫用的回呼函式的指標。</span><span class="sxs-lookup"><span data-stu-id="580ee-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="580ee-117">ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="580ee-118">通知主機在 CLR 已經完成使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="580ee-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="580ee-119">VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="580ee-120">可做為對應的 Win32 函式，保留或認可呼叫的處理序的虛擬位址空間中的頁面區域的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="580ee-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="580ee-121">VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="580ee-122">可做為對應的 Win32 函式，以釋放、 取消的認可，或釋放和取消認可呼叫的處理序的虛擬位址空間中的頁面區域的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="580ee-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="580ee-123">VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="580ee-124">可做為對應的 Win32 函式，可變更的認可頁面呼叫處理序的虛擬位址空間中的保護區域上的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="580ee-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="580ee-125">VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="580ee-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="580ee-126">可做為對應的 Win32 函式，會擷取呼叫處理序的虛擬位址空間中的頁面範圍的相關資訊的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="580ee-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="580ee-127">備註</span><span class="sxs-lookup"><span data-stu-id="580ee-127">Remarks</span></span>  
 <span data-ttu-id="580ee-128">`IHostMemoryManager` 也提供 CLR，以取得的指標，請在堆積上之記憶體要求，並取得處理序中的記憶體不足壓力層級透過主應用程式所報告的方法。</span><span class="sxs-lookup"><span data-stu-id="580ee-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="580ee-129">需求</span><span class="sxs-lookup"><span data-stu-id="580ee-129">Requirements</span></span>  
 <span data-ttu-id="580ee-130">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="580ee-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="580ee-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="580ee-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="580ee-132">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="580ee-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="580ee-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="580ee-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580ee-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="580ee-134">See Also</span></span>  
 [<span data-ttu-id="580ee-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="580ee-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="580ee-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="580ee-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
