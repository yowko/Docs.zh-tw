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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f681001b610f42fef28181ffe3b47d702aabdf6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452687"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="b54e3-102">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="b54e3-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="b54e3-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="b54e3-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="b54e3-104">[ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) 子類別提供一種回呼方法，以讓 Common Language Runtime 用來通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="b54e3-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b54e3-105">方法</span><span class="sxs-lookup"><span data-stu-id="b54e3-105">Methods</span></span>  
  
|<span data-ttu-id="b54e3-106">方法</span><span class="sxs-lookup"><span data-stu-id="b54e3-106">Method</span></span>|<span data-ttu-id="b54e3-107">描述</span><span class="sxs-lookup"><span data-stu-id="b54e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b54e3-108">ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="b54e3-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="b54e3-109">通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="b54e3-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b54e3-110">需求</span><span class="sxs-lookup"><span data-stu-id="b54e3-110">Requirements</span></span>  
 <span data-ttu-id="b54e3-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b54e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b54e3-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b54e3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b54e3-113">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b54e3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b54e3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b54e3-114">See Also</span></span>  
 [<span data-ttu-id="b54e3-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="b54e3-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
