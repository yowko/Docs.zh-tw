---
title: 分析全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 20ee2a9e045d839aa8ac043e035c438986b987ef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860862"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="a9a82-102">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-102">Profiling Global Static Functions</span></span>
<span data-ttu-id="a9a82-103">本節說明分析 API 所使用的非受控 API 函式。</span><span class="sxs-lookup"><span data-stu-id="a9a82-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9a82-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="a9a82-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="a9a82-105">.NET Framework 版本1分析函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-105">.NET Framework version 1 Profiling Functions</span></span>  
 [<span data-ttu-id="a9a82-106">FunctionEnter 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-106">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="a9a82-107">通知分析工具，控制項正在傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="a9a82-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="a9a82-108">在 .NET Framework 2.0 中被取代。</span><span class="sxs-lookup"><span data-stu-id="a9a82-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="a9a82-109">FunctionLeave 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-109">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="a9a82-110">通知分析工具，函式即將傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="a9a82-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="a9a82-111">在 .NET Framework 2.0 中被取代。</span><span class="sxs-lookup"><span data-stu-id="a9a82-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="a9a82-112">FunctionTailcall 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-112">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="a9a82-113">通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="a9a82-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="a9a82-114">在 .NET Framework 2.0 中被取代。</span><span class="sxs-lookup"><span data-stu-id="a9a82-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="a9a82-115">.NET Framework 版本2分析函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-115">.NET Framework version 2 Profiling Functions</span></span>  
 [<span data-ttu-id="a9a82-116">FunctionIDMapper 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-116">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="a9a82-117">通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於該函式的[FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和[FunctionTailcall2](functiontailcall2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="a9a82-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="a9a82-118">也可讓分析工具指出它是否想要接收該函式的回呼</span><span class="sxs-lookup"><span data-stu-id="a9a82-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="a9a82-119">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-119">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="a9a82-120">通知分析工具控制項正傳遞至函式，並提供堆疊框架和函式引數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a9a82-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="a9a82-121">在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="a9a82-121">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a9a82-122">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-122">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="a9a82-123">通知分析工具，函式即將傳回給呼叫端，並提供堆疊框架和函數傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a9a82-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="a9a82-124">在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="a9a82-124">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a9a82-125">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-125">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="a9a82-126">通知分析工具，目前正在執行的函式即將執行另一個函式的尾呼叫，並提供堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a9a82-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="a9a82-127">在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="a9a82-127">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a9a82-128">StackSnapshotCallback 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-128">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="a9a82-129">提供程式碼剖析工具，其中包含每個 managed 框架的相關資訊，以及堆疊階段期間每次在堆疊上執行的非受控框架，這是由[ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法起始。</span><span class="sxs-lookup"><span data-stu-id="a9a82-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="a9a82-130">.NET Framework 第4版程式碼剖析函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-130">.NET Framework version 4 Profiling Functions</span></span>  
 [<span data-ttu-id="a9a82-131">FunctionIDMapper2 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-131">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="a9a82-132">通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和[FunctionTailcall3](functiontailcall3-function.md)，或[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)回呼（針對該函數）。</span><span class="sxs-lookup"><span data-stu-id="a9a82-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="a9a82-133">也可讓分析工具指出它是否想要接收該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="a9a82-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="a9a82-134">`FunctionIDMapper2` 使用 `clientData` 參數擴充[FunctionIDMapper](functionidmapper-function.md)函式，而分析工具可能會使用它來區分執行時間。</span><span class="sxs-lookup"><span data-stu-id="a9a82-134">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="a9a82-135">FunctionEnter3 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-135">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="a9a82-136">通知分析工具，控制項正在傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="a9a82-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="a9a82-137">FunctionEnter3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-137">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="a9a82-138">通知分析工具控制項正傳遞至函式，並提供可傳遞給[ICorProfilerInfo3：： GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)的控制碼，以取得堆疊框架和函式引數。</span><span class="sxs-lookup"><span data-stu-id="a9a82-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="a9a82-139">FunctionLeave3 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-139">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="a9a82-140">通知分析工具，控制項是從函式傳回。</span><span class="sxs-lookup"><span data-stu-id="a9a82-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="a9a82-141">FunctionLeave3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-141">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="a9a82-142">通知分析工具，控制項是從函式傳回，並提供可傳遞至[ICorProfilerInfo3：： GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md)的控制碼，以取得堆疊框架和傳回值。</span><span class="sxs-lookup"><span data-stu-id="a9a82-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="a9a82-143">FunctionTailcall3 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-143">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="a9a82-144">通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="a9a82-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="a9a82-145">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="a9a82-145">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="a9a82-146">通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫，並提供可傳遞給[ICorProfilerInfo3：： GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md)以取得堆疊框架的控制碼。</span><span class="sxs-lookup"><span data-stu-id="a9a82-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a9a82-147">相關章節</span><span class="sxs-lookup"><span data-stu-id="a9a82-147">Related Sections</span></span>  
 [<span data-ttu-id="a9a82-148">分析概觀</span><span class="sxs-lookup"><span data-stu-id="a9a82-148">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="a9a82-149">分析介面</span><span class="sxs-lookup"><span data-stu-id="a9a82-149">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="a9a82-150">分析列舉</span><span class="sxs-lookup"><span data-stu-id="a9a82-150">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="a9a82-151">分析結構</span><span class="sxs-lookup"><span data-stu-id="a9a82-151">Profiling Structures</span></span>](profiling-structures.md)
