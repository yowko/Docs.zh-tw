---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: f71d0b5c77d4a514001bcbe6904ed912be388d18
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681544"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="3b7d1-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="3b7d1-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>

<span data-ttu-id="3b7d1-103">指定要在 managed 函式的「輸入」、「離開」和「tailcall」的更新版本上呼叫的 profiler 型函數。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b7d1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b7d1-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b7d1-105">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="3b7d1-106">在要當做 [FunctionEnter2](functionenter2-function.md) 回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="3b7d1-107">在要當做 [FunctionLeave2](functionleave2-function.md) 回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="3b7d1-108">在要當做 [FunctionTailcall2](functiontailcall2-function.md) 回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b7d1-109">備註</span><span class="sxs-lookup"><span data-stu-id="3b7d1-109">Remarks</span></span>  

 <span data-ttu-id="3b7d1-110">`SetEnterLeaveFunctionHooks2`方法類似于[ICorProfilerInfo：： SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="3b7d1-111">您可以使用前者來指定函式，以做為輸入/離開/tailcall 回呼的較新版本，而後者則指定要做為輸入/離開/tailcall 回呼的較舊版本使用的函數。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="3b7d1-112">一次只能有一組回呼處於作用中。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="3b7d1-113">因此，如果 profiler 同時呼叫 `ICorProfilerInfo::SetEnterLeaveFunctionHooks` 和 `SetEnterLeaveFunctionHooks2` ， `SetEnterLeaveFunctionHooks2` 則會使用。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="3b7d1-114">您 `SetEnterLeaveFunctionHooks2` 只能從分析工具的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 回呼呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b7d1-115">需求</span><span class="sxs-lookup"><span data-stu-id="3b7d1-115">Requirements</span></span>  

 <span data-ttu-id="3b7d1-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b7d1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b7d1-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b7d1-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b7d1-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b7d1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b7d1-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b7d1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7d1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b7d1-120">See also</span></span>

- [<span data-ttu-id="3b7d1-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3b7d1-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="3b7d1-122">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="3b7d1-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
