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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f95a404ce7124a76ee527cdc70ccccf103838b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076792"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="63660-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="63660-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="63660-103">指定分析工具實作函式呼叫上的 「 輸入 」、 「 保留 」 和 「 tailcall 「 勾點 managed 函式的已更新的版本。</span><span class="sxs-lookup"><span data-stu-id="63660-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63660-104">語法</span><span class="sxs-lookup"><span data-stu-id="63660-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63660-105">參數</span><span class="sxs-lookup"><span data-stu-id="63660-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="63660-106">[in]要做為實作的指標[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="63660-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="63660-107">[in]要做為實作的指標[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="63660-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="63660-108">[in]要做為實作的指標[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="63660-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63660-109">備註</span><span class="sxs-lookup"><span data-stu-id="63660-109">Remarks</span></span>  
 <span data-ttu-id="63660-110">`SetEnterLeaveFunctionHooks2`方法是類似[icorprofilerinfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="63660-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="63660-111">您可以使用先前指定的 enter/保持/tailcall 回呼和後者較新版本用來指定用於舊版的 enter/保持/tailcall 回呼函式的函式。</span><span class="sxs-lookup"><span data-stu-id="63660-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="63660-112">只有一組回呼可能會使用一次。</span><span class="sxs-lookup"><span data-stu-id="63660-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="63660-113">因此，如果程式碼剖析工具呼叫兩者`ICorProfilerInfo::SetEnterLeaveFunctionHooks`並`SetEnterLeaveFunctionHooks2`，`SetEnterLeaveFunctionHooks2`用。</span><span class="sxs-lookup"><span data-stu-id="63660-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="63660-114">`SetEnterLeaveFunctionHooks2`可能只會從分析工具的呼叫方法[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="63660-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63660-115">需求</span><span class="sxs-lookup"><span data-stu-id="63660-115">Requirements</span></span>  
 <span data-ttu-id="63660-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63660-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63660-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63660-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63660-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63660-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63660-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63660-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63660-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63660-120">See also</span></span>

- [<span data-ttu-id="63660-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="63660-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="63660-122">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="63660-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
