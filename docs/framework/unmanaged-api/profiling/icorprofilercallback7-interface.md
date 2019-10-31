---
title: ICorProfilerCallback7 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: f8c2fb544cf9fd6642bd0581211e0e4e49633221
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139768"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="e00d2-102">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="e00d2-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="e00d2-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="e00d2-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="e00d2-104">[ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) 子類別提供一種回呼方法，以讓 Common Language Runtime 用來通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="e00d2-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e00d2-105">方法</span><span class="sxs-lookup"><span data-stu-id="e00d2-105">Methods</span></span>  
  
|<span data-ttu-id="e00d2-106">方法</span><span class="sxs-lookup"><span data-stu-id="e00d2-106">Method</span></span>|<span data-ttu-id="e00d2-107">描述</span><span class="sxs-lookup"><span data-stu-id="e00d2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e00d2-108">ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="e00d2-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="e00d2-109">通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="e00d2-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e00d2-110">需求</span><span class="sxs-lookup"><span data-stu-id="e00d2-110">Requirements</span></span>  
 <span data-ttu-id="e00d2-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e00d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e00d2-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e00d2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e00d2-113">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e00d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e00d2-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e00d2-114">See also</span></span>

- [<span data-ttu-id="e00d2-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="e00d2-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
