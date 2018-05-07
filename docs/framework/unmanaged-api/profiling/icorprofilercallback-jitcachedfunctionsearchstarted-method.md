---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d97b40412b6999000a601b72904a03edf2acd08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted 方法
通知分析工具已用於先前使用原生映像產生器 (NGen.exe) 所編譯的函式中開始搜尋。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]正在執行搜尋函式的識別碼。  
  
 `pbUseCachedFunction`  
 [out]`true`如果執行引擎應該使用快取的版本的函式 （如果有的話），否則為`false`。 如果值為`false`，執行引擎 JIT 編譯的函式，而不是使用不是 JIT 編譯的版本。  
  
## <a name="remarks"></a>備註  
 在.NET Framework 2.0 版中，`JITCachedFunctionSearchStarted`和[icorprofilercallback:: Jitcachedfunctionsearchfinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)回呼將不會進行一般 NGen 映像中的所有函式。 只最佳化的設定檔的 NGen 映像將映像中產生的所有函式的回呼。 不過，額外負擔，因為分析工具應該要求程式碼剖析工具最佳化 NGen 影像才想要使用這些回呼強制將函式編譯在 just-in-time (JIT)。 否則，分析工具應該收集的資訊函式使用延遲的策略。  
  
 程式碼剖析工具必須支援分析的應用程式的多個執行緒會呼叫同時相同方法的情況。 例如，執行緒的呼叫`JITCachedFunctionSearchStarted`和分析工具會藉由設定回應*pbUseCachedFunction*為 FALSE，以強制執行 JIT 編譯。 然後會呼叫的執行緒[icorprofilercallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)和[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)。  
  
 現在執行緒 B 呼叫`JITCachedFunctionSearchStarted`相同的函式。 即使分析工具有另外註明其進行 JIT 編譯函式的目的，分析工具收到第二個回呼，因為執行緒 B 在分析工具已經回應執行緒的呼叫之前，會將傳送回呼`JITCachedFunctionSearchStarted`。 執行緒的呼叫順序取決於執行緒的排程。  
  
 當分析工具收到重複的回撥時，它必須設定所參考的值`pbUseCachedFunction`為相同的值為所有重複的回呼。 也就是說，當`JITCachedFunctionSearchStarted`多次呼叫具有相同`functionId`值，分析工具必須回應相同的每一次。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
