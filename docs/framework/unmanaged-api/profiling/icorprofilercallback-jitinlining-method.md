---
title: ICorProfilerCallback::JITInlining 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 62035d623d56f7521e0a599a13bc20778e3f18d1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449910"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="800d8-102">ICorProfilerCallback::JITInlining 方法</span><span class="sxs-lookup"><span data-stu-id="800d8-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="800d8-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span><span class="sxs-lookup"><span data-stu-id="800d8-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="800d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="800d8-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="800d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="800d8-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="800d8-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span><span class="sxs-lookup"><span data-stu-id="800d8-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="800d8-107">[in] The ID of the function to be inserted.</span><span class="sxs-lookup"><span data-stu-id="800d8-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="800d8-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="800d8-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="800d8-109">備註</span><span class="sxs-lookup"><span data-stu-id="800d8-109">Remarks</span></span>  
 <span data-ttu-id="800d8-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span><span class="sxs-lookup"><span data-stu-id="800d8-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="800d8-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="800d8-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="800d8-112">Functions inserted inline do not raise events for entering or leaving.</span><span class="sxs-lookup"><span data-stu-id="800d8-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="800d8-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span><span class="sxs-lookup"><span data-stu-id="800d8-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="800d8-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span><span class="sxs-lookup"><span data-stu-id="800d8-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="800d8-115">需求</span><span class="sxs-lookup"><span data-stu-id="800d8-115">Requirements</span></span>  
 <span data-ttu-id="800d8-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="800d8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="800d8-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="800d8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="800d8-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="800d8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="800d8-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="800d8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="800d8-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="800d8-120">See also</span></span>

- [<span data-ttu-id="800d8-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="800d8-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
