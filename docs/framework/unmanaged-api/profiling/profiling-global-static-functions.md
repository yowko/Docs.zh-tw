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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461831"
---
# <a name="profiling-global-static-functions"></a>分析全域靜態函式
本節說明分析 API 所使用的 unmanaged 應用程式開發介面函式。  
  
## <a name="in-this-section"></a>本節內容  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET framework 第 1 版程式碼剖析函式  
 [FunctionEnter 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 通知分析工具控制會傳遞至函數。 .NET Framework 2.0 中被取代。  
  
 [FunctionLeave 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 通知分析工具函式是要傳回給呼叫者。 .NET Framework 2.0 中被取代。  
  
 [FunctionTailcall 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 通知分析工具目前執行函式即將執行對另一個函式的 tail 呼叫。 .NET Framework 2.0 中被取代。  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET framework 第 2 版程式碼剖析函式  
 [FunctionIDMapper 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 通知分析工具函式的指定的識別碼可能會重新對應至替代識別碼，以用於[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)， [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)，和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)該函式的回呼。 也可讓分析工具指出它是否要接收回撥，該函式  
  
 [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 控制項傳遞至函式，並提供堆疊的相關資訊框架和函式的引數，請通知分析工具。 中已被取代[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 函式傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊，請通知分析工具。 中已被取代[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 通知分析工具，目前執行函式即將執行對另一個函式的 tail 呼叫，並提供相關的堆疊框架資訊。 中已被取代[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  
  
 [StackSnapshotCallback 函式](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 提供程式碼剖析工具相關資訊每個 managed 的框架和每次執行未受管理的框架的堆疊上堆疊查核行程，由起始期間[icorprofilerinfo2:: Dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET framework 第 4 版程式碼剖析函式  
 [FunctionIDMapper2 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 通知分析工具函式的指定的識別碼可能會重新對應至替代識別碼，以用於[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)， [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)，和[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)，或[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)， [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)，和[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)該函式的回呼。 也可讓分析工具指出它是否要接收該函式的回呼。  
  
 `FunctionIDMapper2` 擴充[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式與`clientData`用分析工具可能用來區分執行階段的參數。  
  
 [FunctionEnter3 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 通知分析工具控制會傳遞至函數。  
  
 [FunctionEnter3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 通知分析工具，控制權會被傳遞給函式，並提供的控制代碼，可以傳遞至[icorprofilerinfo3:: Getfunctionenter3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)擷取的堆疊框架和函式引數。  
  
 [FunctionLeave3 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 通知分析工具會從函式傳回控制項。  
  
 [FunctionLeave3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 通知分析工具會傳回控制從函式，並提供的控制代碼，可以傳遞至[icorprofilerinfo3:: Getfunctionleave3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)擷取堆疊框架和傳回值。  
  
 [FunctionTailcall3 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 通知分析工具目前執行函式即將執行對另一個函式的 tail 呼叫。  
  
 [FunctionTailcall3WithInfo 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 通知分析工具目前執行函式即將執行 tail 呼叫另一個函式，並提供的控制代碼，可以傳遞至[icorprofilerinfo3:: Getfunctiontailcall3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)擷取堆疊框架。  
  
## <a name="related-sections"></a>相關章節  
 [分析概觀](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
