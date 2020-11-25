---
title: ICorProfilerCallback9 介面
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 23b91a2a58c6e76b31b94e0fa3661dfbc8e18e33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712764"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="30140-102">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="30140-102">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="30140-103">[在 .NET Framework 4.7.2 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="30140-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="30140-104">[ICorProfilerCallback8](icorprofilercallback8-interface.md)的子類別，可提供 common language runtime 所使用的回呼方法，以通知分析工具，動態方法已進行垃圾收集並隨後卸載。</span><span class="sxs-lookup"><span data-stu-id="30140-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30140-105">方法</span><span class="sxs-lookup"><span data-stu-id="30140-105">Methods</span></span>  
  
|<span data-ttu-id="30140-106">方法</span><span class="sxs-lookup"><span data-stu-id="30140-106">Method</span></span>|<span data-ttu-id="30140-107">描述</span><span class="sxs-lookup"><span data-stu-id="30140-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30140-108">DynamicMethodUnloaded 方法</span><span class="sxs-lookup"><span data-stu-id="30140-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="30140-109">通知分析工具，動態方法已進行垃圾收集，並隨後卸載。</span><span class="sxs-lookup"><span data-stu-id="30140-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30140-110">需求</span><span class="sxs-lookup"><span data-stu-id="30140-110">Requirements</span></span>  

 <span data-ttu-id="30140-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30140-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30140-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30140-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="30140-113">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="30140-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="30140-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30140-114">See also</span></span>

- [<span data-ttu-id="30140-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="30140-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="30140-116">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="30140-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="30140-117">ICorProfilerCallback8. DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="30140-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="30140-118">ICorProfilerCallback8. DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="30140-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
