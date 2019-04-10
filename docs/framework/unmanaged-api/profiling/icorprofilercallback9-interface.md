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
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227752"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="b90ca-102">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="b90ca-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="b90ca-103">[.NET Framework 4.7.2 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="b90ca-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="b90ca-104">子類別[ICorProfilerCallback8](icorprofilercallback8-interface.md)提供一種回呼方法，common language runtime 用來通知分析工具的動態方法已被記憶體回收，並接著卸載。</span><span class="sxs-lookup"><span data-stu-id="b90ca-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b90ca-105">方法</span><span class="sxs-lookup"><span data-stu-id="b90ca-105">Methods</span></span>  
  
|<span data-ttu-id="b90ca-106">方法</span><span class="sxs-lookup"><span data-stu-id="b90ca-106">Method</span></span>|<span data-ttu-id="b90ca-107">描述</span><span class="sxs-lookup"><span data-stu-id="b90ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b90ca-108">DynamicMethodUnloaded 方法</span><span class="sxs-lookup"><span data-stu-id="b90ca-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="b90ca-109">通知的動態方法已被記憶體回收，並接著卸載分析工具。</span><span class="sxs-lookup"><span data-stu-id="b90ca-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b90ca-110">需求</span><span class="sxs-lookup"><span data-stu-id="b90ca-110">Requirements</span></span>  
 <span data-ttu-id="b90ca-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b90ca-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b90ca-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b90ca-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
**<span data-ttu-id="b90ca-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b90ca-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a><span data-ttu-id="b90ca-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b90ca-114">See also</span></span>

- [<span data-ttu-id="b90ca-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="b90ca-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b90ca-116">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="b90ca-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="b90ca-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="b90ca-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="b90ca-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="b90ca-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
