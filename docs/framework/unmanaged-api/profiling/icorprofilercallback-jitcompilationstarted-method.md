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
ms.openlocfilehash: 5eb881c8f024373fbff1dad17cd883ab6cafa2a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466630"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted 方法
通知分析工具在 just-in-time (JIT) 編譯器已開始編譯函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in]為其開始編譯函式的識別碼。  
  
 `fIsSafeToBlock`  
 [in]這個值表示是否封鎖的程式碼剖析工具，將會影響執行階段的作業。 值是`true`如果封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒，否則為`false`。  
  
 雖然值`true`將不會危害執行階段，它可能會扭曲分析的結果。  
  
## <a name="remarks"></a>備註  
 可接收的多個配對`JITCompilationStarted`並[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)會呼叫每個函式因為執行階段控制代碼類別建構函式。 比方說，在執行階段開始 JIT 編譯方法，但類別 B 的類別建構函式必須執行。 因此，執行階段 JIT 編譯類別 B 的建構函式，並執行它。 當建構函式執行時，會呼叫方法 A，這會導致方法一次是 JIT 編譯。 在此案例中，就會中止方法的第一次 JIT 編譯。 不過，這兩個 JIT 編譯方法的嘗試會報告與 JIT 編譯事件。 如果分析工具即將取代方法的 Microsoft intermediate language (MSIL) 程式碼，藉由呼叫[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法，它必須同時進行`JITCompilationStarted`事件，但它可能會使用相同的 MSIL 區塊兩者。  
  
 在其中兩個執行緒同時進行回呼的情況下，程式碼剖析工具必須支援 JIT 回呼的序列。 例如，呼叫執行緒 A `JITCompilationStarted`。 不過，在執行緒的呼叫之前`JITCompilationFinished`，執行緒 B 呼叫[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)函式識別碼從執行緒 A 的`JITCompilationStarted`回呼。 它可能會顯示該函式識別碼尚未有效期不應因為呼叫`JITCompilationFinished`有尚未收到的分析工具。 不過，在這種情況下，函式識別碼無效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
