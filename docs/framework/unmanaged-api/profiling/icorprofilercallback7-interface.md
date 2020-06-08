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
ms.openlocfilehash: 9a49d8e1ff31942c6564ab560d6726b9ede26466
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499138"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="ce0e8-102">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="ce0e8-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="ce0e8-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="ce0e8-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="ce0e8-104">[ICorProfilerCallback6](icorprofilercallback6-interface.md) 子類別提供一種回呼方法，以讓 Common Language Runtime 用來通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="ce0e8-104">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce0e8-105">方法</span><span class="sxs-lookup"><span data-stu-id="ce0e8-105">Methods</span></span>  
  
|<span data-ttu-id="ce0e8-106">方法</span><span class="sxs-lookup"><span data-stu-id="ce0e8-106">Method</span></span>|<span data-ttu-id="ce0e8-107">描述</span><span class="sxs-lookup"><span data-stu-id="ce0e8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce0e8-108">ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="ce0e8-108">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="ce0e8-109">通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="ce0e8-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce0e8-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="ce0e8-110">Requirements</span></span>  
 <span data-ttu-id="ce0e8-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce0e8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce0e8-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce0e8-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce0e8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce0e8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0e8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce0e8-114">See also</span></span>

- [<span data-ttu-id="ce0e8-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="ce0e8-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
