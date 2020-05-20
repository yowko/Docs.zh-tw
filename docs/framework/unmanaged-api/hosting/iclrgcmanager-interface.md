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
ms.openlocfilehash: 76a50be6da790ed7bd193c489d36e2823cdbe587
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616954"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="30918-102">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="30918-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="30918-103">提供可讓主機與 common language runtime 的垃圾收集系統互動的方法。</span><span class="sxs-lookup"><span data-stu-id="30918-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30918-104">從 .NET Framework 4.5 開始，您可以使用[ICLRGCManager2：： SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法，將垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限設定為大於 `DWORD` [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md)方法所加諸限制的值。</span><span class="sxs-lookup"><span data-stu-id="30918-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30918-105">方法</span><span class="sxs-lookup"><span data-stu-id="30918-105">Methods</span></span>  
  
|<span data-ttu-id="30918-106">方法</span><span class="sxs-lookup"><span data-stu-id="30918-106">Method</span></span>|<span data-ttu-id="30918-107">描述</span><span class="sxs-lookup"><span data-stu-id="30918-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30918-108">Collect 方法</span><span class="sxs-lookup"><span data-stu-id="30918-108">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="30918-109">強制執行指定之層代的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="30918-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="30918-110">GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="30918-110">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="30918-111">取得有關垃圾收集系統的一組目前統計資料。</span><span class="sxs-lookup"><span data-stu-id="30918-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="30918-112">SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="30918-112">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="30918-113">設定垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="30918-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30918-114">備註</span><span class="sxs-lookup"><span data-stu-id="30918-114">Remarks</span></span>  
 <span data-ttu-id="30918-115">Common language runtime （CLR）會使用 managed 類型來執行其垃圾收集機制 <xref:System.GC> 。</span><span class="sxs-lookup"><span data-stu-id="30918-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="30918-116">如需垃圾收集系統的詳細資訊，請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="30918-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30918-117">需求</span><span class="sxs-lookup"><span data-stu-id="30918-117">Requirements</span></span>  
 <span data-ttu-id="30918-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30918-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30918-119">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="30918-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30918-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="30918-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30918-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30918-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30918-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30918-122">See also</span></span>

- [<span data-ttu-id="30918-123">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="30918-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="30918-124">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="30918-124">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="30918-125">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="30918-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="30918-126">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="30918-126">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="30918-127">裝載介面</span><span class="sxs-lookup"><span data-stu-id="30918-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="30918-128">裝載</span><span class="sxs-lookup"><span data-stu-id="30918-128">Hosting</span></span>](index.md)
