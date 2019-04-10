---
title: ICorProfilerInfo3::GetFunctionLeave3Info 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d51462017287d42fd468ed0a74a2e83203a3d94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172389"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="b06f0-102">ICorProfilerInfo3::GetFunctionLeave3Info 方法</span><span class="sxs-lookup"><span data-stu-id="b06f0-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="b06f0-103">提供的堆疊框架和傳回值的函式報告給分析工具所[FunctionLeave3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="b06f0-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="b06f0-104">只能在 `FunctionLeave3WithInfo` 回呼期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="b06f0-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b06f0-105">語法</span><span class="sxs-lookup"><span data-stu-id="b06f0-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b06f0-106">參數</span><span class="sxs-lookup"><span data-stu-id="b06f0-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b06f0-107">[in]`FunctionID`函式傳回。</span><span class="sxs-lookup"><span data-stu-id="b06f0-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b06f0-108">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b06f0-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b06f0-109">分析工具應該提供相同`eltInfo`，已指定用來藉由分析工具[FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="b06f0-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="b06f0-110">[out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b06f0-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="b06f0-111">此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionLeave3Info` 方法的 `FunctionLeave3WithInfo` 回呼中有效。</span><span class="sxs-lookup"><span data-stu-id="b06f0-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="b06f0-112">[out]指標[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構，其中包含函式傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b06f0-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="b06f0-113">若要存取傳回值的詳細資訊，`COR_PRF_ENABLE_FUNCTION_RETVAL`旗標必須設定。</span><span class="sxs-lookup"><span data-stu-id="b06f0-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="b06f0-114">可以使用分析工具[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)設定的事件旗標。</span><span class="sxs-lookup"><span data-stu-id="b06f0-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b06f0-115">備註</span><span class="sxs-lookup"><span data-stu-id="b06f0-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b06f0-116">需求</span><span class="sxs-lookup"><span data-stu-id="b06f0-116">Requirements</span></span>  
 <span data-ttu-id="b06f0-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b06f0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b06f0-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b06f0-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b06f0-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b06f0-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b06f0-120">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b06f0-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b06f0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b06f0-121">See also</span></span>

- [<span data-ttu-id="b06f0-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b06f0-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="b06f0-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b06f0-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="b06f0-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b06f0-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b06f0-125">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="b06f0-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b06f0-126">分析介面</span><span class="sxs-lookup"><span data-stu-id="b06f0-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b06f0-127">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="b06f0-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
