---
title: ICorProfilerInfo4 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 177e5ef8054f408dc8ec3475c56043394a636bc0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194210"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="f54ac-102">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="f54ac-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="f54ac-103">提供程式碼分析工具使用與通用語言執行平台 (CLR)，以控制事件監視以及要求資訊進行通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="f54ac-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="f54ac-104">。</span><span class="sxs-lookup"><span data-stu-id="f54ac-104">.</span></span> <span data-ttu-id="f54ac-105">`ICorProfilerInfo4`介面是其他延伸模組`ICorProfilerInfo`介面。</span><span class="sxs-lookup"><span data-stu-id="f54ac-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="f54ac-106">它提供新的方法，以支援在 just-in-time (JIT) 重新編譯中加入[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f54ac-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f54ac-107">方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-107">Methods</span></span>  
  
|<span data-ttu-id="f54ac-108">方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-108">Method</span></span>|<span data-ttu-id="f54ac-109">描述</span><span class="sxs-lookup"><span data-stu-id="f54ac-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f54ac-110">EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="f54ac-111">傳回所有先前 JIT 編譯和 JIT 重新編譯的函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f54ac-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="f54ac-112">EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="f54ac-113">取得列舉值，提供方法，以循序逐一查看分析的處理序中的所有 managed 執行緒的集合。</span><span class="sxs-lookup"><span data-stu-id="f54ac-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="f54ac-114">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="f54ac-115">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="f54ac-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="f54ac-116">GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="f54ac-117">將 managed 程式碼指令指標對應到指定的函式的 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="f54ac-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="f54ac-118">GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="f54ac-119">取得從 Microsoft intermediate language (MSIL) 位移到原生位移指定的函式的 JIT 重新編譯版本中包含的程式碼對應。</span><span class="sxs-lookup"><span data-stu-id="f54ac-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="f54ac-120">GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="f54ac-121">傳回指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="f54ac-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="f54ac-122">GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="f54ac-123">傳回識別 JIT 重新編譯的所有版本指定的函式仍配置的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="f54ac-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="f54ac-124">InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="f54ac-125">初始化目前的執行緒之前後續的程式碼剖析工具 API 呼叫在相同的執行緒，因此可以避免死結。</span><span class="sxs-lookup"><span data-stu-id="f54ac-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="f54ac-126">RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="f54ac-127">要求指定函式的所有執行個體進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="f54ac-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="f54ac-128">RequestRevert 方法</span><span class="sxs-lookup"><span data-stu-id="f54ac-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="f54ac-129">將指定函式的所有執行個體還原成其原始版本。</span><span class="sxs-lookup"><span data-stu-id="f54ac-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f54ac-130">備註</span><span class="sxs-lookup"><span data-stu-id="f54ac-130">Remarks</span></span>  
 <span data-ttu-id="f54ac-131">藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo4` 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="f54ac-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="f54ac-132">每個方法會傳回 HRESULT，表示成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="f54ac-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="f54ac-133">如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。</span><span class="sxs-lookup"><span data-stu-id="f54ac-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f54ac-134">需求</span><span class="sxs-lookup"><span data-stu-id="f54ac-134">Requirements</span></span>  
 <span data-ttu-id="f54ac-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f54ac-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f54ac-136">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f54ac-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f54ac-137">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f54ac-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f54ac-138">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f54ac-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f54ac-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f54ac-139">See also</span></span>

- [<span data-ttu-id="f54ac-140">分析介面</span><span class="sxs-lookup"><span data-stu-id="f54ac-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f54ac-141">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f54ac-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
