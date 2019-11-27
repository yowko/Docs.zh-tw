---
title: 分析全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: d1d9b0a4c61ce7c3f8f9792046fb4bddf0fdfa05
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447441"
---
# <a name="profiling-global-static-functions"></a>分析全域靜態函式
本節說明分析 API 所使用的非受控 API 函式。  
  
## <a name="in-this-section"></a>本節內容  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET Framework 版本1分析函式  
 [FunctionEnter 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 通知分析工具，控制項正在傳遞至函式。 在 .NET Framework 2.0 中被取代。  
  
 [FunctionLeave 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 通知分析工具，函式即將傳回給呼叫者。 在 .NET Framework 2.0 中被取代。  
  
 [FunctionTailcall 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫。 在 .NET Framework 2.0 中被取代。  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET Framework 版本2分析函式  
 [FunctionIDMapper 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於該函式的[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)回呼。 也可讓分析工具指出它是否想要接收該函式的回呼  
  
 [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 通知分析工具控制項正傳遞至函式，並提供堆疊框架和函式引數的相關資訊。 在 .NET Framework 4 中已被取代。  
  
 [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 通知分析工具，函式即將傳回給呼叫端，並提供堆疊框架和函數傳回值的相關資訊。 在 .NET Framework 4 中已被取代。  
  
 [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 通知分析工具，目前正在執行的函式即將執行另一個函式的尾呼叫，並提供堆疊框架的相關資訊。 在 .NET Framework 4 中已被取代。  
  
 [StackSnapshotCallback 函式](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 提供程式碼剖析工具，其中包含每個 managed 框架的相關資訊，以及堆疊階段期間每次在堆疊上執行的非受控框架，這是由[ICorProfilerInfo2：:D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法起始。  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET Framework 第4版程式碼剖析函式  
 [FunctionIDMapper2 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)和[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)，或[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)回呼（針對該函數）。 也可讓分析工具指出它是否想要接收該函式的回呼。  
  
 `FunctionIDMapper2` 使用 `clientData` 參數擴充[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式，而分析工具可能會使用它來區分執行時間。  
  
 [FunctionEnter3 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 通知分析工具，控制項正在傳遞至函式。  
  
 [FunctionEnter3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 通知分析工具控制項正傳遞至函式，並提供可傳遞給[ICorProfilerInfo3：： GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)的控制碼，以取得堆疊框架和函式引數。  
  
 [FunctionLeave3 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 通知分析工具，控制項是從函式傳回。  
  
 [FunctionLeave3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 通知分析工具，控制項是從函式傳回，並提供可傳遞至[ICorProfilerInfo3：： GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)的控制碼，以取得堆疊框架和傳回值。  
  
 [FunctionTailcall3 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫。  
  
 [FunctionTailcall3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫，並提供可傳遞給[ICorProfilerInfo3：： GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)以取得堆疊框架的控制碼。  
  
## <a name="related-sections"></a>相關章節  
 [分析概觀](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
