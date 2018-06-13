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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455279"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="f543f-102">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="f543f-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="f543f-103">[在.NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="f543f-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="f543f-104">子類別[ICorProfilerCallback7](icorprofilercallback7-interface.md)提供 common language runtime 用於通知的動態方法的 JIT 編譯已啟動及完成的分析工具回呼方法。</span><span class="sxs-lookup"><span data-stu-id="f543f-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="f543f-105">方法</span><span class="sxs-lookup"><span data-stu-id="f543f-105">Methods</span></span>  
  
|<span data-ttu-id="f543f-106">方法</span><span class="sxs-lookup"><span data-stu-id="f543f-106">Method</span></span>|<span data-ttu-id="f543f-107">描述</span><span class="sxs-lookup"><span data-stu-id="f543f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f543f-108">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f543f-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="f543f-109">通知分析工具的動態方法的 JIT 編譯已啟動。</span><span class="sxs-lookup"><span data-stu-id="f543f-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="f543f-110">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="f543f-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="f543f-111">通知分析工具已完成的動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="f543f-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f543f-112">需求</span><span class="sxs-lookup"><span data-stu-id="f543f-112">Requirements</span></span>  
 <span data-ttu-id="f543f-113">**平台：** 看到[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f543f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f543f-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f543f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="f543f-115">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f543f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f543f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f543f-116">See Also</span></span>  
<span data-ttu-id="f543f-117">[分析介面](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="f543f-117">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
[<span data-ttu-id="f543f-118">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="f543f-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
