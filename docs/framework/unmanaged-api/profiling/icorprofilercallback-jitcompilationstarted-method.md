---
title: "ICorProfilerCallback::JITCompilationStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a25f452ccb121ef7ebcae05048eb7116b4ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="9ed31-102">ICorProfilerCallback::JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="9ed31-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="9ed31-103">通知分析工具在 just-in-time (JIT) 編譯器已開始編譯函式。</span><span class="sxs-lookup"><span data-stu-id="9ed31-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed31-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ed31-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ed31-105">參數</span><span class="sxs-lookup"><span data-stu-id="9ed31-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9ed31-106">[in]編譯正在啟動的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ed31-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="9ed31-107">[in]值，指出程式碼剖析工具來封鎖是否會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="9ed31-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="9ed31-108">值是`true`如果封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候否則`false`。</span><span class="sxs-lookup"><span data-stu-id="9ed31-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="9ed31-109">雖然值`true`將不會危害到執行階段，則會扭曲分析的結果。</span><span class="sxs-lookup"><span data-stu-id="9ed31-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ed31-110">備註</span><span class="sxs-lookup"><span data-stu-id="9ed31-110">Remarks</span></span>  
 <span data-ttu-id="9ed31-111">很可能會收到一對以上的`JITCompilationStarted`和[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)呼叫每個函式因為執行階段控制代碼類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="9ed31-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="9ed31-112">比方說，執行階段開始 JIT 編譯方法，但類別 B 的類別建構函式必須在執行。</span><span class="sxs-lookup"><span data-stu-id="9ed31-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="9ed31-113">因此，執行階段 JIT 編譯類別 B 的建構函式，並執行它。</span><span class="sxs-lookup"><span data-stu-id="9ed31-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="9ed31-114">建構函式執行時，會呼叫方法 A，這會導致方法 A JIT 編譯一次。</span><span class="sxs-lookup"><span data-stu-id="9ed31-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="9ed31-115">在此案例中，就會中止方法 A 的第一次的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="9ed31-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="9ed31-116">不過，這兩個 JIT 編譯方法的嘗試都會回報與 JIT 編譯事件。</span><span class="sxs-lookup"><span data-stu-id="9ed31-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="9ed31-117">如果要藉由呼叫取代方法的 Microsoft intermediate language (MSIL) 程式碼分析工具[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法，它必須同時執行`JITCompilationStarted`事件，但它可能會使用相同的 MSIL 區塊兩者。</span><span class="sxs-lookup"><span data-stu-id="9ed31-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="9ed31-118">程式碼剖析工具必須在其中兩個執行緒同時進行回呼的情況下支援 JIT 回呼的序列。</span><span class="sxs-lookup"><span data-stu-id="9ed31-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="9ed31-119">例如，執行緒的呼叫`JITCompilationStarted`。</span><span class="sxs-lookup"><span data-stu-id="9ed31-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="9ed31-120">不過，執行緒的呼叫之前`JITCompilationFinished`，執行緒 B 呼叫[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)函式識別碼從執行緒 A 的`JITCompilationStarted`回呼。</span><span class="sxs-lookup"><span data-stu-id="9ed31-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="9ed31-121">它可能會顯示該函式 ID 尚未有效期不應因為呼叫`JITCompilationFinished`有尚未收到分析工具。</span><span class="sxs-lookup"><span data-stu-id="9ed31-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="9ed31-122">不過，在這類情況下，函式識別碼無效。</span><span class="sxs-lookup"><span data-stu-id="9ed31-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed31-123">需求</span><span class="sxs-lookup"><span data-stu-id="9ed31-123">Requirements</span></span>  
 <span data-ttu-id="9ed31-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed31-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed31-125">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ed31-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ed31-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ed31-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed31-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed31-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed31-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="9ed31-128">See Also</span></span>  
 [<span data-ttu-id="9ed31-129">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9ed31-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9ed31-130">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="9ed31-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
