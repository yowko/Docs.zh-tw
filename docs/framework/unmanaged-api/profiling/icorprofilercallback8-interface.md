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
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125563"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="37cc8-102">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="37cc8-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="37cc8-103">[.NET Framework 4.7 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="37cc8-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="37cc8-104">子類別[ICorProfilerCallback7](icorprofilercallback7-interface.md)提供 common language runtime 用來通知分析工具中的動態方法的 JIT 編譯已啟動並完成的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="37cc8-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="37cc8-105">方法</span><span class="sxs-lookup"><span data-stu-id="37cc8-105">Methods</span></span>  
  
|<span data-ttu-id="37cc8-106">方法</span><span class="sxs-lookup"><span data-stu-id="37cc8-106">Method</span></span>|<span data-ttu-id="37cc8-107">描述</span><span class="sxs-lookup"><span data-stu-id="37cc8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37cc8-108">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="37cc8-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="37cc8-109">通知分析工具已啟動的動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="37cc8-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="37cc8-110">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="37cc8-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="37cc8-111">通知分析工具已完成的動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="37cc8-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37cc8-112">需求</span><span class="sxs-lookup"><span data-stu-id="37cc8-112">Requirements</span></span>  
 <span data-ttu-id="37cc8-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37cc8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37cc8-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="37cc8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
**<span data-ttu-id="37cc8-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="37cc8-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="37cc8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37cc8-116">See also</span></span>

- [<span data-ttu-id="37cc8-117">分析介面</span><span class="sxs-lookup"><span data-stu-id="37cc8-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="37cc8-118">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="37cc8-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
