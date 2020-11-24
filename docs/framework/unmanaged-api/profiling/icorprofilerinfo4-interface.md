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
ms.openlocfilehash: c3e623b0b5f8b49e043fe3a1aa8311558e573573
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682831"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="9ed6a-102">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="9ed6a-102">ICorProfilerInfo4 Interface</span></span>

<span data-ttu-id="9ed6a-103">提供程式碼分析工具用來與 common language runtime 進行通訊的方法， (CLR) 來控制事件監視和要求資訊。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="9ed6a-104">.</span><span class="sxs-lookup"><span data-stu-id="9ed6a-104">.</span></span> <span data-ttu-id="9ed6a-105">`ICorProfilerInfo4`介面是其他介面的延伸 `ICorProfilerInfo` 。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="9ed6a-106">它提供新的方法，以支援 .NET Framework 4.5 中新增的即時 (JIT) 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ed6a-107">方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-107">Methods</span></span>  
  
|<span data-ttu-id="9ed6a-108">方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-108">Method</span></span>|<span data-ttu-id="9ed6a-109">描述</span><span class="sxs-lookup"><span data-stu-id="9ed6a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ed6a-110">EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="9ed6a-111">傳回先前 JIT 編譯和 JIT 重新編譯之所有函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="9ed6a-112">EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="9ed6a-113">取得列舉值，這個列舉值會提供方法，以依序逐一查看已分析進程中所有 managed 執行緒的集合。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="9ed6a-114">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="9ed6a-115">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="9ed6a-116">GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="9ed6a-117">將 managed 程式碼指令指標對應至指定之函式的 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="9ed6a-118">GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="9ed6a-119">取得 Microsoft 中繼語言 (MSIL 的對應，) 指定函式之 JIT 重新編譯版本中所包含之程式碼的原生位移。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="9ed6a-120">GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="9ed6a-121">傳回指定之物件的大小。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="9ed6a-122">GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="9ed6a-123">傳回識別碼陣列，識別仍配置之指定函式的所有 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="9ed6a-124">InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="9ed6a-125">在相同執行緒上的後續分析工具 API 呼叫之前，初始化目前的執行緒，因此可以避免鎖死。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="9ed6a-126">RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="9ed6a-127">要求指定函式的所有執行個體進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="9ed6a-128">RequestRevert 方法</span><span class="sxs-lookup"><span data-stu-id="9ed6a-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="9ed6a-129">將指定函式的所有執行個體還原成其原始版本。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed6a-130">備註</span><span class="sxs-lookup"><span data-stu-id="9ed6a-130">Remarks</span></span>  

 <span data-ttu-id="9ed6a-131">藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo4` 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="9ed6a-132">每個方法會傳回 HRESULT，表示成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="9ed6a-133">如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed6a-134">需求</span><span class="sxs-lookup"><span data-stu-id="9ed6a-134">Requirements</span></span>  

 <span data-ttu-id="9ed6a-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed6a-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed6a-136">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ed6a-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ed6a-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ed6a-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed6a-138">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed6a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed6a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ed6a-139">See also</span></span>

- [<span data-ttu-id="9ed6a-140">分析介面</span><span class="sxs-lookup"><span data-stu-id="9ed6a-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9ed6a-141">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="9ed6a-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
