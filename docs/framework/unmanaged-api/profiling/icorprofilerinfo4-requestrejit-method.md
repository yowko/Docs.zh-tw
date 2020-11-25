---
title: ICorProfilerInfo4::RequestReJIT 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: 92e2901b2c228e4b774fbb1dbcc66cd0b4f82087
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733850"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="c24a6-102">ICorProfilerInfo4::RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="c24a6-102">ICorProfilerInfo4::RequestReJIT Method</span></span>

<span data-ttu-id="c24a6-103">要求指定函式的所有執行個體進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="c24a6-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c24a6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c24a6-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c24a6-105">參數</span><span class="sxs-lookup"><span data-stu-id="c24a6-105">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="c24a6-106">[in] 要重新編譯的函式數目。</span><span class="sxs-lookup"><span data-stu-id="c24a6-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="c24a6-107">[in] 指定 (`module`, `methodDef`) 組的 `moduleId` 部分，這個部分可識別所要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="c24a6-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="c24a6-108">[in] 指定 (`module`, `methodDef`) 組的 `methodId` 部分，這個部分可識別所要重新編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="c24a6-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c24a6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c24a6-109">Return Value</span></span>  

 <span data-ttu-id="c24a6-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c24a6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c24a6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c24a6-111">HRESULT</span></span>|<span data-ttu-id="c24a6-112">描述</span><span class="sxs-lookup"><span data-stu-id="c24a6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c24a6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c24a6-113">S_OK</span></span>|<span data-ttu-id="c24a6-114">已嘗試將所有方法標示為要進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="c24a6-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="c24a6-115">分析工具必須執行 [ICorProfilerCallback4：： ReJITError](icorprofilercallback4-rejiterror-method.md) 方法，以判斷哪些方法已成功標示為 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="c24a6-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="c24a6-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="c24a6-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="c24a6-117">分析工具必須執行 [ICorProfilerCallback4](icorprofilercallback4-interface.md) 介面，才能支援此呼叫。</span><span class="sxs-lookup"><span data-stu-id="c24a6-117">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="c24a6-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="c24a6-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="c24a6-119">尚未啟用 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="c24a6-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="c24a6-120">您必須在初始化期間啟用 JIT 重新編譯，方法是使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md) 方法來設定 `COR_PRF_ENABLE_REJIT` 旗標。</span><span class="sxs-lookup"><span data-stu-id="c24a6-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="c24a6-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c24a6-121">E_INVALIDARG</span></span>|<span data-ttu-id="c24a6-122">`cFunctions` 為 0，或者 `moduleIds` 或 `methodIds` 為 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="c24a6-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="c24a6-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c24a6-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c24a6-124">CLR 無法完成要求，因為記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="c24a6-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c24a6-125">備註</span><span class="sxs-lookup"><span data-stu-id="c24a6-125">Remarks</span></span>  

 <span data-ttu-id="c24a6-126">呼叫 `RequestReJIT`，讓執行階段重新編譯所指定的一組函式。</span><span class="sxs-lookup"><span data-stu-id="c24a6-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="c24a6-127">然後，程式碼分析工具可以使用 [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) 介面來調整重新編譯函式時所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c24a6-127">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="c24a6-128">這不會影響目前正在執行的函式，只會影響未來的函式叫用。</span><span class="sxs-lookup"><span data-stu-id="c24a6-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="c24a6-129">如果所指定的任何函式先前已進行過 JIT 重新編譯，要求重新編譯就等於還原並重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="c24a6-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="c24a6-130">為了保留可反轉性，當 JIT 編譯器編譯函式的原始版本時，只會考慮其被呼叫端的原始版本來進行內嵌決策。</span><span class="sxs-lookup"><span data-stu-id="c24a6-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="c24a6-131">當 JIT 編譯器重新編譯函式時，它會考慮其被呼叫端的目前版本 (已重新編譯或原始) 來進行內嵌。</span><span class="sxs-lookup"><span data-stu-id="c24a6-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="c24a6-132">分析工具通常會呼叫 `RequestReJIT`，以回應要求分析工具檢測一或多個方法的使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="c24a6-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="c24a6-133">`RequestReJIT` 通常會暫停執行階段，以執行某些工作，而且可能會觸發記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="c24a6-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="c24a6-134">因此，分析工具應該從其先前建立的執行緒來呼叫 `RequestReJIT`，而不是從目前正在執行分析工具回呼的 CLR 建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c24a6-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c24a6-135">需求</span><span class="sxs-lookup"><span data-stu-id="c24a6-135">Requirements</span></span>  

 <span data-ttu-id="c24a6-136">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c24a6-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c24a6-137">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c24a6-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c24a6-138">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c24a6-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c24a6-139">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c24a6-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c24a6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c24a6-140">See also</span></span>

- [<span data-ttu-id="c24a6-141">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="c24a6-141">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="c24a6-142">分析介面</span><span class="sxs-lookup"><span data-stu-id="c24a6-142">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c24a6-143">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="c24a6-143">Profiling</span></span>](index.md)
