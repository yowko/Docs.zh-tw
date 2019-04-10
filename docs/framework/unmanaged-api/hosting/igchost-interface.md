---
title: IGCHost 介面
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3202aa25261863dae953e3edac36f3406fa001d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228168"
---
# <a name="igchost-interface"></a><span data-ttu-id="4f109-102">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="4f109-102">IGCHost Interface</span></span>
<span data-ttu-id="4f109-103">提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。</span><span class="sxs-lookup"><span data-stu-id="4f109-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f109-104">開頭[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以使用[IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於`DWORD`所加諸的限制[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4f109-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f109-105">這個介面是僅供專家使用。</span><span class="sxs-lookup"><span data-stu-id="4f109-105">This interface is for expert usage only.</span></span> <span data-ttu-id="4f109-106">如果不當使用，它可能會影響應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="4f109-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f109-107">方法</span><span class="sxs-lookup"><span data-stu-id="4f109-107">Methods</span></span>  
  
|<span data-ttu-id="4f109-108">方法</span><span class="sxs-lookup"><span data-stu-id="4f109-108">Method</span></span>|<span data-ttu-id="4f109-109">描述</span><span class="sxs-lookup"><span data-stu-id="4f109-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f109-110">Collect 方法</span><span class="sxs-lookup"><span data-stu-id="4f109-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="4f109-111">強制發生指定的層代，不論目前的記憶體回收集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="4f109-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="4f109-112">GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="4f109-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="4f109-113">取得記憶體回收系統的目前狀態的統計資料。</span><span class="sxs-lookup"><span data-stu-id="4f109-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="4f109-114">GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="4f109-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="4f109-115">取得每個執行緒統計資料進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4f109-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="4f109-116">SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="4f109-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="4f109-117">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="4f109-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="4f109-118">SetVirtualMemLimit 方法</span><span class="sxs-lookup"><span data-stu-id="4f109-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="4f109-119">設定執行階段的虛擬記憶體的大小上限。</span><span class="sxs-lookup"><span data-stu-id="4f109-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f109-120">需求</span><span class="sxs-lookup"><span data-stu-id="4f109-120">Requirements</span></span>  
 <span data-ttu-id="4f109-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f109-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f109-122">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="4f109-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="4f109-123">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4f109-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4f109-124">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4f109-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4f109-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f109-125">See also</span></span>

- [<span data-ttu-id="4f109-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4f109-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4f109-127">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="4f109-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
