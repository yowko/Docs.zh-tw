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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a96aadcec6cb3c4f4680499585bf1c950bc5ddd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525306"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="eac3d-102">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="eac3d-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="eac3d-103">提供 common language runtime (CLR) 會將資訊傳達給分析工具使用的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="eac3d-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eac3d-104">方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-104">Methods</span></span>  
  
|<span data-ttu-id="eac3d-105">方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-105">Method</span></span>|<span data-ttu-id="eac3d-106">描述</span><span class="sxs-lookup"><span data-stu-id="eac3d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eac3d-107">GetReJITParameters 方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="eac3d-108">可讓程式碼剖析工具，來設定新的重新編譯的方法主體的替代程式碼產生旗標。</span><span class="sxs-lookup"><span data-stu-id="eac3d-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="eac3d-109">MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="eac3d-110">回報新的版面配置，因為壓縮記憶體回收堆積中的物件。</span><span class="sxs-lookup"><span data-stu-id="eac3d-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="eac3d-111">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="eac3d-112">通知分析工具，在 just-in-time (JIT) 編譯器已完成的函式重新編譯。</span><span class="sxs-lookup"><span data-stu-id="eac3d-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="eac3d-113">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="eac3d-114">通知分析工具在 just-in-time (JIT) 編譯器已開始重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="eac3d-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="eac3d-115">ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="eac3d-116">報表處理的重新編譯要求時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="eac3d-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="eac3d-117">SurvivingReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="eac3d-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="eac3d-118">報告堆積中物件的配置做為非壓縮記憶體回收的結果。</span><span class="sxs-lookup"><span data-stu-id="eac3d-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eac3d-119">備註</span><span class="sxs-lookup"><span data-stu-id="eac3d-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eac3d-120">需求</span><span class="sxs-lookup"><span data-stu-id="eac3d-120">Requirements</span></span>  
 <span data-ttu-id="eac3d-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eac3d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eac3d-122">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eac3d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eac3d-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eac3d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eac3d-124">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eac3d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac3d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eac3d-125">See also</span></span>
- [<span data-ttu-id="eac3d-126">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="eac3d-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="eac3d-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="eac3d-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="eac3d-128">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="eac3d-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
