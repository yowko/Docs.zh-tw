---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: bea857f65081432eb3f5501c75af6d13805c76d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426245"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="f43c3-102">ICorProfilerCallback::JITCachedFunctionSearchFinished 方法</span><span class="sxs-lookup"><span data-stu-id="f43c3-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="f43c3-103">通知分析工具已完成先前使用原生映射產生器（Ngen.exe）編譯之函式的搜尋。</span><span class="sxs-lookup"><span data-stu-id="f43c3-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f43c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="f43c3-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f43c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="f43c3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f43c3-106">在執行搜尋的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="f43c3-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="f43c3-107">在表示搜尋結果之[COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)列舉的值。</span><span class="sxs-lookup"><span data-stu-id="f43c3-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f43c3-108">備註</span><span class="sxs-lookup"><span data-stu-id="f43c3-108">Remarks</span></span>  
 <span data-ttu-id="f43c3-109">在 .NET Framework 版本2.0 中，不會對一般 NGen 影像中的所有函式進行[ICorProfilerCallback：： JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)和 `JITCachedFunctionSearchFinished` 回呼。</span><span class="sxs-lookup"><span data-stu-id="f43c3-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="f43c3-110">只有針對 profiler 優化的 NGen 影像才會針對影像中的所有函式產生回呼。</span><span class="sxs-lookup"><span data-stu-id="f43c3-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="f43c3-111">不過，由於額外的負擔，分析工具應該只在想要使用這些回呼來強制編譯函式（JIT）時，才要求 profiler 優化的 NGen 影像。</span><span class="sxs-lookup"><span data-stu-id="f43c3-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="f43c3-112">否則，分析工具應該使用延遲策略來收集函數資訊。</span><span class="sxs-lookup"><span data-stu-id="f43c3-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f43c3-113">需求</span><span class="sxs-lookup"><span data-stu-id="f43c3-113">Requirements</span></span>  
 <span data-ttu-id="f43c3-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f43c3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f43c3-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f43c3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f43c3-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f43c3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f43c3-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f43c3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43c3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f43c3-118">See also</span></span>

- [<span data-ttu-id="f43c3-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f43c3-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
