---
title: "ICorProfilerCallback4::ReJITCompilationFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1aab8fd836da5238fa939b4d20d019f7bd581213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="f18df-102">ICorProfilerCallback4::ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="f18df-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="f18df-103">通知分析工具，在 just-in-time (JIT) 編譯器已完成重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="f18df-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18df-104">語法</span><span class="sxs-lookup"><span data-stu-id="f18df-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f18df-105">參數</span><span class="sxs-lookup"><span data-stu-id="f18df-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f18df-106">[in]重新編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f18df-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="f18df-107">[in] 經過 JIT 重新編譯的函式識別。</span><span class="sxs-lookup"><span data-stu-id="f18df-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f18df-108">[in]值，指出是否已成功 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="f18df-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="f18df-109">[in]`true`表示封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候`false`表示封鎖將不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="f18df-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="f18df-110">值為`true`不傷害執行階段，但可能會影響分析的結果。</span><span class="sxs-lookup"><span data-stu-id="f18df-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f18df-111">需求</span><span class="sxs-lookup"><span data-stu-id="f18df-111">Requirements</span></span>  
 <span data-ttu-id="f18df-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f18df-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f18df-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f18df-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f18df-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f18df-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f18df-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f18df-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18df-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f18df-116">See Also</span></span>  
 [<span data-ttu-id="f18df-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f18df-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f18df-118">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="f18df-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="f18df-119">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f18df-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="f18df-120">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f18df-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
