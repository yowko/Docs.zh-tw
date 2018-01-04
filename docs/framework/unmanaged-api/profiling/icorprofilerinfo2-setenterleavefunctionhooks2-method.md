---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c460cfd24a83ca2a6c75e061b7a797c8f455bc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="b9cad-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="b9cad-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="b9cad-103">指定程式碼剖析工具實作函式上更新版本的 「 輸入 」、 「 保留 」 和 「 tailcall"攔截 managed 函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b9cad-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9cad-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9cad-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9cad-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9cad-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="b9cad-106">[in]指向要做為實作[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="b9cad-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="b9cad-107">[in]指向要做為實作[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="b9cad-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="b9cad-108">[in]指向要做為實作[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="b9cad-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9cad-109">備註</span><span class="sxs-lookup"><span data-stu-id="b9cad-109">Remarks</span></span>  
 <span data-ttu-id="b9cad-110">`SetEnterLeaveFunctionHooks2`方法很類似[icorprofilerinfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b9cad-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="b9cad-111">以指定要做為輸入/保持/tailcall 回呼和後者的較新版本以指定要做為輸入/保持/tailcall 回呼較舊版本的函式的函式使用前者。</span><span class="sxs-lookup"><span data-stu-id="b9cad-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="b9cad-112">一次只能有一組的回呼可能作用中。</span><span class="sxs-lookup"><span data-stu-id="b9cad-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="b9cad-113">因此，如果程式碼剖析工具呼叫兩者`ICorProfilerInfo::SetEnterLeaveFunctionHooks`和`SetEnterLeaveFunctionHooks2`，`SetEnterLeaveFunctionHooks2`用。</span><span class="sxs-lookup"><span data-stu-id="b9cad-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="b9cad-114">`SetEnterLeaveFunctionHooks2`方法可能只會從程式碼剖析工具呼叫[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="b9cad-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9cad-115">需求</span><span class="sxs-lookup"><span data-stu-id="b9cad-115">Requirements</span></span>  
 <span data-ttu-id="b9cad-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9cad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9cad-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9cad-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9cad-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9cad-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9cad-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9cad-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9cad-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9cad-120">See Also</span></span>  
 [<span data-ttu-id="b9cad-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="b9cad-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="b9cad-122">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="b9cad-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
