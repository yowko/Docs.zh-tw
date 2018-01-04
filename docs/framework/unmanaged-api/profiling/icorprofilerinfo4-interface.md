---
title: "ICorProfilerInfo4 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83629d0fc8288d118ec31c38473cb63335bb1d48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="fb6ae-102">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="fb6ae-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="fb6ae-103">提供程式碼分析工具用於和 common language runtime (CLR)，以控制事件監視以及要求資訊通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="fb6ae-104">。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-104">.</span></span> <span data-ttu-id="fb6ae-105">`ICorProfilerInfo4`介面是其他擴充功能`ICorProfilerInfo`介面。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="fb6ae-106">它會提供新方法來支援在 just-in-time (JIT) 重新編譯中加入[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb6ae-107">方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-107">Methods</span></span>  
  
|<span data-ttu-id="fb6ae-108">方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-108">Method</span></span>|<span data-ttu-id="fb6ae-109">描述</span><span class="sxs-lookup"><span data-stu-id="fb6ae-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb6ae-110">EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="fb6ae-111">傳回所有先前 JIT 編譯和 JIT 重新編譯的函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="fb6ae-112">EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="fb6ae-113">取得可提供方法，以循序逐一查看集合的已分析的處理序中的所有 managed 執行緒的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="fb6ae-114">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="fb6ae-115">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="fb6ae-116">GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="fb6ae-117">將 managed 程式碼指令指標對應至指定的函式的 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="fb6ae-118">GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="fb6ae-119">取得從 Microsoft intermediate language (MSIL) 位移到原生位移的指定函式的 JIT 重新編譯版本中包含的程式碼對應。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="fb6ae-120">GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="fb6ae-121">傳回指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="fb6ae-122">GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="fb6ae-123">傳回識別 JIT 重新編譯的所有版本的指定函式仍配置的識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="fb6ae-124">InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="fb6ae-125">初始化目前的執行緒之前後續程式碼剖析工具應用程式開發介面呼叫，在相同執行緒，因此可以避免發生死結。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="fb6ae-126">RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="fb6ae-127">要求指定函式的所有執行個體進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="fb6ae-128">RequestRevert 方法</span><span class="sxs-lookup"><span data-stu-id="fb6ae-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="fb6ae-129">將指定函式的所有執行個體還原成其原始版本。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb6ae-130">備註</span><span class="sxs-lookup"><span data-stu-id="fb6ae-130">Remarks</span></span>  
 <span data-ttu-id="fb6ae-131">藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo4` 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="fb6ae-132">每個方法會傳回 HRESULT，表示成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="fb6ae-133">如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb6ae-134">需求</span><span class="sxs-lookup"><span data-stu-id="fb6ae-134">Requirements</span></span>  
 <span data-ttu-id="fb6ae-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb6ae-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb6ae-136">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb6ae-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb6ae-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb6ae-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb6ae-138">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb6ae-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb6ae-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb6ae-139">See Also</span></span>  
 [<span data-ttu-id="fb6ae-140">分析介面</span><span class="sxs-lookup"><span data-stu-id="fb6ae-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="fb6ae-141">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fb6ae-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
