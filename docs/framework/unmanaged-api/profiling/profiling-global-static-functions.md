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
ms.openlocfilehash: 3ea65c06871d9762fa6daac229a568594b4c4479
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457482"
---
# <a name="profiling-global-static-functions"></a>分析全域靜態函式
本節說明分析 API 所使用的 unmanaged 的 API 函式。  
  
## <a name="in-this-section"></a>本節內容  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET framework 第 1 版程式碼剖析函式  
 [FunctionEnter 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 通知分析工具的控制項傳遞至函式。 .NET Framework 2.0 中已被取代。  
  
 [FunctionLeave 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 通知分析工具函式會傳回給呼叫者。 .NET Framework 2.0 中已被取代。  
  
 [FunctionTailcall 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 通知分析工具目前正在執行的函式即將執行的另一個函式的 tail 呼叫。 .NET Framework 2.0 中已被取代。  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET framework 第 2 版程式碼剖析函式  
 [FunctionIDMapper 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 通知分析工具的函式指定的識別項可能會重新對應至替代識別碼，以用於[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)， [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)，和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)該函式的回呼。 也可讓分析工具指出它是否要接收回撥，該函式  
  
 [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 控制項已傳遞至函式，並提供資訊堆疊框架和函式的引數，請通知分析工具。 .NET Framework 4 中已被取代。  
  
 [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 函式傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊，請通知分析工具。 .NET Framework 4 中已被取代。  
  
 [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 通知分析工具，目前正在執行的函式執行至另一個函式的 tail 呼叫，並提供有關堆疊框架資訊。 .NET Framework 4 中已被取代。  
  
 [StackSnapshotCallback 函式](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 提供分析工具相關資訊每個 managed 的框架和每次執行的非受控框架在堆疊上堆疊查核行程，這起始期間[ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET framework 第 4 版程式碼剖析函式  
 [FunctionIDMapper2 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 通知分析工具的函式指定的識別項可能會重新對應至替代識別碼，以用於[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)， [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)，和[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)，或[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)， [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)，和[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)該函式的回呼。 也可讓分析工具指出它是否要接收回撥，該函式。  
  
 `FunctionIDMapper2` 擴充[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式搭配`clientData`參數，此程式碼剖析工具可用來區分執行階段參數。  
  
 [FunctionEnter3 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 通知分析工具的控制項傳遞至函式。  
  
 [FunctionEnter3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 通知分析工具的控制項傳遞至函式，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)來擷取堆疊框架和函式引數。  
  
 [FunctionLeave3 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 通知分析工具，從函式傳回控制項。  
  
 [FunctionLeave3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 通知分析工具，從函式，傳回控制項，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)擷取堆疊框架和傳回值。  
  
 [FunctionTailcall3 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 通知分析工具目前正在執行的函式即將執行的另一個函式的 tail 呼叫。  
  
 [FunctionTailcall3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 通知分析工具目前正在執行的函式即將執行結尾呼叫另一個函式，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)擷取堆疊框架。  
  
## <a name="related-sections"></a>相關章節  
 [分析概觀](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
