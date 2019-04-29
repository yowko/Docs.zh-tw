---
title: 分析全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bb5d93c91de857ebbee63009cad73fba7e1d284
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758245"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="fa469-102">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="fa469-102">Profiling Global Static Functions</span></span>
<span data-ttu-id="fa469-103">本節說明分析 API 所使用的 unmanaged 的 API 函式。</span><span class="sxs-lookup"><span data-stu-id="fa469-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa469-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="fa469-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="fa469-105">.NET framework 第 1 版程式碼剖析函式</span><span class="sxs-lookup"><span data-stu-id="fa469-105">.NET Framework version 1 Profiling Functions</span></span>  
 [<span data-ttu-id="fa469-106">FunctionEnter 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-106">FunctionEnter Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 <span data-ttu-id="fa469-107">通知分析工具的控制項傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="fa469-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="fa469-108">.NET Framework 2.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="fa469-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="fa469-109">FunctionLeave 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-109">FunctionLeave Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 <span data-ttu-id="fa469-110">通知分析工具函式會傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="fa469-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="fa469-111">.NET Framework 2.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="fa469-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="fa469-112">FunctionTailcall 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-112">FunctionTailcall Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 <span data-ttu-id="fa469-113">通知分析工具目前正在執行的函式即將執行的另一個函式的 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="fa469-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="fa469-114">.NET Framework 2.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="fa469-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="fa469-115">.NET framework 第 2 版程式碼剖析函式</span><span class="sxs-lookup"><span data-stu-id="fa469-115">.NET Framework version 2 Profiling Functions</span></span>  
 [<span data-ttu-id="fa469-116">FunctionIDMapper 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-116">FunctionIDMapper Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 <span data-ttu-id="fa469-117">通知分析工具的函式指定的識別項可能會重新對應至替代識別碼，以用於[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)， [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)，和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="fa469-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="fa469-118">也可讓分析工具指出它是否要接收回撥，該函式</span><span class="sxs-lookup"><span data-stu-id="fa469-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="fa469-119">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-119">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 <span data-ttu-id="fa469-120">控制項已傳遞至函式，並提供資訊堆疊框架和函式的引數，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="fa469-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="fa469-121">中已被取代[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fa469-121">Deprecated in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="fa469-122">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-122">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 <span data-ttu-id="fa469-123">函式傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="fa469-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="fa469-124">中已被取代[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fa469-124">Deprecated in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="fa469-125">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-125">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 <span data-ttu-id="fa469-126">通知分析工具，目前正在執行的函式執行至另一個函式的 tail 呼叫，並提供有關堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="fa469-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="fa469-127">中已被取代[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fa469-127">Deprecated in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="fa469-128">StackSnapshotCallback 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-128">StackSnapshotCallback Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 <span data-ttu-id="fa469-129">提供分析工具相關資訊每個 managed 的框架和每次執行的非受控框架在堆疊上堆疊查核行程，這起始期間[ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fa469-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="fa469-130">.NET framework 第 4 版程式碼剖析函式</span><span class="sxs-lookup"><span data-stu-id="fa469-130">.NET Framework version 4 Profiling Functions</span></span>  
 [<span data-ttu-id="fa469-131">FunctionIDMapper2 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-131">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 <span data-ttu-id="fa469-132">通知分析工具的函式指定的識別項可能會重新對應至替代識別碼，以用於[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)， [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)，和[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)，或[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)， [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)，和[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="fa469-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="fa469-133">也可讓分析工具指出它是否要接收回撥，該函式。</span><span class="sxs-lookup"><span data-stu-id="fa469-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="fa469-134">`FunctionIDMapper2` 擴充[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式搭配`clientData`參數，此程式碼剖析工具可用來區分執行階段參數。</span><span class="sxs-lookup"><span data-stu-id="fa469-134">`FunctionIDMapper2` extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="fa469-135">FunctionEnter3 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-135">FunctionEnter3 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 <span data-ttu-id="fa469-136">通知分析工具的控制項傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="fa469-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="fa469-137">FunctionEnter3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-137">FunctionEnter3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 <span data-ttu-id="fa469-138">通知分析工具的控制項傳遞至函式，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)來擷取堆疊框架和函式引數。</span><span class="sxs-lookup"><span data-stu-id="fa469-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="fa469-139">FunctionLeave3 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-139">FunctionLeave3 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 <span data-ttu-id="fa469-140">通知分析工具，從函式傳回控制項。</span><span class="sxs-lookup"><span data-stu-id="fa469-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="fa469-141">FunctionLeave3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-141">FunctionLeave3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 <span data-ttu-id="fa469-142">通知分析工具，從函式，傳回控制項，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)擷取堆疊框架和傳回值。</span><span class="sxs-lookup"><span data-stu-id="fa469-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="fa469-143">FunctionTailcall3 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-143">FunctionTailcall3 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 <span data-ttu-id="fa469-144">通知分析工具目前正在執行的函式即將執行的另一個函式的 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="fa469-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="fa469-145">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="fa469-145">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 <span data-ttu-id="fa469-146">通知分析工具目前正在執行的函式即將執行結尾呼叫另一個函式，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)擷取堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="fa469-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fa469-147">相關章節</span><span class="sxs-lookup"><span data-stu-id="fa469-147">Related Sections</span></span>  
 [<span data-ttu-id="fa469-148">分析概觀</span><span class="sxs-lookup"><span data-stu-id="fa469-148">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="fa469-149">分析介面</span><span class="sxs-lookup"><span data-stu-id="fa469-149">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="fa469-150">分析列舉</span><span class="sxs-lookup"><span data-stu-id="fa469-150">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="fa469-151">分析結構</span><span class="sxs-lookup"><span data-stu-id="fa469-151">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
