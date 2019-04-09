---
title: IHostMalloc 介面
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2a7a29ef1dc85c2ad554995286e5137fcb104be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136405"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="82063-102">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="82063-102">IHostMalloc Interface</span></span>
<span data-ttu-id="82063-103">提供方法，可讓 common language runtime (CLR) 會從透過主控件堆積要求更細緻的配置。</span><span class="sxs-lookup"><span data-stu-id="82063-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82063-104">方法</span><span class="sxs-lookup"><span data-stu-id="82063-104">Methods</span></span>  
  
|<span data-ttu-id="82063-105">方法</span><span class="sxs-lookup"><span data-stu-id="82063-105">Method</span></span>|<span data-ttu-id="82063-106">描述</span><span class="sxs-lookup"><span data-stu-id="82063-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82063-107">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="82063-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="82063-108">主應用程式從堆積配置要求的記憶體數量的要求。</span><span class="sxs-lookup"><span data-stu-id="82063-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="82063-109">DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="82063-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="82063-110">要求主機從堆積配置要求的記憶體數量，並額外追蹤記憶體配置的位置。</span><span class="sxs-lookup"><span data-stu-id="82063-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="82063-111">Free 方法</span><span class="sxs-lookup"><span data-stu-id="82063-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="82063-112">釋放已使用所配置的記憶體`Alloc`方法。</span><span class="sxs-lookup"><span data-stu-id="82063-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82063-113">備註</span><span class="sxs-lookup"><span data-stu-id="82063-113">Remarks</span></span>  
 <span data-ttu-id="82063-114">CLR 取得的介面指標`IHostMalloc`藉由呼叫的執行個體[ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="82063-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82063-115">需求</span><span class="sxs-lookup"><span data-stu-id="82063-115">Requirements</span></span>  
 <span data-ttu-id="82063-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82063-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82063-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82063-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82063-118">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="82063-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="82063-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="82063-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82063-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82063-120">See also</span></span>

- [<span data-ttu-id="82063-121">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="82063-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="82063-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="82063-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
