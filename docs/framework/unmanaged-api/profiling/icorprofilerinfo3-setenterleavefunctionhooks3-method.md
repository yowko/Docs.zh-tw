---
title: "ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77a2e8170cd2cf78576b2d376fb592c903bbb403
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="6685c-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 方法</span><span class="sxs-lookup"><span data-stu-id="6685c-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="6685c-103">指定要呼叫的程式碼剖析工具實作函式[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)， [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)，和[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="6685c-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6685c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6685c-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6685c-105">參數</span><span class="sxs-lookup"><span data-stu-id="6685c-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="6685c-106">[in]指向要做為實作`FunctionEnter3`回呼。</span><span class="sxs-lookup"><span data-stu-id="6685c-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="6685c-107">[in]指向要做為實作`FunctionLeave3`回呼。</span><span class="sxs-lookup"><span data-stu-id="6685c-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="6685c-108">[in]指向要做為實作`FunctionTailcall3`回呼。</span><span class="sxs-lookup"><span data-stu-id="6685c-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6685c-109">備註</span><span class="sxs-lookup"><span data-stu-id="6685c-109">Remarks</span></span>  
 <span data-ttu-id="6685c-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)， [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)，和[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)攔截程序不會提供堆疊框架和引數的檢查。</span><span class="sxs-lookup"><span data-stu-id="6685c-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="6685c-111">若要存取該資訊之後， `COR_PRF_ENABLE_FUNCTION_ARGS`， `COR_PRF_ENABLE_FUNCTION_RETVAL`，及/或`COR_PRF_ENABLE_FRAME_INFO`旗標必須設定。</span><span class="sxs-lookup"><span data-stu-id="6685c-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="6685c-112">分析工具可以使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件的旗標，然後使用[icorprofilerinfo3:: Setenterleavefunctionhooks3withinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)方法來註冊您此函式實作。</span><span class="sxs-lookup"><span data-stu-id="6685c-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6685c-113">一次只能有一組的回呼可能在作用中，會優先使用最新版本。</span><span class="sxs-lookup"><span data-stu-id="6685c-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="6685c-114">因此，如果程式碼剖析工具呼叫兩者[SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)和`SetEnterLeaveFunctionHooks3`方法，`SetEnterLeaveFunctionHooks3`用。</span><span class="sxs-lookup"><span data-stu-id="6685c-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="6685c-115">`SetEnterLeaveFunctionHooks3`方法可能只會從程式碼剖析工具呼叫[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="6685c-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6685c-116">需求</span><span class="sxs-lookup"><span data-stu-id="6685c-116">Requirements</span></span>  
 <span data-ttu-id="6685c-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6685c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6685c-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6685c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6685c-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6685c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6685c-120">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6685c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6685c-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="6685c-121">See Also</span></span>  
 [<span data-ttu-id="6685c-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6685c-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="6685c-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="6685c-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="6685c-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="6685c-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="6685c-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="6685c-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="6685c-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6685c-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="6685c-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6685c-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="6685c-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6685c-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="6685c-129">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6685c-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="6685c-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="6685c-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="6685c-131">分析介面</span><span class="sxs-lookup"><span data-stu-id="6685c-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6685c-132">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="6685c-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
