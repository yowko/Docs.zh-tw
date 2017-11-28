---
title: "ICorProfilerCallback::JITCachedFunctionSearchFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ffbe331399334d179cf8325e7d9e6773b5bf7012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="84cc1-102">ICorProfilerCallback::JITCachedFunctionSearchFinished 方法</span><span class="sxs-lookup"><span data-stu-id="84cc1-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="84cc1-103">通知分析工具用於先前使用原生映像產生器 (NGen.exe) 所編譯的函式已完成搜尋。</span><span class="sxs-lookup"><span data-stu-id="84cc1-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84cc1-104">語法</span><span class="sxs-lookup"><span data-stu-id="84cc1-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84cc1-105">參數</span><span class="sxs-lookup"><span data-stu-id="84cc1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="84cc1-106">[in]搜尋已執行其函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="84cc1-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="84cc1-107">[in]值為[COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)列舉，指出的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="84cc1-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84cc1-108">備註</span><span class="sxs-lookup"><span data-stu-id="84cc1-108">Remarks</span></span>  
 <span data-ttu-id="84cc1-109">在.NET Framework 2.0 版中， [icorprofilercallback:: Jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)和`JITCachedFunctionSearchFinished`回呼將不會進行一般 NGen 映像中的所有函式。</span><span class="sxs-lookup"><span data-stu-id="84cc1-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="84cc1-110">只針對分析工具進行最佳化的 NGen 映像將映像中產生的所有函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="84cc1-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="84cc1-111">不過，額外負擔，因為分析工具應該要求程式碼剖析工具最佳化 NGen 影像才想要使用這些回呼強制將函式編譯在 just-in-time (JIT)。</span><span class="sxs-lookup"><span data-stu-id="84cc1-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="84cc1-112">否則，分析工具應該收集的資訊函式使用延遲的策略。</span><span class="sxs-lookup"><span data-stu-id="84cc1-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84cc1-113">需求</span><span class="sxs-lookup"><span data-stu-id="84cc1-113">Requirements</span></span>  
 <span data-ttu-id="84cc1-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84cc1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84cc1-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84cc1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84cc1-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84cc1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84cc1-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84cc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cc1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84cc1-118">See Also</span></span>  
 [<span data-ttu-id="84cc1-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="84cc1-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
