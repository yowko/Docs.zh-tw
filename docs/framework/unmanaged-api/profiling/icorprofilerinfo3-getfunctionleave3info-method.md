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
ms.openlocfilehash: 0d3b93a293d4dda9dfe7b576708c832de2e25869
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862395"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="e7b99-102">ICorProfilerInfo3::GetFunctionLeave3Info 方法</span><span class="sxs-lookup"><span data-stu-id="e7b99-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="e7b99-103">提供[FunctionLeave3WithInfo](functionleave3withinfo-function.md)函式函式所回報給分析工具的函式之堆疊框架和傳回值。</span><span class="sxs-lookup"><span data-stu-id="e7b99-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="e7b99-104">只能在 `FunctionLeave3WithInfo` 回呼期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="e7b99-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b99-105">語法</span><span class="sxs-lookup"><span data-stu-id="e7b99-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7b99-106">參數</span><span class="sxs-lookup"><span data-stu-id="e7b99-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e7b99-107">在傳回之函數的 `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="e7b99-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="e7b99-108">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e7b99-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="e7b99-109">分析工具應該提供[FunctionLeave3WithInfo](functionleave3withinfo-function.md)函式所指定給 profiler 的相同 `eltInfo`。</span><span class="sxs-lookup"><span data-stu-id="e7b99-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="e7b99-110">[out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e7b99-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="e7b99-111">此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionLeave3Info` 方法的 `FunctionLeave3WithInfo` 回呼中有效。</span><span class="sxs-lookup"><span data-stu-id="e7b99-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="e7b99-112">脫銷[COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)結構的指標，其中包含從函數傳回的值。</span><span class="sxs-lookup"><span data-stu-id="e7b99-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="e7b99-113">若要存取傳回值資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_RETVAL` 旗標。</span><span class="sxs-lookup"><span data-stu-id="e7b99-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="e7b99-114">分析工具可以使用[ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)來設定事件旗標。</span><span class="sxs-lookup"><span data-stu-id="e7b99-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7b99-115">備註</span><span class="sxs-lookup"><span data-stu-id="e7b99-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b99-116">需求</span><span class="sxs-lookup"><span data-stu-id="e7b99-116">Requirements</span></span>  
 <span data-ttu-id="e7b99-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7b99-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b99-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7b99-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7b99-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b99-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b99-120">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b99-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b99-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="e7b99-121">See also</span></span>

- [<span data-ttu-id="e7b99-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e7b99-122">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="e7b99-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e7b99-123">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="e7b99-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e7b99-124">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="e7b99-125">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="e7b99-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e7b99-126">分析介面</span><span class="sxs-lookup"><span data-stu-id="e7b99-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e7b99-127">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="e7b99-127">Profiling</span></span>](index.md)
