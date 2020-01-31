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
ms.openlocfilehash: 75414ec3d2b30fe8afc5db1e97c81f34b29a3115
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864670"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="add9a-102">ICorProfilerFunctionControl::SetCodegenFlags 方法</span><span class="sxs-lookup"><span data-stu-id="add9a-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="add9a-103">設定[COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md)列舉中的一或多個旗標，以控制即時（JIT）重新編譯函式的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="add9a-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="add9a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="add9a-105">參數</span><span class="sxs-lookup"><span data-stu-id="add9a-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="add9a-106">在來自[COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md)列舉的一或多個旗標。</span><span class="sxs-lookup"><span data-stu-id="add9a-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="add9a-107">備註</span><span class="sxs-lookup"><span data-stu-id="add9a-107">Remarks</span></span>  
 <span data-ttu-id="add9a-108">分析工具會透過[ICorProfilerCallback4：： GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md)回呼來取得此介面的實例。</span><span class="sxs-lookup"><span data-stu-id="add9a-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="add9a-109">`SetCodegenFlags` 可讓 profiler 控制重新編譯函式的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="add9a-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="add9a-110">如同所有其他 JIT 重新編譯參數，程式碼產生旗標適用于函式的所有實例。</span><span class="sxs-lookup"><span data-stu-id="add9a-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="add9a-111">在編譯函式時，JIT 編譯程式會考慮這些編譯旗標以及其他來源所指定的其他旗標。</span><span class="sxs-lookup"><span data-stu-id="add9a-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="add9a-112">其他來源包括偵錯工具、在啟動時使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法（加上值 `COR_PRF_DISABLE_INLINING` 和 `COR_PRF_DISABLE_OPTIMIZATIONS`）和分析工具的[ICorProfilerCallback：： JITInlining](icorprofilercallback-jitinlining-method.md)回呼所設定的全域旗標。</span><span class="sxs-lookup"><span data-stu-id="add9a-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="add9a-113">JIT 編譯程式會優先于要求最少量優化的來源。</span><span class="sxs-lookup"><span data-stu-id="add9a-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="add9a-114">例如，如果分析工具在啟動時指定 `COR_PRF_DISABLE_INLINING`，但未在[ICorProfilerFunctionControl：： SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)回呼中指定 `COR_PRF_CODEGEN_DISABLE_INLINING`，則仍會停用內嵌功能。</span><span class="sxs-lookup"><span data-stu-id="add9a-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="add9a-115">同樣地，如果分析工具未在 `SetCodegenFlags`中指定 `COR_PRF_CODEGEN_DISABLE_INLINING`，然後使用[ICorProfilerCallback：： JITInlining](icorprofilercallback-jitinlining-method.md)回呼來停用內嵌，則會停用內嵌功能。</span><span class="sxs-lookup"><span data-stu-id="add9a-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="add9a-116">需求</span><span class="sxs-lookup"><span data-stu-id="add9a-116">Requirements</span></span>  
 <span data-ttu-id="add9a-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="add9a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="add9a-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="add9a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="add9a-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="add9a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="add9a-120">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add9a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add9a-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="add9a-121">See also</span></span>

- [<span data-ttu-id="add9a-122">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="add9a-122">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
