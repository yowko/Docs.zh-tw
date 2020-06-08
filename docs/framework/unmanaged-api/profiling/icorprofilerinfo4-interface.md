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
ms.openlocfilehash: 58d11e9084f53c69f2656b4f0ee6bc7d2cc4ae21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495862"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="441e4-102">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="441e4-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="441e4-103">提供程式碼分析工具用來與 common language runtime （CLR）通訊的方法，以控制事件監視和要求資訊。</span><span class="sxs-lookup"><span data-stu-id="441e4-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="441e4-104">.</span><span class="sxs-lookup"><span data-stu-id="441e4-104">.</span></span> <span data-ttu-id="441e4-105">`ICorProfilerInfo4`介面是其他介面的延伸 `ICorProfilerInfo` 。</span><span class="sxs-lookup"><span data-stu-id="441e4-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="441e4-106">它提供新的方法來支援及時（JIT）重新編譯，並在 .NET Framework 4.5 中新增。</span><span class="sxs-lookup"><span data-stu-id="441e4-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="441e4-107">方法</span><span class="sxs-lookup"><span data-stu-id="441e4-107">Methods</span></span>  
  
|<span data-ttu-id="441e4-108">方法</span><span class="sxs-lookup"><span data-stu-id="441e4-108">Method</span></span>|<span data-ttu-id="441e4-109">描述</span><span class="sxs-lookup"><span data-stu-id="441e4-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="441e4-110">EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="441e4-111">傳回先前已進行 JIT 編譯和 JIT 重新編譯之所有函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="441e4-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="441e4-112">EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="441e4-113">取得列舉值，這個枚舉器會提供逐步逐一查看已分析進程中所有 managed 執行緒集合的方法。</span><span class="sxs-lookup"><span data-stu-id="441e4-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="441e4-114">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="441e4-115">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="441e4-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="441e4-116">GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="441e4-117">將 managed 程式碼指令指標對應至所指定函式的 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="441e4-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="441e4-118">GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="441e4-119">取得從 Microsoft 中繼語言（MSIL）位移到指定函式之 JIT 重新編譯版本中所含程式碼之原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="441e4-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="441e4-120">GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="441e4-121">傳回指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="441e4-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="441e4-122">GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="441e4-123">傳回識別碼的陣列，識別仍然配置的指定函式的所有 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="441e4-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="441e4-124">InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="441e4-125">在同一個執行緒上的後續分析工具 API 呼叫之前，將目前的執行緒初始化，以便避免鎖死。</span><span class="sxs-lookup"><span data-stu-id="441e4-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="441e4-126">RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="441e4-127">要求指定函式的所有執行個體進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="441e4-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="441e4-128">RequestRevert 方法</span><span class="sxs-lookup"><span data-stu-id="441e4-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="441e4-129">將指定函式的所有執行個體還原成其原始版本。</span><span class="sxs-lookup"><span data-stu-id="441e4-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="441e4-130">備註</span><span class="sxs-lookup"><span data-stu-id="441e4-130">Remarks</span></span>  
 <span data-ttu-id="441e4-131">藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo4` 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="441e4-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="441e4-132">每個方法會傳回 HRESULT，表示成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="441e4-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="441e4-133">如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。</span><span class="sxs-lookup"><span data-stu-id="441e4-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="441e4-134">規格需求</span><span class="sxs-lookup"><span data-stu-id="441e4-134">Requirements</span></span>  
 <span data-ttu-id="441e4-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="441e4-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="441e4-136">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="441e4-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="441e4-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="441e4-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="441e4-138">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="441e4-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441e4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="441e4-139">See also</span></span>

- [<span data-ttu-id="441e4-140">分析介面</span><span class="sxs-lookup"><span data-stu-id="441e4-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="441e4-141">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="441e4-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
