---
title: ICorProfilerCallback::JITCompilationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d2e75d357b1f56df676163744015a1a3f77c17b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530746"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="061b6-102">ICorProfilerCallback::JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="061b6-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="061b6-103">通知分析工具，在 just-in-time (JIT) 編譯器已完成編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="061b6-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="061b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="061b6-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="061b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="061b6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="061b6-106">[in]已編譯的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="061b6-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="061b6-107">[in]值，指出編譯是否成功。</span><span class="sxs-lookup"><span data-stu-id="061b6-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="061b6-108">[in]這個值表示是否封鎖的程式碼剖析工具，將會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="061b6-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="061b6-109">值是`true`如果封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="061b6-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="061b6-110">雖然值`true`將不會危害執行階段，它可能會扭曲分析的結果。</span><span class="sxs-lookup"><span data-stu-id="061b6-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="061b6-111">需求</span><span class="sxs-lookup"><span data-stu-id="061b6-111">Requirements</span></span>  
 <span data-ttu-id="061b6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="061b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="061b6-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="061b6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="061b6-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="061b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="061b6-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="061b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061b6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="061b6-116">See also</span></span>
- [<span data-ttu-id="061b6-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="061b6-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="061b6-118">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="061b6-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
