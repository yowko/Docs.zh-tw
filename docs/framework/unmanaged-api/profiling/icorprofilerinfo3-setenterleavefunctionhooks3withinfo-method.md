---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: d40cb424306535cc502d930dd61e6a1e254667da
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496174"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="03be5-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法</span><span class="sxs-lookup"><span data-stu-id="03be5-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="03be5-103">指定將在 managed 函式的[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)勾點上呼叫的分析工具所執行的函數。</span><span class="sxs-lookup"><span data-stu-id="03be5-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03be5-104">語法</span><span class="sxs-lookup"><span data-stu-id="03be5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03be5-105">參數</span><span class="sxs-lookup"><span data-stu-id="03be5-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="03be5-106">在要當做回呼使用的實作為指標 `FunctionEnter3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="03be5-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="03be5-107">在要當做回呼使用的實作為指標 `FunctionLeave3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="03be5-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="03be5-108">在要當做回呼使用的實作為指標 `FunctionTailcall3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="03be5-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03be5-109">備註</span><span class="sxs-lookup"><span data-stu-id="03be5-109">Remarks</span></span>  
 <span data-ttu-id="03be5-110">[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)勾點提供了堆疊框架和引數檢查。</span><span class="sxs-lookup"><span data-stu-id="03be5-110">The [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="03be5-111">若要存取該資訊， `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` 必須設定、和（或） `COR_PRF_ENABLE_FRAME_INFO` 旗標。</span><span class="sxs-lookup"><span data-stu-id="03be5-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="03be5-112">分析工具可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標，然後使用 `SetEnterLeaveFunctionHooks3WithInfo` 方法來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="03be5-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="03be5-113">一次只能有一組回呼處於作用中狀態，而最新的版本會優先使用。</span><span class="sxs-lookup"><span data-stu-id="03be5-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="03be5-114">因此，如果 profiler 同時呼叫[SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)和 `SetEnterLeaveFunctionHooks3WithInfo` ， `SetEnterLeaveFunctionHooks3WithInfo` 則會使用。</span><span class="sxs-lookup"><span data-stu-id="03be5-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="03be5-115">`SetEnterLeaveFunctionHooks3WithInfo`只能從分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="03be5-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03be5-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="03be5-116">Requirements</span></span>  
 <span data-ttu-id="03be5-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03be5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03be5-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="03be5-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03be5-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03be5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03be5-120">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03be5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03be5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03be5-121">See also</span></span>

- [<span data-ttu-id="03be5-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="03be5-122">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="03be5-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="03be5-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="03be5-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="03be5-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="03be5-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="03be5-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="03be5-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="03be5-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="03be5-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="03be5-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="03be5-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="03be5-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="03be5-129">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="03be5-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="03be5-130">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="03be5-130">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="03be5-131">分析介面</span><span class="sxs-lookup"><span data-stu-id="03be5-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="03be5-132">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="03be5-132">Profiling</span></span>](index.md)
