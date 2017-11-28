---
title: "分析列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e0b539c8e455040cc97f37f75476b0efe796abb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-enumerations"></a>分析列舉
本節描述分析 API 所使用的 Unmanaged 列舉。  
  
## <a name="in-this-section"></a>本章節內容  
 [COR_PRF_CLAUSE_TYPE 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 指出剛輸入或留下的程式碼的 exception 子句類型。  
  
 [COR_PRF_CODEGEN_FLAGS 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 定義的程式碼產生旗標可以設定的[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)方法。  
  
 [COR_PRF_FINALIZER_FLAGS 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 描述物件的完成項。  
  
 [COR_PRF_GC_GENERATION 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 指出記憶體回收產生。  
  
 [COR_PRF_GC_REASON 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 指出正在發生之記憶體回收的原因。  
  
 [COR_PRF_GC_ROOT_FLAGS 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 指出記憶體回收行程根目錄的屬性。  
  
 [COR_PRF_GC_ROOT_KIND 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 表示記憶體回收行程根目錄所公開的種類[icorprofilercallback2:: Rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)回呼。  
  
 [COR_PRF_HIGH_MONITOR 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 提供除了中找到的旗標[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別，可以指定程式碼剖析工具[icorprofilerinfo5:: Seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法在載入時。  
  
 [COR_PRF_JIT_CACHE 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 指出快取的函式搜尋結果。  
  
 [COR_PRF_MISC 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 包含指定特定識別項的常數值。  
  
 [COR_PRF_MODULE_FLAGS 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 指定模組的屬性。  
  
 [COR_PRF_MONITOR 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 包含值，這些值用於指定分析工具想要訂閱的行為、功能或事件。  
  
 [COR_PRF_RUNTIME_TYPE 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 包含值，這些值指出 Common Language Runtime 的版本。  
  
 [COR_PRF_SNAPSHOT_INFO 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 指定在每個分析工具的 `StackSnapshotCallback` 函式呼叫中，有多少資料要透過堆疊快照傳回。  
  
 [COR_PRF_STATIC_TYPE 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 指出欄位是否為靜態，若是靜態，則欄位套用的是靜態品質。  
  
 [COR_PRF_SUSPEND_REASON 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 指出執行階段暫停的原因。  
  
 [COR_PRF_TRANSITION_REASON 列舉](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。  
  
## <a name="related-sections"></a>相關章節  
 [程式碼剖析概觀](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
