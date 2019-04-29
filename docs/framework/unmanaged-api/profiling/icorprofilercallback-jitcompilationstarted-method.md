---
title: ICorProfilerCallback::JITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b75eebd8d9bf439a0317521a61c06ece3745be0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787916"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="d94e4-102">ICorProfilerCallback::JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="d94e4-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="d94e4-103">通知分析工具在 just-in-time (JIT) 編譯器已開始編譯函式。</span><span class="sxs-lookup"><span data-stu-id="d94e4-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d94e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="d94e4-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d94e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="d94e4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d94e4-106">[in]為其開始編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d94e4-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="d94e4-107">[in]這個值表示是否封鎖的程式碼剖析工具，將會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="d94e4-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="d94e4-108">值是`true`如果封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="d94e4-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="d94e4-109">雖然值`true`將不會危害執行階段，它可能會扭曲分析的結果。</span><span class="sxs-lookup"><span data-stu-id="d94e4-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d94e4-110">備註</span><span class="sxs-lookup"><span data-stu-id="d94e4-110">Remarks</span></span>  
 <span data-ttu-id="d94e4-111">可接收的多個配對`JITCompilationStarted`並[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)會呼叫每個函式因為執行階段控制代碼類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="d94e4-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="d94e4-112">比方說，在執行階段開始 JIT 編譯方法，但類別 B 的類別建構函式必須執行。</span><span class="sxs-lookup"><span data-stu-id="d94e4-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="d94e4-113">因此，執行階段 JIT 編譯類別 B 的建構函式，並執行它。</span><span class="sxs-lookup"><span data-stu-id="d94e4-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="d94e4-114">當建構函式執行時，會呼叫方法 A，這會導致方法一次是 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="d94e4-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="d94e4-115">在此案例中，就會中止方法的第一次 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="d94e4-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="d94e4-116">不過，這兩個 JIT 編譯方法的嘗試會報告與 JIT 編譯事件。</span><span class="sxs-lookup"><span data-stu-id="d94e4-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="d94e4-117">如果分析工具即將取代方法的 Microsoft intermediate language (MSIL) 程式碼，藉由呼叫[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法，它必須同時進行`JITCompilationStarted`事件，但它可能會使用相同的 MSIL 區塊兩者。</span><span class="sxs-lookup"><span data-stu-id="d94e4-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="d94e4-118">在其中兩個執行緒同時進行回呼的情況下，程式碼剖析工具必須支援 JIT 回呼的序列。</span><span class="sxs-lookup"><span data-stu-id="d94e4-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="d94e4-119">例如，呼叫執行緒 A `JITCompilationStarted`。</span><span class="sxs-lookup"><span data-stu-id="d94e4-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="d94e4-120">不過，在執行緒的呼叫之前`JITCompilationFinished`，執行緒 B 呼叫[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)函式識別碼從執行緒 A 的`JITCompilationStarted`回呼。</span><span class="sxs-lookup"><span data-stu-id="d94e4-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="d94e4-121">它可能會顯示該函式識別碼尚未有效期不應因為呼叫`JITCompilationFinished`有尚未收到的分析工具。</span><span class="sxs-lookup"><span data-stu-id="d94e4-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="d94e4-122">不過，在這種情況下，函式識別碼無效。</span><span class="sxs-lookup"><span data-stu-id="d94e4-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d94e4-123">需求</span><span class="sxs-lookup"><span data-stu-id="d94e4-123">Requirements</span></span>  
 <span data-ttu-id="d94e4-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d94e4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d94e4-125">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d94e4-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d94e4-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d94e4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d94e4-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d94e4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d94e4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d94e4-128">See also</span></span>

- [<span data-ttu-id="d94e4-129">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d94e4-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d94e4-130">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="d94e4-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
