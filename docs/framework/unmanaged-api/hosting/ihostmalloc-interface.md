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
ms.openlocfilehash: ea3656fa00e84291ff7b2bdb65f9300cd7933c0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571778"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="4204a-102">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="4204a-102">IHostMalloc Interface</span></span>
<span data-ttu-id="4204a-103">提供方法，可讓 common language runtime (CLR) 會從透過主控件堆積要求更細緻的配置。</span><span class="sxs-lookup"><span data-stu-id="4204a-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4204a-104">方法</span><span class="sxs-lookup"><span data-stu-id="4204a-104">Methods</span></span>  
  
|<span data-ttu-id="4204a-105">方法</span><span class="sxs-lookup"><span data-stu-id="4204a-105">Method</span></span>|<span data-ttu-id="4204a-106">描述</span><span class="sxs-lookup"><span data-stu-id="4204a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4204a-107">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="4204a-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="4204a-108">主應用程式從堆積配置要求的記憶體數量的要求。</span><span class="sxs-lookup"><span data-stu-id="4204a-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="4204a-109">DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="4204a-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="4204a-110">要求主機從堆積配置要求的記憶體數量，並額外追蹤記憶體配置的位置。</span><span class="sxs-lookup"><span data-stu-id="4204a-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="4204a-111">Free 方法</span><span class="sxs-lookup"><span data-stu-id="4204a-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="4204a-112">釋放已使用所配置的記憶體`Alloc`方法。</span><span class="sxs-lookup"><span data-stu-id="4204a-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4204a-113">備註</span><span class="sxs-lookup"><span data-stu-id="4204a-113">Remarks</span></span>  
 <span data-ttu-id="4204a-114">CLR 取得的介面指標`IHostMalloc`藉由呼叫的執行個體[ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4204a-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4204a-115">需求</span><span class="sxs-lookup"><span data-stu-id="4204a-115">Requirements</span></span>  
 <span data-ttu-id="4204a-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4204a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4204a-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4204a-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4204a-118">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4204a-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4204a-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4204a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4204a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4204a-120">See also</span></span>
- [<span data-ttu-id="4204a-121">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="4204a-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="4204a-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4204a-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
