---
title: ICorProfilerCallback4 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 1b85c48859ac29738347d112dd0466a76bfdfd2c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865333"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="6f019-102">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="6f019-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="6f019-103">提供通用語言執行時間（CLR）用來將資訊傳達給分析工具的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="6f019-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f019-104">方法</span><span class="sxs-lookup"><span data-stu-id="6f019-104">Methods</span></span>  
  
|<span data-ttu-id="6f019-105">方法</span><span class="sxs-lookup"><span data-stu-id="6f019-105">Method</span></span>|<span data-ttu-id="6f019-106">描述</span><span class="sxs-lookup"><span data-stu-id="6f019-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f019-107">GetReJITParameters 方法</span><span class="sxs-lookup"><span data-stu-id="6f019-107">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="6f019-108">可讓程式碼分析工具針對新重新編譯的方法主體，設定替代的程式碼產生旗標。</span><span class="sxs-lookup"><span data-stu-id="6f019-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="6f019-109">MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="6f019-109">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="6f019-110">報告壓縮垃圾收集造成的堆積中物件的新版面配置。</span><span class="sxs-lookup"><span data-stu-id="6f019-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="6f019-111">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="6f019-111">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="6f019-112">通知分析工具，及時（JIT）編譯器已完成函數的重新編譯。</span><span class="sxs-lookup"><span data-stu-id="6f019-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="6f019-113">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="6f019-113">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="6f019-114">通知 profiler，及時（JIT）編譯器已開始重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="6f019-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="6f019-115">ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="6f019-115">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="6f019-116">回報處理重新編譯要求時所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f019-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="6f019-117">SurvivingReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="6f019-117">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="6f019-118">報告非壓縮記憶體回收造成的堆積中物件配置。</span><span class="sxs-lookup"><span data-stu-id="6f019-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f019-119">備註</span><span class="sxs-lookup"><span data-stu-id="6f019-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f019-120">需求</span><span class="sxs-lookup"><span data-stu-id="6f019-120">Requirements</span></span>  
 <span data-ttu-id="6f019-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f019-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f019-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f019-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f019-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f019-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f019-124">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f019-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f019-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f019-125">See also</span></span>

- [<span data-ttu-id="6f019-126">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="6f019-126">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="6f019-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="6f019-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6f019-128">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6f019-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
