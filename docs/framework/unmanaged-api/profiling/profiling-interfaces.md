---
title: 分析介面
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059fadc5607e76b871083682136fda542ae9bacf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758193"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="8e9ee-102">分析介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-102">Profiling Interfaces</span></span>
<span data-ttu-id="8e9ee-103">本節說明 Unmanaged 介面，這類介面可讓您分析由 Common Language Runtime (CLR) 所執行的程式。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e9ee-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="8e9ee-104">In This Section</span></span>  
 [<span data-ttu-id="8e9ee-105">ICLRProfiling 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="8e9ee-106">提供[AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法，可讓分析工具附加至正在執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="8e9ee-107">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="8e9ee-108">可讓分析工具通知分析工具會在加入的組件參考的 CLR [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="8e9ee-109">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="8e9ee-110">提供讓 CLR 在分析工具已訂閱的事件發生時，通知程式碼分析工具的方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="8e9ee-111">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="8e9ee-112">使用 .NET Framework 2.0 及更新版本中支援的回呼，延伸 `ICorProfilerCallback` 介面。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="8e9ee-113">ICorProfilerCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="8e9ee-114">提供回呼方法，供 CLR 用於將連結及中斷連結的狀態資訊傳達給分析工具。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="8e9ee-115">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="8e9ee-116">提供回呼方法，供 CLR 用於將資訊傳達給分析工具。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="8e9ee-117">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="8e9ee-118">提供方法，以識別記憶體回收根目錄所參考之物件的可轉移關閉。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="8e9ee-119">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="8e9ee-120">提供 CLR 用於通知分析工具組件正在載入中的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="8e9ee-121">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="8e9ee-122">提供回呼方法，common language runtime 用來通知分析工具會更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="8e9ee-123">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-123">ICorProfilerCallback8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
<span data-ttu-id="8e9ee-124">提供 common language runtime 用來通知分析工具中的動態方法的 JIT 編譯已啟動並完成的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="8e9ee-125">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-125">ICorProfilerCallback9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
<span data-ttu-id="8e9ee-126">提供 common language runtime 用於通知的動態方法在記憶體回收，並接著卸載分析工具回呼方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="8e9ee-127">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-127">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="8e9ee-128">提供方法，讓程式碼分析工具能夠和 CLR 通訊，以控制 JIT 編譯器在重新編譯特定方法時，應如何產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="8e9ee-129">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-129">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="8e9ee-130">提供方法，以循序逐一查看 CLR 中的函式集合。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="8e9ee-131">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-131">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="8e9ee-132">提供程式碼分析工具用於和 CLR 通訊以控制事件監視及要求資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="8e9ee-133">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-133">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="8e9ee-134">使用 .NET Framework 2.0 及更新版本中支援的方法，延伸 `ICorProfilerInfo` 介面。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="8e9ee-135">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-135">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="8e9ee-136">使用 `ICorProfilerInfo2` 及更新版本中支援的方法，延伸 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 介面。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-136">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="8e9ee-137">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-137">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="8e9ee-138">提供程式碼分析工具用於和 CLR 通訊，以控制事件監視以及要求資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="8e9ee-139">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-139">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="8e9ee-140">提供程式碼分析工具用於和 CLR 通訊以控制事件監視的方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="8e9ee-141">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-141">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="8e9ee-142">請提供隸屬於指定的 NGen 模組，以及屬於指定的方法主體中內嵌的所有方法的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="8e9ee-143">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-143">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="8e9ee-144">提供方法，以套用新定義模組的中繼資料，並提供存取記憶體中的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="8e9ee-145">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-145">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="8e9ee-146">提供方法，以循序逐一查看由應用程式或分析工具所載入的模組集合。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="8e9ee-147">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-147">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="8e9ee-148">提供方法，以循序逐一查看所產生的凍結物件的集合[Ngen.exe （原生映像產生器）](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="8e9ee-149">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-149">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="8e9ee-150">提供方法，以循序逐一查看 CLR 中的執行緒集合。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="8e9ee-151">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="8e9ee-151">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="8e9ee-152">提供[Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)配置記憶體給新的 Microsoft intermediate language (MSIL) 函式主體的方法。</span><span class="sxs-lookup"><span data-stu-id="8e9ee-152">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8e9ee-153">相關章節</span><span class="sxs-lookup"><span data-stu-id="8e9ee-153">Related Sections</span></span>  
 [<span data-ttu-id="8e9ee-154">分析概觀</span><span class="sxs-lookup"><span data-stu-id="8e9ee-154">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="8e9ee-155">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="8e9ee-155">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="8e9ee-156">分析列舉</span><span class="sxs-lookup"><span data-stu-id="8e9ee-156">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="8e9ee-157">分析結構</span><span class="sxs-lookup"><span data-stu-id="8e9ee-157">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
