---
title: 分析全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 1b0ad42e6b34e99212e112f6a594b0a36b6715e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723073"
---
# <a name="profiling-global-static-functions"></a>分析全域靜態函式

本節說明分析 API 所使用的非受控 API 函式。  
  
## <a name="in-this-section"></a>本節內容  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET Framework 第1版程式碼剖析函式  

 [FunctionEnter 函式](functionenter-function.md)  
 通知分析工具，控制項正在傳遞至函式。 在 .NET Framework 2.0 中已淘汰。  
  
 [FunctionLeave 函式](functionleave-function.md)  
 通知分析工具，函式即將傳回到呼叫端。 在 .NET Framework 2.0 中已淘汰。  
  
 [FunctionTailcall 函式](functiontailcall-function.md)  
 通知分析工具，目前正在執行的函式即將執行另一個函式的 tail 呼叫。 在 .NET Framework 2.0 中已淘汰。  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET Framework 第2版程式碼剖析函式  

 [FunctionIDMapper 函式](functionidmapper-function.md)  
 通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於該函式的 [FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和 [FunctionTailcall2](functiontailcall2-function.md) 回呼中。 也可讓 profiler 指出是否要接收該函式的回呼  
  
 [FunctionEnter2 函式](functionenter2-function.md)  
 通知分析工具將控制權傳遞至函式，並提供堆疊框架和函式引數的相關資訊。 .NET Framework 4 中已淘汰。  
  
 [FunctionLeave2 函式](functionleave2-function.md)  
 通知分析工具，函式即將傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊。 .NET Framework 4 中已淘汰。  
  
 [FunctionTailcall2 函式](functiontailcall2-function.md)  
 通知分析工具，目前正在執行的函式即將執行另一個函式的 tail 呼叫，並提供堆疊框架的相關資訊。 .NET Framework 4 中已淘汰。  
  
 [StackSnapshotCallback 函式](stacksnapshotcallback-function.md)  
 提供分析工具，其中包含每個 managed 框架的相關資訊，以及堆疊逐步解說（由 [ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) 方法所起始）堆疊中每次執行的非受控框架。  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET Framework 第4版程式碼剖析函式  

 [FunctionIDMapper2 函式](functionidmapper2-function.md)  
 通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於 [FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和 [FunctionTailcall3](functiontailcall3-function.md)，或[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和 [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) 回呼。 也可讓 profiler 指出是否要接收該函式的回呼。  
  
 `FunctionIDMapper2` 使用參數擴充 [FunctionIDMapper](functionidmapper-function.md) 函式 `clientData` ，分析工具可能會使用這個參數來區分執行時間。  
  
 [FunctionEnter3 函式](functionenter3-function.md)  
 通知分析工具，控制項正在傳遞至函式。  
  
 [FunctionEnter3WithInfo 函式](functionenter3withinfo-function.md)  
 通知分析工具將控制權傳遞至函式，並提供可傳遞至 [ICorProfilerInfo3：： GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) 的控制碼，以取得堆疊框架和函式引數。  
  
 [FunctionLeave3 函式](functionleave3-function.md)  
 通知分析工具，從函數傳回控制項。  
  
 [FunctionLeave3WithInfo 函式](functionleave3withinfo-function.md)  
 通知分析工具正在從函式傳回控制權，並提供可傳遞至 [ICorProfilerInfo3：： GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) 的控制碼，以取得堆疊框架和傳回值。  
  
 [FunctionTailcall3 函式](functiontailcall3-function.md)  
 通知分析工具，目前正在執行的函式即將執行另一個函式的 tail 呼叫。  
  
 [FunctionTailcall3WithInfo 函式](functiontailcall3withinfo-function.md)  
 通知分析工具，目前正在執行的函式即將執行另一個函式的 tail 呼叫，並提供可傳遞至 [ICorProfilerInfo3：： GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) 的控制碼，以取得堆疊框架。  
  
## <a name="related-sections"></a>相關章節  

 [分析概觀](profiling-overview.md)  
  
 [分析介面](profiling-interfaces.md)  
  
 [分析列舉](profiling-enumerations.md)  
  
 [分析結構](profiling-structures.md)
