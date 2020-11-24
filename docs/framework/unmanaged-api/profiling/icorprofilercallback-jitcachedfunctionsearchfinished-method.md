---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: fe07270989df897c3dbf689305784f9f0af65742
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684040"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished 方法

通知分析工具，在先前使用原生映射產生器 ( # A0) 編譯的函式已完成搜尋。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>參數

- `functionId`

  \[in] 執行搜尋的函式識別碼。

- `result`

  \[in] [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) 列舉的值，表示搜尋的結果。

## <a name="remarks"></a>備註  

 在 .NET Framework 2.0 版中，不會對一般 NGen 影像中的所有函式進行 [ICorProfilerCallback：： JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) 和 `JITCachedFunctionSearchFinished` 回呼。 只有針對分析工具優化的 NGen 映射才會產生影像中所有函式的回呼。 不過，由於額外的額外負荷，分析工具應該只在想要使用這些回呼來強制將函式編譯為即時 (JIT) 時，才要求 profiler 優化的 NGen 映射。 否則，分析工具應該使用延遲策略來收集函數資訊。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
