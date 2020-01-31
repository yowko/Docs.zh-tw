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
ms.openlocfilehash: ad155c4efb9f11565eeed8bc0a3540311aca4eb7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866269"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished 方法
通知分析工具已完成先前使用原生映射產生器（Ngen.exe）編譯之函式的搜尋。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>參數

- `functionId`

  在中 \[] 執行搜尋的函式識別碼。

- `result`

  \[in] 表示搜尋結果之[COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md)列舉的值。

## <a name="remarks"></a>備註  
 在 .NET Framework 版本2.0 中，不會對一般 NGen 影像中的所有函式進行[ICorProfilerCallback：： JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md)和 `JITCachedFunctionSearchFinished` 回呼。 只有針對 profiler 優化的 NGen 影像才會針對影像中的所有函式產生回呼。 不過，由於額外的負擔，分析工具應該只在想要使用這些回呼來強制編譯函式（JIT）時，才要求 profiler 優化的 NGen 影像。 否則，分析工具應該使用延遲策略來收集函數資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
