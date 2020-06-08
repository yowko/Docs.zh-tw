---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497448"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="fb8d7-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法</span><span class="sxs-lookup"><span data-stu-id="fb8d7-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="fb8d7-103">指定要在「輸入」、「離開」和 managed 函式的「tailcall」攔截器上呼叫的分析工具所實函數。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb8d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb8d7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb8d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="fb8d7-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="fb8d7-106">在要當做[FunctionEnter](functionenter-function.md)回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="fb8d7-107">在要當做[FunctionLeave](functionleave-function.md)回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="fb8d7-108">在要當做[FunctionTailcall](functiontailcall-function.md)回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb8d7-109">備註</span><span class="sxs-lookup"><span data-stu-id="fb8d7-109">Remarks</span></span>  
 <span data-ttu-id="fb8d7-110">在 .NET Framework 版本1.0 中，每個函式指標都可以是 null，以停用該對應的回呼。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="fb8d7-111">一次只能使用一組回呼。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="fb8d7-112">因此，如果 profiler 同時呼叫 `SetEnterLeaveFunctionHooks` 和[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，則 `SetEnterLeaveFunctionHooks2` 會優先使用。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="fb8d7-113">只能 `SetEnterLeaveFunctionHooks` 從分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb8d7-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="fb8d7-114">Requirements</span></span>  
 <span data-ttu-id="fb8d7-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb8d7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb8d7-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb8d7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb8d7-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb8d7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb8d7-118">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb8d7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb8d7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb8d7-119">See also</span></span>

- [<span data-ttu-id="fb8d7-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fb8d7-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
