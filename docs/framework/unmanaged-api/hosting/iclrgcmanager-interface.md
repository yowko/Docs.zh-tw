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
ms.openlocfilehash: 76d1071ddde1509f16fd786afa4c05c05224d051
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966215"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="b9cd6-102">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="b9cd6-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="b9cd6-103">提供可讓主機與 common language runtime 的垃圾收集系統互動的方法。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9cd6-104">從 .NET Framework 4.5 開始, 您可以使用[ICLRGCManager2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法, 將垃圾收集區段的大小, 以及垃圾收集系統層代0的大小上限設定為大於的`DWORD`值。 [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)方法所加諸的限制。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9cd6-105">方法</span><span class="sxs-lookup"><span data-stu-id="b9cd6-105">Methods</span></span>  
  
|<span data-ttu-id="b9cd6-106">方法</span><span class="sxs-lookup"><span data-stu-id="b9cd6-106">Method</span></span>|<span data-ttu-id="b9cd6-107">描述</span><span class="sxs-lookup"><span data-stu-id="b9cd6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9cd6-108">Collect 方法</span><span class="sxs-lookup"><span data-stu-id="b9cd6-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="b9cd6-109">強制執行指定之層代的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="b9cd6-110">GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="b9cd6-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="b9cd6-111">取得有關垃圾收集系統的一組目前統計資料。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="b9cd6-112">SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="b9cd6-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="b9cd6-113">設定垃圾收集區段的大小, 以及垃圾收集系統層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9cd6-114">備註</span><span class="sxs-lookup"><span data-stu-id="b9cd6-114">Remarks</span></span>  
 <span data-ttu-id="b9cd6-115">Common language runtime (CLR) 會使用 managed <xref:System.GC>類型來執行其垃圾收集機制。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="b9cd6-116">如需垃圾收集系統的詳細資訊, 請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9cd6-117">需求</span><span class="sxs-lookup"><span data-stu-id="b9cd6-117">Requirements</span></span>  
 <span data-ttu-id="b9cd6-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9cd6-119">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b9cd6-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9cd6-120">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b9cd6-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9cd6-121">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9cd6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9cd6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9cd6-122">See also</span></span>

- [<span data-ttu-id="b9cd6-123">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="b9cd6-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b9cd6-124">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="b9cd6-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="b9cd6-125">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b9cd6-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b9cd6-126">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="b9cd6-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="b9cd6-127">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b9cd6-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="b9cd6-128">裝載</span><span class="sxs-lookup"><span data-stu-id="b9cd6-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
