---
title: "分析介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a>分析介面
本節說明 Unmanaged 介面，這類介面可讓您分析由 Common Language Runtime (CLR) 所執行的程式。  
  
## <a name="in-this-section"></a>本章節內容  
 [ICLRProfiling 介面](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 提供[AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法，可讓分析工具附加至正在執行的處理序。  
  
 [ICorProfilerAssemblyReferenceProvider 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 可讓分析工具通知分析工具會在中加入的組件參考的 CLR [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。  
  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 提供讓 CLR 在分析工具已訂閱的事件發生時，通知程式碼分析工具的方法。  
  
 [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 使用 .NET Framework 2.0 及更新版本中支援的回呼，延伸 `ICorProfilerCallback` 介面。  
  
 [ICorProfilerCallback3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 提供回呼方法，供 CLR 用於將連結及中斷連結的狀態資訊傳達給分析工具。  
  
 [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 提供回呼方法，供 CLR 用於將資訊傳達給分析工具。  
  
 [ICorProfilerCallback5 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 提供方法，以識別記憶體回收根目錄所參考之物件的可轉移關閉。  
  
 [ICorProfilerCallback6 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 提供 CLR 用於通知分析工具組件正在載入中的回呼方法。  
  
 [ICorProfilerCallback7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 提供 common language runtime 用於通知分析工具會更新記憶體中模組相關聯的符號資料流的回呼方法。  
  
 [ICorProfilerFunctionControl 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 提供方法，讓程式碼分析工具能夠和 CLR 通訊，以控制 JIT 編譯器在重新編譯特定方法時，應如何產生程式碼。  
  
 [ICorProfilerFunctionEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 提供方法，以循序逐一查看 CLR 中的函式集合。  
  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 提供程式碼分析工具用於和 CLR 通訊以控制事件監視及要求資訊的方法。  
  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 使用 .NET Framework 2.0 及更新版本中支援的方法，延伸 `ICorProfilerInfo` 介面。  
  
 [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 使用 `ICorProfilerInfo2` 及更新版本中支援的方法，延伸 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 介面。  
  
 [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 提供程式碼分析工具用於和 CLR 通訊，以控制事件監視以及要求資訊的方法。  
  
 [ICorProfilerInfo5 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 提供程式碼分析工具用於和 CLR 通訊以控制事件監視的方法。  
  
 [ICorProfilerInfo6 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 請提供隸屬於給定的 NGen 模組，以及屬於給定方法主體中內嵌的所有方法的列舉值。  
  
 [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 提供方法，以套用新定義的中繼資料至模組，以及提供存取記憶體中的符號資料流。  
  
 [ICorProfilerModuleEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 提供方法，以循序逐一查看由應用程式或分析工具所載入的模組集合。  
  
 [ICorProfilerObjectEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 提供方法，以循序逐一查看所產生的已凍結物件的集合[Ngen.exe （原生映像產生器）](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)。  
  
 [ICorProfilerThreadEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 提供方法，以循序逐一查看 CLR 中的執行緒集合。  
  
 [IMethodMalloc 介面](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 提供[配置](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)方法來為新的 Microsoft intermediate language (MSIL) 函式主體配置記憶體。  
  
## <a name="related-sections"></a>相關章節  
 [程式碼剖析概觀](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
