---
title: ICorProfilerCallback4::ReJITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: 81d11c87c9bc970dd5b5c9010023610cea7c0e72
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865190"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted 方法
通知 profiler，及時（JIT）編譯器已開始重新編譯函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 在JIT 編譯程式已開始重新編譯之函式的識別碼。  
  
 `rejitId`  
 在新版本函數的重新編譯識別碼。  
  
 `fIsSafeToBlock`  
 [in] `true`，表示封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回;`false`，表示封鎖作業不會影響執行時間的作業。 `true` 的值不會傷害執行時間，但可能會影響分析結果。  
  
## <a name="remarks"></a>備註  
 您可以針對每個函式接收一對以上的 `ReJITCompilationStarted` 和[ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)方法呼叫，因為執行時間會處理類別的方法。 例如，執行時間會開始重新編譯方法 A，但類別 B 的類別函式必須執行。 因此，執行時間會重新編譯類別 B 的函式，並加以執行。 當此函式正在執行時，它會呼叫方法 A，這會導致再次重新編譯方法 A。 在此案例中，第一次重新編譯方法 A 會停止。 不過，這兩次嘗試重新編譯方法 A 都會使用 JIT 重新編譯事件來回報。  
  
 分析工具在兩個執行緒同時進行回呼的情況下，必須支援 JIT 重新編譯回呼的順序。 例如，執行緒 A 會呼叫 `ReJITCompilationStarted`;不過，線上程 A 呼叫[ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)之前，執行緒 B 會呼叫[ICorProfilerCallback：： ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ，並從執行緒 a 的 `ReJITCompilationStarted` 回呼中取得函數識別碼。可能會出現函式識別碼尚未生效的情況，因為分析工具尚未收到[ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)的呼叫。 不過，在此情況下，函數識別碼是有效的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
- [JITCompilationFinished 方法](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished 方法](icorprofilercallback4-rejitcompilationfinished-method.md)
