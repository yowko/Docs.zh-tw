---
title: "ICLRGCManager 介面"
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
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6cc6c84d57e4114a28a8b363b99b98f3c4d21410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="4b0c7-102">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="4b0c7-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="4b0c7-103">提供方法，讓主應用程式與 common language runtime 的記憶體回收系統互動。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b0c7-104">從開始[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以使用[iclrgcmanager2:: Setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小為的值大於比`DWORD`所加諸的限制[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b0c7-105">方法</span><span class="sxs-lookup"><span data-stu-id="4b0c7-105">Methods</span></span>  
  
|<span data-ttu-id="4b0c7-106">方法</span><span class="sxs-lookup"><span data-stu-id="4b0c7-106">Method</span></span>|<span data-ttu-id="4b0c7-107">描述</span><span class="sxs-lookup"><span data-stu-id="4b0c7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b0c7-108">Collect 方法</span><span class="sxs-lookup"><span data-stu-id="4b0c7-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="4b0c7-109">強制執行指定的層代的回收。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="4b0c7-110">GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="4b0c7-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="4b0c7-111">取得一組有關記憶體回收系統目前的統計資料。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="4b0c7-112">SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="4b0c7-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="4b0c7-113">設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b0c7-114">備註</span><span class="sxs-lookup"><span data-stu-id="4b0c7-114">Remarks</span></span>  
 <span data-ttu-id="4b0c7-115">Common language runtime (CLR) 會實作與受管理的記憶體回收機制<xref:System.GC>型別。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="4b0c7-116">如需記憶體回收系統的詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b0c7-117">需求</span><span class="sxs-lookup"><span data-stu-id="4b0c7-117">Requirements</span></span>  
 <span data-ttu-id="4b0c7-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b0c7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b0c7-119">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b0c7-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b0c7-120">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4b0c7-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b0c7-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b0c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0c7-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b0c7-122">See Also</span></span>  
 [<span data-ttu-id="4b0c7-123">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="4b0c7-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="4b0c7-124">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="4b0c7-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="4b0c7-125">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="4b0c7-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="4b0c7-126">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="4b0c7-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="4b0c7-127">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4b0c7-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="4b0c7-128">裝載</span><span class="sxs-lookup"><span data-stu-id="4b0c7-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
