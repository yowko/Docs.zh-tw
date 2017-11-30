---
title: "ICorProfilerCallback4 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4
helpviewer_keywords: ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64a26f5dfb0ad9f06bb1b9eb31dcae36f4623c4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="36480-102">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="36480-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="36480-103">提供 common language runtime (CLR) 會將資訊傳達給分析工具使用的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="36480-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36480-104">方法</span><span class="sxs-lookup"><span data-stu-id="36480-104">Methods</span></span>  
  
|<span data-ttu-id="36480-105">方法</span><span class="sxs-lookup"><span data-stu-id="36480-105">Method</span></span>|<span data-ttu-id="36480-106">說明</span><span class="sxs-lookup"><span data-stu-id="36480-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36480-107">GetReJITParameters 方法</span><span class="sxs-lookup"><span data-stu-id="36480-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="36480-108">可讓程式碼分析工具來設定替代程式碼產生旗標，為新的重新編譯的方法主體。</span><span class="sxs-lookup"><span data-stu-id="36480-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="36480-109">MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="36480-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="36480-110">報告壓縮記憶體回收造成堆積中物件的新配置。</span><span class="sxs-lookup"><span data-stu-id="36480-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="36480-111">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="36480-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="36480-112">通知分析工具，在 just-in-time (JIT) 編譯器已完成重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="36480-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="36480-113">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="36480-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="36480-114">通知分析工具在 just-in-time (JIT) 編譯器已啟動重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="36480-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="36480-115">ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="36480-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="36480-116">報告處理重新編譯要求時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="36480-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="36480-117">SurvivingReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="36480-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="36480-118">報告堆積中物件的配置做為非壓縮記憶體回收的結果。</span><span class="sxs-lookup"><span data-stu-id="36480-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36480-119">備註</span><span class="sxs-lookup"><span data-stu-id="36480-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36480-120">需求</span><span class="sxs-lookup"><span data-stu-id="36480-120">Requirements</span></span>  
 <span data-ttu-id="36480-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36480-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36480-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36480-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36480-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36480-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36480-124">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36480-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36480-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36480-125">See Also</span></span>  
 [<span data-ttu-id="36480-126">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="36480-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="36480-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="36480-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="36480-128">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="36480-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
