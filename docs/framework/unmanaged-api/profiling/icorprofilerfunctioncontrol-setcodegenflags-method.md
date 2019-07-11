---
title: ICorProfilerFunctionControl::SetCodegenFlags 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4103925462732fa8ddc509a9538ef5b485266a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780365"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="e10ac-102">ICorProfilerFunctionControl::SetCodegenFlags 方法</span><span class="sxs-lookup"><span data-stu-id="e10ac-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="e10ac-103">設定從一或多個旗標[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉來控制產生程式碼在 just-in-time (JIT) 編譯函式。</span><span class="sxs-lookup"><span data-stu-id="e10ac-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e10ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="e10ac-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e10ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="e10ac-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="e10ac-106">[in]從一或多個旗標[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="e10ac-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e10ac-107">備註</span><span class="sxs-lookup"><span data-stu-id="e10ac-107">Remarks</span></span>  
 <span data-ttu-id="e10ac-108">分析工具取得透過這個介面的執行個體[ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="e10ac-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="e10ac-109">`SetCodegenFlags` 可讓分析工具，來控制重新編譯的函式的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="e10ac-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="e10ac-110">如同其他所有的 JIT 重新編譯參數，程式碼產生旗標適用於函式的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="e10ac-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="e10ac-111">JIT 編譯器會考慮這些編譯旗標，以及編譯函式時，由其他來源中，指定其他旗標。</span><span class="sxs-lookup"><span data-stu-id="e10ac-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="e10ac-112">其他來源包括偵錯工具、 全域旗標設定在所啟動的分析工具使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法 (具有值`COR_PRF_DISABLE_INLINING`並`COR_PRF_DISABLE_OPTIMIZATIONS`)，和分析工具的[Icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="e10ac-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="e10ac-113">JIT 編譯器會提供要求最少的最佳化來源的優先順序。</span><span class="sxs-lookup"><span data-stu-id="e10ac-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="e10ac-114">例如，如果指定的程式碼剖析工具`COR_PRF_DISABLE_INLINING`在啟動時，但未指定`COR_PRF_CODEGEN_DISABLE_INLINING`中[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)回呼中，內嵌仍然停用。</span><span class="sxs-lookup"><span data-stu-id="e10ac-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="e10ac-115">同樣地，如果未指定分析工具`COR_PRF_CODEGEN_DISABLE_INLINING`中`SetCodegenFlags`，然後停用內嵌使用，但[icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼中，內嵌已停用。</span><span class="sxs-lookup"><span data-stu-id="e10ac-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e10ac-116">需求</span><span class="sxs-lookup"><span data-stu-id="e10ac-116">Requirements</span></span>  
 <span data-ttu-id="e10ac-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e10ac-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e10ac-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e10ac-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e10ac-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e10ac-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e10ac-120">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e10ac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e10ac-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e10ac-121">See also</span></span>

- [<span data-ttu-id="e10ac-122">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="e10ac-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
