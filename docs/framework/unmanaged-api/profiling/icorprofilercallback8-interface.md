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
ms.openlocfilehash: 22a133d02bb69026190428905379323362943d40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732381"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="20a46-102">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="20a46-102">ICorProfilerCallback8 Interface</span></span>

<span data-ttu-id="20a46-103">[在 .NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="20a46-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="20a46-104">[ICorProfilerCallback7](icorprofilercallback7-interface.md)的子類別，提供 common language runtime 用來通知分析工具已啟動和完成 JIT 編譯動態方法的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="20a46-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="20a46-105">方法</span><span class="sxs-lookup"><span data-stu-id="20a46-105">Methods</span></span>  
  
|<span data-ttu-id="20a46-106">方法</span><span class="sxs-lookup"><span data-stu-id="20a46-106">Method</span></span>|<span data-ttu-id="20a46-107">描述</span><span class="sxs-lookup"><span data-stu-id="20a46-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20a46-108">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="20a46-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="20a46-109">通知分析工具已啟動動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="20a46-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="20a46-110">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="20a46-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="20a46-111">通知分析工具已完成動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="20a46-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20a46-112">需求</span><span class="sxs-lookup"><span data-stu-id="20a46-112">Requirements</span></span>  

 <span data-ttu-id="20a46-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20a46-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a46-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20a46-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="20a46-115">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="20a46-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="20a46-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20a46-116">See also</span></span>

- [<span data-ttu-id="20a46-117">分析介面</span><span class="sxs-lookup"><span data-stu-id="20a46-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="20a46-118">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="20a46-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
