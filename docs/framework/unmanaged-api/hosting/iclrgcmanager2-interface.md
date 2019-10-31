---
title: ICLRGCManager2 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: 72ffd7b47795ee8e46f8fbff07559133843793e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141153"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="25959-102">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="25959-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="25959-103">提供可讓主機與 common language runtime 的垃圾收集系統互動的方法。</span><span class="sxs-lookup"><span data-stu-id="25959-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25959-104">方法</span><span class="sxs-lookup"><span data-stu-id="25959-104">Methods</span></span>  
  
|<span data-ttu-id="25959-105">方法</span><span class="sxs-lookup"><span data-stu-id="25959-105">Method</span></span>|<span data-ttu-id="25959-106">描述</span><span class="sxs-lookup"><span data-stu-id="25959-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25959-107">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="25959-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="25959-108">設定垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="25959-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="25959-109">啟用層代0和區段大小大於 `DWORD`。</span><span class="sxs-lookup"><span data-stu-id="25959-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25959-110">備註</span><span class="sxs-lookup"><span data-stu-id="25959-110">Remarks</span></span>  
 <span data-ttu-id="25959-111">此介面繼承自[ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="25959-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="25959-112">Common language runtime （CLR）會使用 managed <xref:System.GC> 類型來執行其垃圾收集機制。</span><span class="sxs-lookup"><span data-stu-id="25959-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="25959-113">如需垃圾收集系統的詳細資訊，請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="25959-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25959-114">需求</span><span class="sxs-lookup"><span data-stu-id="25959-114">Requirements</span></span>  
 <span data-ttu-id="25959-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25959-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25959-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="25959-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25959-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25959-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25959-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25959-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25959-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="25959-119">See also</span></span>

- [<span data-ttu-id="25959-120">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="25959-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="25959-121">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="25959-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="25959-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="25959-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="25959-123">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="25959-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="25959-124">裝載介面</span><span class="sxs-lookup"><span data-stu-id="25959-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="25959-125">裝載</span><span class="sxs-lookup"><span data-stu-id="25959-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
