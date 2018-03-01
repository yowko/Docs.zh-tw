---
title: "ICLRGCManager2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4a8b51cf4297c1ccadbef8730c06148263d310e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="b34f4-102">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="b34f4-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="b34f4-103">提供方法，讓主應用程式與 common language runtime 的記憶體回收系統互動。</span><span class="sxs-lookup"><span data-stu-id="b34f4-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b34f4-104">方法</span><span class="sxs-lookup"><span data-stu-id="b34f4-104">Methods</span></span>  
  
|<span data-ttu-id="b34f4-105">方法</span><span class="sxs-lookup"><span data-stu-id="b34f4-105">Method</span></span>|<span data-ttu-id="b34f4-106">描述</span><span class="sxs-lookup"><span data-stu-id="b34f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b34f4-107">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="b34f4-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="b34f4-108">設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小。</span><span class="sxs-lookup"><span data-stu-id="b34f4-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="b34f4-109">可讓層代 0 和區段大小大於`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="b34f4-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b34f4-110">備註</span><span class="sxs-lookup"><span data-stu-id="b34f4-110">Remarks</span></span>  
 <span data-ttu-id="b34f4-111">此介面繼承自[ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="b34f4-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="b34f4-112">Common language runtime (CLR) 會實作與受管理的記憶體回收機制<xref:System.GC>型別。</span><span class="sxs-lookup"><span data-stu-id="b34f4-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="b34f4-113">如需記憶體回收系統的詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b34f4-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b34f4-114">需求</span><span class="sxs-lookup"><span data-stu-id="b34f4-114">Requirements</span></span>  
 <span data-ttu-id="b34f4-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b34f4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b34f4-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b34f4-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b34f4-117">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b34f4-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b34f4-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b34f4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b34f4-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="b34f4-119">See Also</span></span>  
 [<span data-ttu-id="b34f4-120">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="b34f4-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="b34f4-121">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="b34f4-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="b34f4-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b34f4-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b34f4-123">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="b34f4-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="b34f4-124">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b34f4-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b34f4-125">裝載</span><span class="sxs-lookup"><span data-stu-id="b34f4-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
