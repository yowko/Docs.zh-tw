---
title: ICLRGCManager 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9519f7c2df5cf078bac6be038275527d7741edb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152161"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="19310-102">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="19310-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="19310-103">提供方法，可讓主應用程式與 common language runtime 的記憶體回收系統互動。</span><span class="sxs-lookup"><span data-stu-id="19310-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19310-104">開頭[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以使用[ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於比`DWORD`所加諸的限制[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="19310-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19310-105">方法</span><span class="sxs-lookup"><span data-stu-id="19310-105">Methods</span></span>  
  
|<span data-ttu-id="19310-106">方法</span><span class="sxs-lookup"><span data-stu-id="19310-106">Method</span></span>|<span data-ttu-id="19310-107">描述</span><span class="sxs-lookup"><span data-stu-id="19310-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19310-108">Collect 方法</span><span class="sxs-lookup"><span data-stu-id="19310-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="19310-109">強制執行指定層代的回收。</span><span class="sxs-lookup"><span data-stu-id="19310-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="19310-110">GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="19310-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="19310-111">取得一組關於記憶體回收系統目前的統計資料。</span><span class="sxs-lookup"><span data-stu-id="19310-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="19310-112">SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="19310-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="19310-113">設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小。</span><span class="sxs-lookup"><span data-stu-id="19310-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19310-114">備註</span><span class="sxs-lookup"><span data-stu-id="19310-114">Remarks</span></span>  
 <span data-ttu-id="19310-115">Common language runtime (CLR) 實作與 managed 其記憶體回收機制<xref:System.GC>型別。</span><span class="sxs-lookup"><span data-stu-id="19310-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="19310-116">如需記憶體回收系統的詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="19310-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19310-117">需求</span><span class="sxs-lookup"><span data-stu-id="19310-117">Requirements</span></span>  
 <span data-ttu-id="19310-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19310-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19310-119">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="19310-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19310-120">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="19310-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19310-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19310-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19310-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19310-122">See also</span></span>

- [<span data-ttu-id="19310-123">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="19310-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="19310-124">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="19310-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="19310-125">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="19310-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="19310-126">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="19310-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="19310-127">裝載介面</span><span class="sxs-lookup"><span data-stu-id="19310-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="19310-128">裝載</span><span class="sxs-lookup"><span data-stu-id="19310-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
