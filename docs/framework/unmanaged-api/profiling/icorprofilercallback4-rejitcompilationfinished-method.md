---
title: ICorProfilerCallback4::ReJITCompilationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99eca9fc431d159dab47cd1add5f1fe126548b5a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488886"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="396a0-102">ICorProfilerCallback4::ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="396a0-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="396a0-103">通知分析工具，在 just-in-time (JIT) 編譯器已完成重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="396a0-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="396a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="396a0-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="396a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="396a0-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="396a0-106">[in]已重新編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="396a0-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="396a0-107">[in] 經過 JIT 重新編譯的函式識別。</span><span class="sxs-lookup"><span data-stu-id="396a0-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="396a0-108">[in]值，指出 JIT 重新編譯是否成功。</span><span class="sxs-lookup"><span data-stu-id="396a0-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="396a0-109">[in]`true`表示封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒`false`表示封鎖會不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="396a0-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="396a0-110">值為`true`不會損害執行階段，但可能會影響分析結果。</span><span class="sxs-lookup"><span data-stu-id="396a0-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="396a0-111">需求</span><span class="sxs-lookup"><span data-stu-id="396a0-111">Requirements</span></span>  
 <span data-ttu-id="396a0-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="396a0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="396a0-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="396a0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="396a0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="396a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="396a0-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="396a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396a0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="396a0-116">See also</span></span>
- [<span data-ttu-id="396a0-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="396a0-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="396a0-118">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="396a0-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="396a0-119">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="396a0-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="396a0-120">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="396a0-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
