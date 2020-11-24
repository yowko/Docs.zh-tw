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
ms.openlocfilehash: fe07270989df897c3dbf689305784f9f0af65742
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684040"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="7034f-102">ICorProfilerCallback::JITCachedFunctionSearchFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7034f-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>

<span data-ttu-id="7034f-103">通知分析工具，在先前使用原生映射產生器 ( # A0) 編譯的函式已完成搜尋。</span><span class="sxs-lookup"><span data-stu-id="7034f-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7034f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7034f-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7034f-105">參數</span><span class="sxs-lookup"><span data-stu-id="7034f-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="7034f-106">\[in] 執行搜尋的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="7034f-106">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="7034f-107">\[in] [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) 列舉的值，表示搜尋的結果。</span><span class="sxs-lookup"><span data-stu-id="7034f-107">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="7034f-108">備註</span><span class="sxs-lookup"><span data-stu-id="7034f-108">Remarks</span></span>  

 <span data-ttu-id="7034f-109">在 .NET Framework 2.0 版中，不會對一般 NGen 影像中的所有函式進行 [ICorProfilerCallback：： JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) 和 `JITCachedFunctionSearchFinished` 回呼。</span><span class="sxs-lookup"><span data-stu-id="7034f-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="7034f-110">只有針對分析工具優化的 NGen 映射才會產生影像中所有函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="7034f-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="7034f-111">不過，由於額外的額外負荷，分析工具應該只在想要使用這些回呼來強制將函式編譯為即時 (JIT) 時，才要求 profiler 優化的 NGen 映射。</span><span class="sxs-lookup"><span data-stu-id="7034f-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="7034f-112">否則，分析工具應該使用延遲策略來收集函數資訊。</span><span class="sxs-lookup"><span data-stu-id="7034f-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7034f-113">需求</span><span class="sxs-lookup"><span data-stu-id="7034f-113">Requirements</span></span>  

 <span data-ttu-id="7034f-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7034f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7034f-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7034f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7034f-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7034f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7034f-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7034f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7034f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7034f-118">See also</span></span>

- [<span data-ttu-id="7034f-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7034f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
