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
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136770"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="0dbd8-102">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="0dbd8-102">IHostMalloc Interface</span></span>
<span data-ttu-id="0dbd8-103">提供的方法可讓 common language runtime （CLR）透過主機要求堆積中的精細配置。</span><span class="sxs-lookup"><span data-stu-id="0dbd8-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0dbd8-104">方法</span><span class="sxs-lookup"><span data-stu-id="0dbd8-104">Methods</span></span>  
  
|<span data-ttu-id="0dbd8-105">方法</span><span class="sxs-lookup"><span data-stu-id="0dbd8-105">Method</span></span>|<span data-ttu-id="0dbd8-106">描述</span><span class="sxs-lookup"><span data-stu-id="0dbd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0dbd8-107">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="0dbd8-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="0dbd8-108">要求主機從堆積配置要求的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="0dbd8-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="0dbd8-109">DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="0dbd8-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="0dbd8-110">要求主機從堆積配置要求的記憶體數量，並另外追蹤記憶體的配置位置。</span><span class="sxs-lookup"><span data-stu-id="0dbd8-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="0dbd8-111">Free 方法</span><span class="sxs-lookup"><span data-stu-id="0dbd8-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="0dbd8-112">釋放使用 `Alloc` 方法所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0dbd8-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dbd8-113">備註</span><span class="sxs-lookup"><span data-stu-id="0dbd8-113">Remarks</span></span>  
 <span data-ttu-id="0dbd8-114">CLR 會藉由呼叫[IHostMemoryManager：： CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法，取得 `IHostMalloc` 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="0dbd8-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dbd8-115">需求</span><span class="sxs-lookup"><span data-stu-id="0dbd8-115">Requirements</span></span>  
 <span data-ttu-id="0dbd8-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0dbd8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dbd8-117">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0dbd8-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0dbd8-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0dbd8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0dbd8-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dbd8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dbd8-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="0dbd8-120">See also</span></span>

- [<span data-ttu-id="0dbd8-121">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="0dbd8-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="0dbd8-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="0dbd8-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
