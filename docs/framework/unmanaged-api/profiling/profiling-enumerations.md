---
title: 分析列舉
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868131"
---
# <a name="profiling-enumerations"></a>分析列舉
本節描述分析 API 所使用的 Unmanaged 列舉。  
  
## <a name="in-this-section"></a>本章節內容  
 [COR_PRF_CLAUSE_TYPE 列舉](cor-prf-clause-type-enumeration.md)  
 指出剛輸入或留下的程式碼的 exception 子句類型。  
  
 [COR_PRF_CODEGEN_FLAGS 列舉](cor-prf-codegen-flags-enumeration.md)  
 定義可使用[ICorProfilerFunctionControl：： SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)方法設定的程式碼產生旗標。  
  
 [COR_PRF_FINALIZER_FLAGS 列舉](cor-prf-finalizer-flags-enumeration.md)  
 描述物件的完成項。  
  
 [COR_PRF_GC_GENERATION 列舉](cor-prf-gc-generation-enumeration.md)  
 指出記憶體回收產生。  
  
 [COR_PRF_GC_REASON 列舉](cor-prf-gc-reason-enumeration.md)  
 指出正在發生之記憶體回收的原因。  
  
 [COR_PRF_GC_ROOT_FLAGS 列舉](cor-prf-gc-root-flags-enumeration.md)  
 指出記憶體回收行程根目錄的屬性。  
  
 [COR_PRF_GC_ROOT_KIND 列舉](cor-prf-gc-root-kind-enumeration.md)  
 表示[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)回呼所公開的垃圾收集行程根種類。  
  
 [COR_PRF_HIGH_MONITOR 列舉](cor-prf-high-monitor-enumeration.md)  
 除了在[ICorProfilerInfo5：： SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法載入時，分析工具可以指定的標記[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)以外，還提供旗標。  
  
 [COR_PRF_JIT_CACHE 列舉](cor-prf-jit-cache-enumeration.md)  
 指出快取的函式搜尋結果。  
  
 [COR_PRF_MISC 列舉](cor-prf-misc-enumeration.md)  
 包含指定特定識別項的常數值。  
  
 [COR_PRF_MODULE_FLAGS 列舉](cor-prf-module-flags-enumeration.md)  
 指定模組的屬性。  
  
 [COR_PRF_MONITOR 列舉](cor-prf-monitor-enumeration.md)  
 包含值，這些值用於指定分析工具想要訂閱的行為、功能或事件。  
  
 [COR_PRF_RUNTIME_TYPE 列舉](cor-prf-runtime-type-enumeration.md)  
 包含值，這些值指出 Common Language Runtime 的版本。  
  
 [COR_PRF_SNAPSHOT_INFO 列舉](cor-prf-snapshot-info-enumeration.md)  
 指定在每個分析工具的 `StackSnapshotCallback` 函式呼叫中，有多少資料要透過堆疊快照傳回。  
  
 [COR_PRF_STATIC_TYPE 列舉](cor-prf-static-type-enumeration.md)  
 指出欄位是否為靜態，若是靜態，則欄位套用的是靜態品質。  
  
 [COR_PRF_SUSPEND_REASON 列舉](cor-prf-suspend-reason-enumeration.md)  
 指出執行階段暫停的原因。  
  
 [COR_PRF_TRANSITION_REASON 列舉](cor-prf-transition-reason-enumeration.md)  
 指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。  
  
## <a name="related-sections"></a>相關章節  
 [分析概觀](profiling-overview.md)  
  
 [分析介面](profiling-interfaces.md)  
  
 [分析全域靜態函式](profiling-global-static-functions.md)  
  
 [分析結構](profiling-structures.md)
