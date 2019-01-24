---
title: ICorProfilerCallback8 Interface
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
ms.openlocfilehash: a3bdf79582619777a22c80caac5b4e90d603f3a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675011"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="60ec9-102">ICorProfilerCallback8 Interface</span><span class="sxs-lookup"><span data-stu-id="60ec9-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="60ec9-103">[.NET Framework 4.7 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="60ec9-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="60ec9-104">子類別[ICorProfilerCallback7](icorprofilercallback7-interface.md)提供 common language runtime 用來通知分析工具中的動態方法的 JIT 編譯已啟動並完成的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="60ec9-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="60ec9-105">方法</span><span class="sxs-lookup"><span data-stu-id="60ec9-105">Methods</span></span>  
  
|<span data-ttu-id="60ec9-106">方法</span><span class="sxs-lookup"><span data-stu-id="60ec9-106">Method</span></span>|<span data-ttu-id="60ec9-107">描述</span><span class="sxs-lookup"><span data-stu-id="60ec9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60ec9-108">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="60ec9-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="60ec9-109">通知分析工具已啟動的動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="60ec9-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="60ec9-110">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="60ec9-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="60ec9-111">通知分析工具已完成的動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="60ec9-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60ec9-112">需求</span><span class="sxs-lookup"><span data-stu-id="60ec9-112">Requirements</span></span>  
 <span data-ttu-id="60ec9-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60ec9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ec9-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60ec9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="60ec9-115">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60ec9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="60ec9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60ec9-116">See also</span></span>
- [<span data-ttu-id="60ec9-117">分析介面</span><span class="sxs-lookup"><span data-stu-id="60ec9-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="60ec9-118">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="60ec9-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
