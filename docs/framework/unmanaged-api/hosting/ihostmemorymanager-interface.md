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
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137347"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="06255-102">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="06255-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="06255-103">提供方法，可讓 common language runtime (CLR)，讓主應用程式，透過虛擬記憶體要求，而不是使用標準的 Win32 虛擬記憶體函式。</span><span class="sxs-lookup"><span data-stu-id="06255-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06255-104">方法</span><span class="sxs-lookup"><span data-stu-id="06255-104">Methods</span></span>  
  
|<span data-ttu-id="06255-105">方法</span><span class="sxs-lookup"><span data-stu-id="06255-105">Method</span></span>|<span data-ttu-id="06255-106">描述</span><span class="sxs-lookup"><span data-stu-id="06255-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06255-107">AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="06255-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="06255-108">Common language runtime (CLR) 已取得指定的記憶體，作業系統會告知主應用程式。</span><span class="sxs-lookup"><span data-stu-id="06255-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="06255-109">CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="06255-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="06255-110">取得的介面指標[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)用來從主應用程式所建立的堆積要求記憶體配置的執行個體。</span><span class="sxs-lookup"><span data-stu-id="06255-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="06255-111">GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="06255-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="06255-112">主應用程式所回報，請取得目前正在使用的實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="06255-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="06255-113">NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="06255-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="06255-114">主應用程式，CLR 會嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="06255-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="06255-115">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="06255-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="06255-116">註冊通知目前的記憶體負載，在電腦上的 CLR 的主機會叫用的回呼函式的指標。</span><span class="sxs-lookup"><span data-stu-id="06255-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="06255-117">ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="06255-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="06255-118">主應用程式，CLR 已完成使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="06255-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="06255-119">VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="06255-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="06255-120">做為對應的 Win32 函式，保留或認可呼叫處理序虛擬位址空間中的頁面區域的邏輯包裝函數。</span><span class="sxs-lookup"><span data-stu-id="06255-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="06255-121">VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="06255-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="06255-122">做為對應的 Win32 函式，可釋放、 取消認可，或釋放及取消認可頁面呼叫處理序虛擬位址空間內的某個區域的邏輯包裝函數。</span><span class="sxs-lookup"><span data-stu-id="06255-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="06255-123">VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="06255-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="06255-124">做為對應的 Win32 函式，可變更的認可頁面呼叫處理序虛擬位址空間中的保護區域上的邏輯包裝函數。</span><span class="sxs-lookup"><span data-stu-id="06255-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="06255-125">VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="06255-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="06255-126">做為對應的 Win32 函式，它會擷取呼叫處理序虛擬位址空間中的頁面範圍的相關資訊的邏輯包裝函數。</span><span class="sxs-lookup"><span data-stu-id="06255-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06255-127">備註</span><span class="sxs-lookup"><span data-stu-id="06255-127">Remarks</span></span>  
 `IHostMemoryManager` <span data-ttu-id="06255-128">也提供 CLR，以取得透過在堆積上提出記憶體要求，並取得處理序中的記憶體不足壓力層級指標如主應用程式所報告的方法。</span><span class="sxs-lookup"><span data-stu-id="06255-128">also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06255-129">需求</span><span class="sxs-lookup"><span data-stu-id="06255-129">Requirements</span></span>  
 <span data-ttu-id="06255-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06255-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06255-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="06255-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06255-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="06255-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="06255-133">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="06255-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="06255-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06255-134">See also</span></span>

- [<span data-ttu-id="06255-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="06255-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="06255-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="06255-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
