---
title: ICorProfilerCallback8 介面
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136444"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="b7e16-102">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="b7e16-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="b7e16-103">[在 .NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="b7e16-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="b7e16-104">[ICorProfilerCallback7](icorprofilercallback7-interface.md)的子類別，提供通用語言執行時間使用的回呼方法，以通知分析工具已開始和完成動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="b7e16-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="b7e16-105">方法</span><span class="sxs-lookup"><span data-stu-id="b7e16-105">Methods</span></span>  
  
|<span data-ttu-id="b7e16-106">方法</span><span class="sxs-lookup"><span data-stu-id="b7e16-106">Method</span></span>|<span data-ttu-id="b7e16-107">描述</span><span class="sxs-lookup"><span data-stu-id="b7e16-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7e16-108">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="b7e16-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="b7e16-109">通知分析工具已啟動動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="b7e16-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="b7e16-110">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="b7e16-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="b7e16-111">通知分析工具已完成動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="b7e16-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7e16-112">需求</span><span class="sxs-lookup"><span data-stu-id="b7e16-112">Requirements</span></span>  
 <span data-ttu-id="b7e16-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7e16-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7e16-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7e16-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="b7e16-115">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b7e16-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b7e16-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7e16-116">See also</span></span>

- [<span data-ttu-id="b7e16-117">分析介面</span><span class="sxs-lookup"><span data-stu-id="b7e16-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b7e16-118">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="b7e16-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
