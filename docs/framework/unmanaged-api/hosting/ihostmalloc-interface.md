---
title: "IHostMalloc 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1690f5fe8f1417e6547ed94db8c71f079ebf5e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="70db4-102">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="70db4-102">IHostMalloc Interface</span></span>
<span data-ttu-id="70db4-103">提供方法讓 common language runtime (CLR) 會從透過主機堆積要求更細緻的配置。</span><span class="sxs-lookup"><span data-stu-id="70db4-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70db4-104">方法</span><span class="sxs-lookup"><span data-stu-id="70db4-104">Methods</span></span>  
  
|<span data-ttu-id="70db4-105">方法</span><span class="sxs-lookup"><span data-stu-id="70db4-105">Method</span></span>|<span data-ttu-id="70db4-106">描述</span><span class="sxs-lookup"><span data-stu-id="70db4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70db4-107">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="70db4-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="70db4-108">要求主機從堆積配置要求的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="70db4-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="70db4-109">DebugAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="70db4-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="70db4-110">要求主機從堆積配置要求的記憶體數量，並額外追蹤記憶體配置的位置。</span><span class="sxs-lookup"><span data-stu-id="70db4-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="70db4-111">Free 方法</span><span class="sxs-lookup"><span data-stu-id="70db4-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="70db4-112">釋放記憶體取消配置使用`Alloc`方法。</span><span class="sxs-lookup"><span data-stu-id="70db4-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70db4-113">備註</span><span class="sxs-lookup"><span data-stu-id="70db4-113">Remarks</span></span>  
 <span data-ttu-id="70db4-114">CLR 取得的介面指標`IHostMalloc`藉由呼叫的執行個體[ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="70db4-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70db4-115">需求</span><span class="sxs-lookup"><span data-stu-id="70db4-115">Requirements</span></span>  
 <span data-ttu-id="70db4-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70db4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70db4-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70db4-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70db4-118">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="70db4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70db4-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70db4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70db4-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="70db4-120">See Also</span></span>  
 [<span data-ttu-id="70db4-121">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="70db4-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="70db4-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="70db4-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
