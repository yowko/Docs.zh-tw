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
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868573"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="39f9e-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="39f9e-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="39f9e-103">指定要在 managed 函式之 "enter"、"leave" 和 "tailcall" 勾點的更新版本上呼叫的分析工具所執行的函數。</span><span class="sxs-lookup"><span data-stu-id="39f9e-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="39f9e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39f9e-105">參數</span><span class="sxs-lookup"><span data-stu-id="39f9e-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="39f9e-106">在要當做[FunctionEnter2](functionenter2-function.md)回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="39f9e-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="39f9e-107">在要當做[FunctionLeave2](functionleave2-function.md)回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="39f9e-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="39f9e-108">在要當做[FunctionTailcall2](functiontailcall2-function.md)回呼使用的實作為指標。</span><span class="sxs-lookup"><span data-stu-id="39f9e-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39f9e-109">備註</span><span class="sxs-lookup"><span data-stu-id="39f9e-109">Remarks</span></span>  
 <span data-ttu-id="39f9e-110">`SetEnterLeaveFunctionHooks2` 方法類似于[ICorProfilerInfo：： SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="39f9e-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="39f9e-111">使用前者來指定要當做較新版本的進入/離開/tailcall 回呼使用的函式，而後者則用來指定要當做較舊版本的進入/離開/tailcall 回呼使用的函數。</span><span class="sxs-lookup"><span data-stu-id="39f9e-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="39f9e-112">一次只能有一組回呼處於作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="39f9e-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="39f9e-113">因此，如果 profiler 同時呼叫 `ICorProfilerInfo::SetEnterLeaveFunctionHooks` 和 `SetEnterLeaveFunctionHooks2`，則會使用 `SetEnterLeaveFunctionHooks2`。</span><span class="sxs-lookup"><span data-stu-id="39f9e-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="39f9e-114">只能從分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼呼叫 `SetEnterLeaveFunctionHooks2` 方法。</span><span class="sxs-lookup"><span data-stu-id="39f9e-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39f9e-115">需求</span><span class="sxs-lookup"><span data-stu-id="39f9e-115">Requirements</span></span>  
 <span data-ttu-id="39f9e-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39f9e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39f9e-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="39f9e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="39f9e-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39f9e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39f9e-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39f9e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f9e-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="39f9e-120">See also</span></span>

- [<span data-ttu-id="39f9e-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="39f9e-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="39f9e-122">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="39f9e-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
