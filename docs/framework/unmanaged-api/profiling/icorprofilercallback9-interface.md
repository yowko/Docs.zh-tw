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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452373"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="86a79-102">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="86a79-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="86a79-103">[在.NET Framework 4.7.2 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="86a79-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="86a79-104">子類別[ICorProfilerCallback8](icorprofilercallback8-interface.md)提供 common language runtime 用於通知的動態方法已被記憶體回收，並接著卸載分析工具回呼方法。</span><span class="sxs-lookup"><span data-stu-id="86a79-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86a79-105">方法</span><span class="sxs-lookup"><span data-stu-id="86a79-105">Methods</span></span>  
  
|<span data-ttu-id="86a79-106">方法</span><span class="sxs-lookup"><span data-stu-id="86a79-106">Method</span></span>|<span data-ttu-id="86a79-107">描述</span><span class="sxs-lookup"><span data-stu-id="86a79-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86a79-108">DynamicMethodUnloaded 方法</span><span class="sxs-lookup"><span data-stu-id="86a79-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="86a79-109">通知的動態方法已被記憶體回收，並接著卸載分析工具。</span><span class="sxs-lookup"><span data-stu-id="86a79-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86a79-110">需求</span><span class="sxs-lookup"><span data-stu-id="86a79-110">Requirements</span></span>  
 <span data-ttu-id="86a79-111">**平台：** 看到[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86a79-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a79-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86a79-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="86a79-113">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="86a79-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="86a79-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86a79-114">See Also</span></span>  
<span data-ttu-id="86a79-115">[分析介面](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="86a79-115">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
<span data-ttu-id="86a79-116">[ICorProfilerCallback8 介面](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="86a79-116">[ICorProfilerCallback8 Interface](icorprofilercallback9-interface.md) </span></span>  
<span data-ttu-id="86a79-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span><span class="sxs-lookup"><span data-stu-id="86a79-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted method](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span></span>  
[<span data-ttu-id="86a79-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="86a79-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
