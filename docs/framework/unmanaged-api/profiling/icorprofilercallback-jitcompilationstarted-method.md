---
title: ICorProfilerCallback::JITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fa1081afc77c8116d8858c187401555409b4dcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted 方法
通知分析工具在 just-in-time (JIT) 編譯器已開始編譯函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]編譯正在啟動的函式的識別碼。  
  
 `fIsSafeToBlock`  
 [in]值，指出程式碼剖析工具來封鎖是否會影響執行階段的作業。 值是`true`如果封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候否則`false`。  
  
 雖然值`true`將不會危害到執行階段，則會扭曲分析的結果。  
  
## <a name="remarks"></a>備註  
 很可能會收到一對以上的`JITCompilationStarted`和[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)呼叫每個函式因為執行階段控制代碼類別建構函式。 比方說，執行階段開始 JIT 編譯方法，但類別 B 的類別建構函式必須在執行。 因此，執行階段 JIT 編譯類別 B 的建構函式，並執行它。 建構函式執行時，會呼叫方法 A，這會導致方法 A JIT 編譯一次。 在此案例中，就會中止方法 A 的第一次的 JIT 編譯。 不過，這兩個 JIT 編譯方法的嘗試都會回報與 JIT 編譯事件。 如果要藉由呼叫取代方法的 Microsoft intermediate language (MSIL) 程式碼分析工具[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法，它必須同時執行`JITCompilationStarted`事件，但它可能會使用相同的 MSIL 區塊兩者。  
  
 程式碼剖析工具必須在其中兩個執行緒同時進行回呼的情況下支援 JIT 回呼的序列。 例如，執行緒的呼叫`JITCompilationStarted`。 不過，執行緒的呼叫之前`JITCompilationFinished`，執行緒 B 呼叫[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)函式識別碼從執行緒 A 的`JITCompilationStarted`回呼。 它可能會顯示該函式 ID 尚未有效期不應因為呼叫`JITCompilationFinished`有尚未收到分析工具。 不過，在這類情況下，函式識別碼無效。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [JITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
