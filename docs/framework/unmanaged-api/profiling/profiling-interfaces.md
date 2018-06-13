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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462048"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="e7cdc-102">分析介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-102">Profiling Interfaces</span></span>
<span data-ttu-id="e7cdc-103">本節說明 Unmanaged 介面，這類介面可讓您分析由 Common Language Runtime (CLR) 所執行的程式。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7cdc-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="e7cdc-104">In This Section</span></span>  
 [<span data-ttu-id="e7cdc-105">ICLRProfiling 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="e7cdc-106">提供[AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法，可讓分析工具附加至正在執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="e7cdc-107">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="e7cdc-108">可讓分析工具通知分析工具會在中加入的組件參考的 CLR [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="e7cdc-109">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="e7cdc-110">提供讓 CLR 在分析工具已訂閱的事件發生時，通知程式碼分析工具的方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="e7cdc-111">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="e7cdc-112">使用 .NET Framework 2.0 及更新版本中支援的回呼，延伸 `ICorProfilerCallback` 介面。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="e7cdc-113">ICorProfilerCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="e7cdc-114">提供回呼方法，供 CLR 用於將連結及中斷連結的狀態資訊傳達給分析工具。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="e7cdc-115">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="e7cdc-116">提供回呼方法，供 CLR 用於將資訊傳達給分析工具。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="e7cdc-117">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="e7cdc-118">提供方法，以識別記憶體回收根目錄所參考之物件的可轉移關閉。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="e7cdc-119">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="e7cdc-120">提供 CLR 用於通知分析工具組件正在載入中的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="e7cdc-121">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="e7cdc-122">提供 common language runtime 用於通知分析工具會更新記憶體中模組相關聯的符號資料流的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="e7cdc-123">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-123">ICorProfilerCallback8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
<span data-ttu-id="e7cdc-124">提供 common language runtime 用於通知的動態方法的 JIT 編譯已啟動及完成的分析工具回呼方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="e7cdc-125">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-125">ICorProfilerCallback9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
<span data-ttu-id="e7cdc-126">提供 common language runtime 用於通知的動態方法在記憶體回收，並接著卸載分析工具回呼方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="e7cdc-127">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-127">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="e7cdc-128">提供方法，讓程式碼分析工具能夠和 CLR 通訊，以控制 JIT 編譯器在重新編譯特定方法時，應如何產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="e7cdc-129">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-129">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="e7cdc-130">提供方法，以循序逐一查看 CLR 中的函式集合。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="e7cdc-131">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-131">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="e7cdc-132">提供程式碼分析工具用於和 CLR 通訊以控制事件監視及要求資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="e7cdc-133">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-133">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="e7cdc-134">使用 .NET Framework 2.0 及更新版本中支援的方法，延伸 `ICorProfilerInfo` 介面。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="e7cdc-135">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-135">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="e7cdc-136">使用 `ICorProfilerInfo2` 及更新版本中支援的方法，延伸 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 介面。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-136">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="e7cdc-137">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-137">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="e7cdc-138">提供程式碼分析工具用於和 CLR 通訊，以控制事件監視以及要求資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="e7cdc-139">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-139">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="e7cdc-140">提供程式碼分析工具用於和 CLR 通訊以控制事件監視的方法。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="e7cdc-141">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-141">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="e7cdc-142">請提供隸屬於給定的 NGen 模組，以及屬於給定方法主體中內嵌的所有方法的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="e7cdc-143">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-143">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="e7cdc-144">提供方法，以套用新定義的中繼資料至模組，以及提供存取記憶體中的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="e7cdc-145">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-145">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="e7cdc-146">提供方法，以循序逐一查看由應用程式或分析工具所載入的模組集合。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="e7cdc-147">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-147">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="e7cdc-148">提供方法，以循序逐一查看所產生的已凍結物件的集合[Ngen.exe （原生映像產生器）](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="e7cdc-149">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-149">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="e7cdc-150">提供方法，以循序逐一查看 CLR 中的執行緒集合。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="e7cdc-151">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="e7cdc-151">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="e7cdc-152">提供[配置](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)方法來為新的 Microsoft intermediate language (MSIL) 函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="e7cdc-152">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7cdc-153">相關章節</span><span class="sxs-lookup"><span data-stu-id="e7cdc-153">Related Sections</span></span>  
 [<span data-ttu-id="e7cdc-154">分析概觀</span><span class="sxs-lookup"><span data-stu-id="e7cdc-154">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="e7cdc-155">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e7cdc-155">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="e7cdc-156">分析列舉</span><span class="sxs-lookup"><span data-stu-id="e7cdc-156">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="e7cdc-157">分析結構</span><span class="sxs-lookup"><span data-stu-id="e7cdc-157">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
