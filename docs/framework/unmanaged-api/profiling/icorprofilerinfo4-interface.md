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
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448012"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="26b80-102">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="26b80-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="26b80-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span><span class="sxs-lookup"><span data-stu-id="26b80-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="26b80-104">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="26b80-104">.</span></span> <span data-ttu-id="26b80-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span><span class="sxs-lookup"><span data-stu-id="26b80-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="26b80-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="26b80-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26b80-107">方法</span><span class="sxs-lookup"><span data-stu-id="26b80-107">Methods</span></span>  
  
|<span data-ttu-id="26b80-108">方法</span><span class="sxs-lookup"><span data-stu-id="26b80-108">Method</span></span>|<span data-ttu-id="26b80-109">描述</span><span class="sxs-lookup"><span data-stu-id="26b80-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26b80-110">EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="26b80-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span><span class="sxs-lookup"><span data-stu-id="26b80-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="26b80-112">EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="26b80-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span><span class="sxs-lookup"><span data-stu-id="26b80-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="26b80-114">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="26b80-115">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="26b80-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="26b80-116">GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="26b80-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span><span class="sxs-lookup"><span data-stu-id="26b80-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="26b80-118">GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="26b80-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span><span class="sxs-lookup"><span data-stu-id="26b80-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="26b80-120">GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="26b80-121">Returns the size of a specified object.</span><span class="sxs-lookup"><span data-stu-id="26b80-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="26b80-122">GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="26b80-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span><span class="sxs-lookup"><span data-stu-id="26b80-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="26b80-124">InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="26b80-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span><span class="sxs-lookup"><span data-stu-id="26b80-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="26b80-126">RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="26b80-127">要求指定函式的所有執行個體進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="26b80-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="26b80-128">RequestRevert 方法</span><span class="sxs-lookup"><span data-stu-id="26b80-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="26b80-129">將指定函式的所有執行個體還原成其原始版本。</span><span class="sxs-lookup"><span data-stu-id="26b80-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26b80-130">備註</span><span class="sxs-lookup"><span data-stu-id="26b80-130">Remarks</span></span>  
 <span data-ttu-id="26b80-131">藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo4` 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="26b80-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="26b80-132">每個方法會傳回 HRESULT，表示成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="26b80-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="26b80-133">如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。</span><span class="sxs-lookup"><span data-stu-id="26b80-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b80-134">需求</span><span class="sxs-lookup"><span data-stu-id="26b80-134">Requirements</span></span>  
 <span data-ttu-id="26b80-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26b80-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b80-136">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26b80-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26b80-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26b80-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b80-138">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b80-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b80-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="26b80-139">See also</span></span>

- [<span data-ttu-id="26b80-140">分析介面</span><span class="sxs-lookup"><span data-stu-id="26b80-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="26b80-141">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="26b80-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
