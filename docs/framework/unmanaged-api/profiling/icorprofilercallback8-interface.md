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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175092"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="f7c09-102">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="f7c09-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="f7c09-103">[在 .NET 框架 4.7 和更高版本中支援]</span><span class="sxs-lookup"><span data-stu-id="f7c09-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="f7c09-104">[ICorProfilerCallback7](icorprofilercallback7-interface.md)的子類，它提供通用語言運行時使用的回檔方法，以通知探測器動態方法的 JIT 編譯已啟動並完成。</span><span class="sxs-lookup"><span data-stu-id="f7c09-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="f7c09-105">方法</span><span class="sxs-lookup"><span data-stu-id="f7c09-105">Methods</span></span>  
  
|<span data-ttu-id="f7c09-106">方法</span><span class="sxs-lookup"><span data-stu-id="f7c09-106">Method</span></span>|<span data-ttu-id="f7c09-107">描述</span><span class="sxs-lookup"><span data-stu-id="f7c09-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7c09-108">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f7c09-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="f7c09-109">通知探測器動態方法的 JIT 編譯已啟動。</span><span class="sxs-lookup"><span data-stu-id="f7c09-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="f7c09-110">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="f7c09-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="f7c09-111">通知探測器動態方法的 JIT 編譯已完成。</span><span class="sxs-lookup"><span data-stu-id="f7c09-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7c09-112">需求</span><span class="sxs-lookup"><span data-stu-id="f7c09-112">Requirements</span></span>  
 <span data-ttu-id="f7c09-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c09-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c09-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7c09-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="f7c09-115">**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c09-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f7c09-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7c09-116">See also</span></span>

- [<span data-ttu-id="f7c09-117">分析介面</span><span class="sxs-lookup"><span data-stu-id="f7c09-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f7c09-118">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="f7c09-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
