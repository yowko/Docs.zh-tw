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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a89a7ef34418163d790fd055de681c1cdf989e57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226907"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="99c28-102">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="99c28-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="99c28-103">提供方法，可讓主應用程式與 common language runtime 的記憶體回收系統互動。</span><span class="sxs-lookup"><span data-stu-id="99c28-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99c28-104">方法</span><span class="sxs-lookup"><span data-stu-id="99c28-104">Methods</span></span>  
  
|<span data-ttu-id="99c28-105">方法</span><span class="sxs-lookup"><span data-stu-id="99c28-105">Method</span></span>|<span data-ttu-id="99c28-106">描述</span><span class="sxs-lookup"><span data-stu-id="99c28-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99c28-107">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="99c28-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="99c28-108">設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小。</span><span class="sxs-lookup"><span data-stu-id="99c28-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="99c28-109">可讓第 0 代和區段大小大於`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="99c28-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99c28-110">備註</span><span class="sxs-lookup"><span data-stu-id="99c28-110">Remarks</span></span>  
 <span data-ttu-id="99c28-111">此介面繼承自[ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="99c28-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="99c28-112">Common language runtime (CLR) 實作與 managed 其記憶體回收機制<xref:System.GC>型別。</span><span class="sxs-lookup"><span data-stu-id="99c28-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="99c28-113">如需記憶體回收系統的詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="99c28-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c28-114">需求</span><span class="sxs-lookup"><span data-stu-id="99c28-114">Requirements</span></span>  
 <span data-ttu-id="99c28-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99c28-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c28-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99c28-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99c28-117">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="99c28-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99c28-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c28-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c28-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99c28-119">See also</span></span>

- [<span data-ttu-id="99c28-120">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="99c28-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="99c28-121">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="99c28-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="99c28-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="99c28-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="99c28-123">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="99c28-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="99c28-124">裝載介面</span><span class="sxs-lookup"><span data-stu-id="99c28-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="99c28-125">裝載</span><span class="sxs-lookup"><span data-stu-id="99c28-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
