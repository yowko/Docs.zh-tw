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
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804608"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="d230b-102">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="d230b-102">IHostMalloc Interface</span></span>
<span data-ttu-id="d230b-103">提供的方法可讓 common language runtime （CLR）透過主機要求堆積中的精細配置。</span><span class="sxs-lookup"><span data-stu-id="d230b-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d230b-104">方法</span><span class="sxs-lookup"><span data-stu-id="d230b-104">Methods</span></span>  
  
|<span data-ttu-id="d230b-105">方法</span><span class="sxs-lookup"><span data-stu-id="d230b-105">Method</span></span>|<span data-ttu-id="d230b-106">描述</span><span class="sxs-lookup"><span data-stu-id="d230b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d230b-107">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="d230b-107">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="d230b-108">要求主機從堆積配置要求的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="d230b-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="d230b-109">DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="d230b-109">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="d230b-110">要求主機從堆積配置要求的記憶體數量，並另外追蹤記憶體的配置位置。</span><span class="sxs-lookup"><span data-stu-id="d230b-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="d230b-111">Free 方法</span><span class="sxs-lookup"><span data-stu-id="d230b-111">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="d230b-112">釋放使用方法所配置的記憶體 `Alloc` 。</span><span class="sxs-lookup"><span data-stu-id="d230b-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d230b-113">備註</span><span class="sxs-lookup"><span data-stu-id="d230b-113">Remarks</span></span>  
 <span data-ttu-id="d230b-114">CLR 會藉 `IHostMalloc` 由呼叫[IHostMemoryManager：： CreateMalloc](ihostmemorymanager-createmalloc-method.md)方法來取得實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="d230b-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d230b-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="d230b-115">Requirements</span></span>  
 <span data-ttu-id="d230b-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d230b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d230b-117">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d230b-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d230b-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d230b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d230b-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d230b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d230b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d230b-120">See also</span></span>

- [<span data-ttu-id="d230b-121">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="d230b-121">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="d230b-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d230b-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
