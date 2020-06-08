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
ms.openlocfilehash: d8f4a04abea0bd5eb9bf38629a8fcaf76479bcc9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500050"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted 方法
通知分析工具已開始使用原生映射產生器（Ngen.exe）編譯過的函式的搜尋。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>參數

- `functionId`

  \[in] 中執行搜尋的函式識別碼。

- `pbUseCachedFunction`

  \[out] `true` 如果執行引擎應該使用函數的快取版本（如果有的話），則為，否則為 `false` 。 如果值為 `false` ，則執行引擎會 JIT 編譯函式，而不是使用非 JIT 編譯的版本。

## <a name="remarks"></a>備註  
 在 .NET Framework 版本2.0 中，不會對 `JITCachedFunctionSearchStarted` 一般 NGen 影像中的所有函式進行和[ICorProfilerCallback：： JITCachedFunctionSearchFinished 方法](icorprofilercallback-jitcachedfunctionsearchfinished-method.md)回呼。 只有針對設定檔優化的 NGen 影像才會針對映射中的所有函式產生回呼。 不過，由於額外的負擔，分析工具應該只在想要使用這些回呼來強制編譯函式（JIT）時，才要求 profiler 優化的 NGen 影像。 否則，分析工具應該使用延遲策略來收集函數資訊。  
  
 分析工具必須支援已剖析應用程式的多個執行緒同時呼叫相同方法的情況。 例如，執行緒 A 會呼叫，而分析工具會藉 `JITCachedFunctionSearchStarted` 由將*pbUseCachedFunction*設定為 FALSE 來強制執行 JIT 編譯，來回應。 執行緒 A 接著會呼叫[ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)和[ICorProfilerCallback：： JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md)。  
  
 現在，執行緒 B 會呼叫相同函式 `JITCachedFunctionSearchStarted` 的。 即使分析工具已指出其對函式進行 JIT 編譯的意圖，分析工具還是會收到第二個回呼，因為執行緒 B 會在分析工具回應執行緒 A 的呼叫之前傳送回呼 `JITCachedFunctionSearchStarted` 。 執行緒進行呼叫的順序取決於執行緒的排程方式。  
  
 當 profiler 收到重複的回呼時，它必須將所參考的值設定 `pbUseCachedFunction` 為所有重複回呼的相同值。 也就是， `JITCachedFunctionSearchStarted` 使用相同的值呼叫多次時 `functionId` ，分析工具必須每次都會回應相同的情況。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
