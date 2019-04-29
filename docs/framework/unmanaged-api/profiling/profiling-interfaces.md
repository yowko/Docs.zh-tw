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
# <a name="profiling-interfaces"></a>分析介面
本節說明 Unmanaged 介面，這類介面可讓您分析由 Common Language Runtime (CLR) 所執行的程式。  
  
## <a name="in-this-section"></a>本節內容  
 [ICLRProfiling 介面](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 提供[AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法，可讓分析工具附加至正在執行的處理序。  
  
 [ICorProfilerAssemblyReferenceProvider 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 可讓分析工具通知分析工具會在加入的組件參考的 CLR [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。  
  
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
 提供回呼方法，common language runtime 用來通知分析工具會更新記憶體中模組相關聯的符號資料流。  

[ICorProfilerCallback8 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
提供 common language runtime 用來通知分析工具中的動態方法的 JIT 編譯已啟動並完成的回呼方法。

[ICorProfilerCallback9 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
提供 common language runtime 用於通知的動態方法在記憶體回收，並接著卸載分析工具回呼方法。

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
 請提供隸屬於指定的 NGen 模組，以及屬於指定的方法主體中內嵌的所有方法的列舉值。  
  
 [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 提供方法，以套用新定義模組的中繼資料，並提供存取記憶體中的符號資料流。  
  
 [ICorProfilerModuleEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 提供方法，以循序逐一查看由應用程式或分析工具所載入的模組集合。  
  
 [ICorProfilerObjectEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 提供方法，以循序逐一查看所產生的凍結物件的集合[Ngen.exe （原生映像產生器）](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)。  
  
 [ICorProfilerThreadEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 提供方法，以循序逐一查看 CLR 中的執行緒集合。  
  
 [IMethodMalloc 介面](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 提供[Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)配置記憶體給新的 Microsoft intermediate language (MSIL) 函式主體的方法。  
  
## <a name="related-sections"></a>相關章節  
 [分析概觀](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
