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
ms.openlocfilehash: f4d35179b8ae35c03370cc3798609d6ed430cde3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782859"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted 方法
通知分析工具對於先前使用 原生映像產生器 (NGen.exe) 所編譯的函式已開始搜尋。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in]正在執行搜尋函式的識別碼。  
  
 `pbUseCachedFunction`  
 [out]`true`如果執行引擎應該使用快取的版本的函式 （如果有的話），否則為`false`。 如果值為`false`，執行引擎的 JIT 編譯的函式，而不是使用不是 JIT 編譯的版本。  
  
## <a name="remarks"></a>備註  
 在.NET Framework 2.0 版中，`JITCachedFunctionSearchStarted`並[icorprofilercallback:: Jitcachedfunctionsearchfinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)回呼將不會進行一般的 NGen 影像中的所有函式。 只適用於設定檔的 NGen 映像會產生映像中的所有函式的回呼。 不過，由於額外的負荷，分析工具應該要求程式碼剖析工具最佳化 NGen 影像才想要使用這些回呼強制函式會編譯在 just-in-time (JIT)。 分析工具，否則為要使用延遲的策略用於蒐集函式資訊使用。  
  
 程式碼剖析工具必須支援多個執行緒的分析的應用程式會呼叫同時相同方法的情況。 例如，呼叫執行緒 A`JITCachedFunctionSearchStarted`和分析工具會藉由設定回應*pbUseCachedFunction*為 FALSE，以強制執行 JIT 編譯。 接著會呼叫的執行緒[icorprofilercallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)並[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)。  
  
 現在執行緒 B 呼叫`JITCachedFunctionSearchStarted`相同函式。 即使分析工具已宣稱其欲 JIT 編譯的函式，分析工具收到第二個回撥，因為執行緒 B 在執行緒 A 的呼叫已回應的程式碼剖析工具之前，會將傳送回呼`JITCachedFunctionSearchStarted`。 執行緒呼叫的順序取決於如何排程執行緒。  
  
 當分析工具收到重複的回呼時，它必須設定所參考的值`pbUseCachedFunction`相同的值為所有重複的回呼。 也就是說，當`JITCachedFunctionSearchStarted`多次呼叫相同`functionId`值，分析工具必須回應相同的每一次。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
