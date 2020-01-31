---
title: 分析介面
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: 8b6b9acff2945e2d8fd684bfa31e4af086ea5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868144"
---
# <a name="profiling-interfaces"></a>分析介面
本節說明 Unmanaged 介面，這類介面可讓您分析由 Common Language Runtime (CLR) 所執行的程式。  
  
## <a name="in-this-section"></a>本章節內容  
 [ICLRProfiling 介面](iclrprofiling-interface.md)  
 提供[AttachProfiler](iclrprofiling-attachprofiler-method.md)方法，可讓 profiler 附加至執行中的進程。  
  
 [ICorProfilerAssemblyReferenceProvider 介面](icorprofilerassemblyreferenceprovider-interface.md)  
 可讓分析工具通知元件參考的 CLR，而分析工具將會在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼中新增此檔案。  
  
 [ICorProfilerCallback 介面](icorprofilercallback-interface.md)  
 提供讓 CLR 在分析工具已訂閱的事件發生時，通知程式碼分析工具的方法。  
  
 [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)  
 使用 .NET Framework 2.0 及更新版本中支援的回呼，延伸 `ICorProfilerCallback` 介面。  
  
 [ICorProfilerCallback3 介面](icorprofilercallback3-interface.md)  
 提供回呼方法，供 CLR 用於將連結及中斷連結的狀態資訊傳達給分析工具。  
  
 [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)  
 提供回呼方法，供 CLR 用於將資訊傳達給分析工具。  
  
 [ICorProfilerCallback5 介面](icorprofilercallback5-interface.md)  
 提供方法，以識別記憶體回收根目錄所參考之物件的可轉移關閉。  
  
 [ICorProfilerCallback6 介面](icorprofilercallback6-interface.md)  
 提供 CLR 用於通知分析工具組件正在載入中的回呼方法。  
  
 [ICorProfilerCallback7 介面](icorprofilercallback7-interface.md)  
 提供一種回呼方法，讓通用語言執行時間用來通知分析工具，與記憶體中模組相關聯的符號資料流程已更新。  

[ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)  
提供公用語言執行時間用來通知分析工具，動態方法的 JIT 編譯已開始和完成的回呼方法。

[ICorProfilerCallback9 介面](icorprofilercallback9-interface.md)  
提供一種回呼方法，讓通用語言執行時間用來通知分析工具，動態方法會進行垃圾收集，然後再卸載。

 [ICorProfilerFunctionControl 介面](icorprofilerfunctioncontrol-interface.md)  
 提供方法，讓程式碼分析工具能夠和 CLR 通訊，以控制 JIT 編譯器在重新編譯特定方法時，應如何產生程式碼。  
  
 [ICorProfilerFunctionEnum 介面](icorprofilerfunctionenum-interface.md)  
 提供方法，以循序逐一查看 CLR 中的函式集合。  
  
 [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)  
 提供程式碼分析工具用於和 CLR 通訊以控制事件監視及要求資訊的方法。  
  
 [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)  
 使用 .NET Framework 2.0 及更新版本中支援的方法，延伸 `ICorProfilerInfo` 介面。  
  
 [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)  
 使用 .NET Framework 4 和更新版本中支援的方法來擴充 `ICorProfilerInfo2` 介面。  
  
 [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)  
 提供程式碼分析工具用於和 CLR 通訊，以控制事件監視以及要求資訊的方法。  
  
 [ICorProfilerInfo5 介面](icorprofilerinfo5-interface.md)  
 提供程式碼分析工具用於和 CLR 通訊以控制事件監視的方法。  
  
 [ICorProfilerInfo6 介面](icorprofilerinfo6-interface.md)  
 提供屬於給定 NGen 模組的所有方法的列舉值，並內嵌在指定方法的主體中。  
  
 [ICorProfilerInfo7 介面](icorprofilerinfo7-interface.md)  
 提供方法，以將新定義的中繼資料套用至模組，並提供記憶體內部符號資料流程的存取權。  
  
 [ICorProfilerModuleEnum 介面](icorprofilermoduleenum-interface.md)  
 提供方法，以循序逐一查看由應用程式或分析工具所載入的模組集合。  
  
 [ICorProfilerObjectEnum 介面](icorprofilerobjectenum-interface.md)  
 提供方法，依序逐一查看由[ngen.exe （原生映射](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)產生器）所產生的凍結物件集合。  
  
 [ICorProfilerThreadEnum 介面](icorprofilerthreadenum-interface.md)  
 提供方法，以循序逐一查看 CLR 中的執行緒集合。  
  
 [IMethodMalloc 介面](imethodmalloc-interface.md)  
 提供配置[方法，](imethodmalloc-alloc-method.md)為新的 Microsoft 中繼語言（MSIL）函式主體配置記憶體。  
  
## <a name="related-sections"></a>相關章節  
 [分析概觀](profiling-overview.md)  
  
 [分析全域靜態函式](profiling-global-static-functions.md)  
  
 [分析列舉](profiling-enumerations.md)  
  
 [分析結構](profiling-structures.md)
