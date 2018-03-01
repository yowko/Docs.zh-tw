---
title: "ICorProfilerCallback::JITCompilationFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9bd1a163fa5e941c68c5dd8d7d3221e8a5aa3df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="360eb-102">ICorProfilerCallback::JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="360eb-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="360eb-103">通知分析工具在 just-in-time (JIT) 編譯器發出已完成函式的編譯。</span><span class="sxs-lookup"><span data-stu-id="360eb-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="360eb-104">語法</span><span class="sxs-lookup"><span data-stu-id="360eb-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="360eb-105">參數</span><span class="sxs-lookup"><span data-stu-id="360eb-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="360eb-106">[in]已編譯的函式 ID。</span><span class="sxs-lookup"><span data-stu-id="360eb-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="360eb-107">[in]值，指出是否已成功編譯。</span><span class="sxs-lookup"><span data-stu-id="360eb-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="360eb-108">[in]值，指出程式碼剖析工具來封鎖是否會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="360eb-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="360eb-109">值是`true`如果封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候否則`false`。</span><span class="sxs-lookup"><span data-stu-id="360eb-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="360eb-110">雖然值`true`將不會危害到執行階段，則會扭曲分析的結果。</span><span class="sxs-lookup"><span data-stu-id="360eb-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="360eb-111">需求</span><span class="sxs-lookup"><span data-stu-id="360eb-111">Requirements</span></span>  
 <span data-ttu-id="360eb-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="360eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="360eb-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="360eb-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="360eb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="360eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="360eb-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="360eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="360eb-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="360eb-116">See Also</span></span>  
 [<span data-ttu-id="360eb-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="360eb-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="360eb-118">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="360eb-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
