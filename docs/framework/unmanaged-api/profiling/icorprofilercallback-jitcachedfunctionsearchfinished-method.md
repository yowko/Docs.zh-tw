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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0e78e10f092bce1c8f7762362f02b7a403c86a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597231"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="76333-102">ICorProfilerCallback::JITCachedFunctionSearchFinished 方法</span><span class="sxs-lookup"><span data-stu-id="76333-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="76333-103">通知分析工具對於先前使用 原生映像產生器 (NGen.exe) 所編譯的函式已完成搜尋。</span><span class="sxs-lookup"><span data-stu-id="76333-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76333-104">語法</span><span class="sxs-lookup"><span data-stu-id="76333-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76333-105">參數</span><span class="sxs-lookup"><span data-stu-id="76333-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="76333-106">[in]執行搜尋函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="76333-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="76333-107">[in]值為[COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)列舉，指出搜尋的結果。</span><span class="sxs-lookup"><span data-stu-id="76333-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76333-108">備註</span><span class="sxs-lookup"><span data-stu-id="76333-108">Remarks</span></span>  
 <span data-ttu-id="76333-109">在.NET Framework 2.0 版中， [icorprofilercallback:: Jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)和`JITCachedFunctionSearchFinished`回呼將不會進行一般的 NGen 影像中的所有函式。</span><span class="sxs-lookup"><span data-stu-id="76333-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="76333-110">只適用於程式碼剖析工具的 NGen 映像會產生映像中的所有函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="76333-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="76333-111">不過，由於額外的負荷，分析工具應該要求程式碼剖析工具最佳化 NGen 影像才想要使用這些回呼強制函式會編譯在 just-in-time (JIT)。</span><span class="sxs-lookup"><span data-stu-id="76333-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="76333-112">分析工具，否則為要使用延遲的策略用於蒐集函式資訊使用。</span><span class="sxs-lookup"><span data-stu-id="76333-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76333-113">需求</span><span class="sxs-lookup"><span data-stu-id="76333-113">Requirements</span></span>  
 <span data-ttu-id="76333-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76333-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76333-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76333-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76333-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76333-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76333-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76333-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76333-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76333-118">See also</span></span>

- [<span data-ttu-id="76333-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="76333-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
