---
title: 分析介面
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: f073794b4fdf89f289b70fed9967ee37b5f4e133
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494029"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="558bd-102">分析介面</span><span class="sxs-lookup"><span data-stu-id="558bd-102">Profiling Interfaces</span></span>
<span data-ttu-id="558bd-103">本節說明 Unmanaged 介面，這類介面可讓您分析由 Common Language Runtime (CLR) 所執行的程式。</span><span class="sxs-lookup"><span data-stu-id="558bd-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="558bd-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="558bd-104">In This Section</span></span>  
 [<span data-ttu-id="558bd-105">ICLRProfiling 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-105">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="558bd-106">提供[AttachProfiler](iclrprofiling-attachprofiler-method.md)方法，可讓 profiler 附加至執行中的進程。</span><span class="sxs-lookup"><span data-stu-id="558bd-106">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="558bd-107">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="558bd-108">可讓分析工具通知元件參考的 CLR，而分析工具將會在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼中新增此檔案。</span><span class="sxs-lookup"><span data-stu-id="558bd-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="558bd-109">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-109">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="558bd-110">提供讓 CLR 在分析工具已訂閱的事件發生時，通知程式碼分析工具的方法。</span><span class="sxs-lookup"><span data-stu-id="558bd-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="558bd-111">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-111">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="558bd-112">使用 .NET Framework 2.0 及更新版本中支援的回呼，延伸 `ICorProfilerCallback` 介面。</span><span class="sxs-lookup"><span data-stu-id="558bd-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="558bd-113">ICorProfilerCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-113">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="558bd-114">提供回呼方法，供 CLR 用於將連結及中斷連結的狀態資訊傳達給分析工具。</span><span class="sxs-lookup"><span data-stu-id="558bd-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="558bd-115">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-115">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="558bd-116">提供回呼方法，供 CLR 用於將資訊傳達給分析工具。</span><span class="sxs-lookup"><span data-stu-id="558bd-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="558bd-117">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-117">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="558bd-118">提供方法，以識別記憶體回收根目錄所參考之物件的可轉移關閉。</span><span class="sxs-lookup"><span data-stu-id="558bd-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="558bd-119">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-119">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="558bd-120">提供 CLR 用於通知分析工具組件正在載入中的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="558bd-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="558bd-121">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-121">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="558bd-122">提供一種回呼方法，讓通用語言執行時間用來通知分析工具，與記憶體中模組相關聯的符號資料流程已更新。</span><span class="sxs-lookup"><span data-stu-id="558bd-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="558bd-123">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="558bd-124">提供公用語言執行時間用來通知分析工具，動態方法的 JIT 編譯已開始和完成的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="558bd-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="558bd-125">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-125">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="558bd-126">提供一種回呼方法，讓通用語言執行時間用來通知分析工具，動態方法會進行垃圾收集，然後再卸載。</span><span class="sxs-lookup"><span data-stu-id="558bd-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="558bd-127">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-127">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="558bd-128">提供方法，讓程式碼分析工具能夠和 CLR 通訊，以控制 JIT 編譯器在重新編譯特定方法時，應如何產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="558bd-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="558bd-129">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-129">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="558bd-130">提供方法，以循序逐一查看 CLR 中的函式集合。</span><span class="sxs-lookup"><span data-stu-id="558bd-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="558bd-131">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="558bd-132">提供程式碼分析工具用於和 CLR 通訊以控制事件監視及要求資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="558bd-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="558bd-133">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-133">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="558bd-134">使用 .NET Framework 2.0 及更新版本中支援的方法，延伸 `ICorProfilerInfo` 介面。</span><span class="sxs-lookup"><span data-stu-id="558bd-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="558bd-135">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-135">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="558bd-136">`ICorProfilerInfo2`使用 .NET Framework 4 和更新版本中支援的方法來擴充介面。</span><span class="sxs-lookup"><span data-stu-id="558bd-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="558bd-137">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-137">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="558bd-138">提供程式碼分析工具用於和 CLR 通訊，以控制事件監視以及要求資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="558bd-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="558bd-139">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="558bd-140">提供程式碼分析工具用於和 CLR 通訊以控制事件監視的方法。</span><span class="sxs-lookup"><span data-stu-id="558bd-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="558bd-141">ICorProfilerInfo6 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-141">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="558bd-142">提供屬於給定 NGen 模組的所有方法的列舉值，並內嵌在指定方法的主體中。</span><span class="sxs-lookup"><span data-stu-id="558bd-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="558bd-143">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-143">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="558bd-144">提供方法，以將新定義的中繼資料套用至模組，並提供記憶體內部符號資料流程的存取權。</span><span class="sxs-lookup"><span data-stu-id="558bd-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="558bd-145">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-145">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="558bd-146">提供方法，以循序逐一查看由應用程式或分析工具所載入的模組集合。</span><span class="sxs-lookup"><span data-stu-id="558bd-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="558bd-147">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-147">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="558bd-148">提供方法，依序逐一查看由[ngen.exe （原生映射](../../tools/ngen-exe-native-image-generator.md)產生器）所產生的凍結物件集合。</span><span class="sxs-lookup"><span data-stu-id="558bd-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="558bd-149">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-149">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="558bd-150">提供方法，以循序逐一查看 CLR 中的執行緒集合。</span><span class="sxs-lookup"><span data-stu-id="558bd-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="558bd-151">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="558bd-151">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="558bd-152">提供配置[方法，](imethodmalloc-alloc-method.md)為新的 Microsoft 中繼語言（MSIL）函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="558bd-152">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="558bd-153">相關章節</span><span class="sxs-lookup"><span data-stu-id="558bd-153">Related Sections</span></span>  
 [<span data-ttu-id="558bd-154">分析概觀</span><span class="sxs-lookup"><span data-stu-id="558bd-154">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="558bd-155">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="558bd-155">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="558bd-156">分析列舉</span><span class="sxs-lookup"><span data-stu-id="558bd-156">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="558bd-157">分析結構</span><span class="sxs-lookup"><span data-stu-id="558bd-157">Profiling Structures</span></span>](profiling-structures.md)
