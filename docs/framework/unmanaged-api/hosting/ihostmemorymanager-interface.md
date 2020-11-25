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
ms.openlocfilehash: 0f71e4c45e43c2027b12998532f2b04401a51951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731328"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="4cb1a-102">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="4cb1a-102">IHostMemoryManager Interface</span></span>

<span data-ttu-id="4cb1a-103">提供可讓 common language runtime (CLR) 透過主機提出虛擬記憶體要求的方法，而不是使用標準的 Win32 虛擬記憶體函式。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4cb1a-104">方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-104">Methods</span></span>  
  
|<span data-ttu-id="4cb1a-105">方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-105">Method</span></span>|<span data-ttu-id="4cb1a-106">描述</span><span class="sxs-lookup"><span data-stu-id="4cb1a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4cb1a-107">AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-107">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="4cb1a-108">通知主機 common language runtime (CLR) 已從作業系統取得指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="4cb1a-109">CreateMAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-109">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="4cb1a-110">取得 [IHostMAlloc](ihostmalloc-interface.md) 實例的介面指標，該實例用來從主控制項建立的堆積要求記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-110">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="4cb1a-111">GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-111">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="4cb1a-112">取得目前正在使用的實體記憶體數量，如主機所報告。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="4cb1a-113">NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-113">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="4cb1a-114">通知主機 CLR 即將嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="4cb1a-115">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-115">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="4cb1a-116">註冊回呼函式的指標，主機會叫用該函式來通知 CLR 目前電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="4cb1a-117">ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-117">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="4cb1a-118">通知主機 CLR 已完成使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="4cb1a-119">VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-119">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="4cb1a-120">作為對應 Win32 函數的邏輯包裝函式，它會保留或認可呼叫進程之虛擬位址空間中的頁面區域。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="4cb1a-121">VirtualFree 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-121">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="4cb1a-122">做為對應 Win32 函數的邏輯包裝函式，它會在呼叫進程的虛擬位址空間內釋放、解除或釋放和解除頁面區域。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="4cb1a-123">VirtualProtect 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-123">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="4cb1a-124">作為對應 Win32 函數的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中變更已認可頁面區域的保護。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="4cb1a-125">VirtualQuery 方法</span><span class="sxs-lookup"><span data-stu-id="4cb1a-125">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="4cb1a-126">做為對應 Win32 函數的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中抓取頁面範圍的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cb1a-127">備註</span><span class="sxs-lookup"><span data-stu-id="4cb1a-127">Remarks</span></span>  

 <span data-ttu-id="4cb1a-128">`IHostMemoryManager` 也提供方法，讓 CLR 取得用來在堆積上提出記憶體要求的指標，以及取得進程中的記憶體壓力層級，如主機所報告。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cb1a-129">需求</span><span class="sxs-lookup"><span data-stu-id="4cb1a-129">Requirements</span></span>  

 <span data-ttu-id="4cb1a-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb1a-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb1a-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4cb1a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cb1a-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="4cb1a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cb1a-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb1a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb1a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cb1a-134">See also</span></span>

- [<span data-ttu-id="4cb1a-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="4cb1a-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="4cb1a-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4cb1a-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
