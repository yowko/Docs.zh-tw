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
ms.openlocfilehash: 938da4e3b7cc45c24dcac872ab504755116197a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684001"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted 方法

通知分析工具，已開始針對先前使用原生映射產生器 ( # A0) 編譯的函式進行搜尋。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>參數

- `functionId`

  \[in] 正在執行搜尋的函式識別碼。

- `pbUseCachedFunction`

  \[out] `true` 如果執行引擎應使用函式的快取版本 (if 可用) ，則為，否則為 `false` 。 如果值為 `false` ，執行引擎會 JIT 編譯函式，而不是使用非 JIT 編譯的版本。

## <a name="remarks"></a>備註  

 在 .NET Framework 2.0 版中，不會對 `JITCachedFunctionSearchStarted` 一般 NGen 影像中的所有函數進行和 [ICorProfilerCallback：： JITCachedFunctionSearchFinished 方法](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) 回呼。 只有針對設定檔優化的 NGen 映射才會產生映射中所有函式的回呼。 不過，由於額外的額外負荷，分析工具應該只在想要使用這些回呼來強制將函式編譯為即時 (JIT) 時，才要求 profiler 優化的 NGen 映射。 否則，分析工具應該使用延遲策略來收集函數資訊。  
  
 分析工具必須支援已分析之應用程式的多個執行緒同時呼叫相同方法的情況。 例如，執行緒 A 呼叫，而分析工具會 `JITCachedFunctionSearchStarted` 將 *pbUseCachedFunction* 設定為 FALSE 以強制 JIT 編譯，以進行回應。 執行緒 A 接著會呼叫 [ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) 和 [ICorProfilerCallback：： JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md)。  
  
 現線上程 B 會呼叫相同的函式 `JITCachedFunctionSearchStarted` 。 雖然分析工具已陳述了函式的 JIT 編譯意圖，但分析工具會收到第二個回呼，因為執行緒 B 會在分析工具回應執行緒 A 的呼叫之前傳送回呼 `JITCachedFunctionSearchStarted` 。 執行緒進行呼叫的順序取決於執行緒的排程方式。  
  
 當分析工具接收重複的回呼時，它必須針對所有重複的回呼，將所參考的值設定 `pbUseCachedFunction` 為相同的值。 也就是說，當 `JITCachedFunctionSearchStarted` 使用相同的值呼叫多次時，分析工具 `functionId` 必須每次都有相同的回應。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
