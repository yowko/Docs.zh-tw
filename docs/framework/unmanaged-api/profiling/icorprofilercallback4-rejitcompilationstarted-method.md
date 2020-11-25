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
ms.openlocfilehash: 43db4ce0ba7a95a029e6c4928f55a99df9085164
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730249"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted 方法

通知分析工具，及時 (JIT) 編譯器已開始重新編譯函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>參數  

 `functionId`  
 在JIT 編譯程式已開始重新編譯的函式識別碼。  
  
 `rejitId`  
 在新版本函數的重新編譯識別碼。  
  
 `fIsSafeToBlock`  
 [in] `true` 若要指出封鎖可能會導致執行時間等候呼叫執行緒從此回呼傳回; `false` 表示封鎖不會影響執行時間的操作。 的值 `true` 不會危害執行時間，但可能會影響分析結果。  
  
## <a name="remarks"></a>備註  

 您可以針對每個函式接收一對以上的 `ReJITCompilationStarted` [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) 方法呼叫，因為執行時間處理類別的函式的方式。 例如，執行時間會開始重新編譯方法 A，但必須執行類別 B 的類別函式。 因此，執行時間會重新編譯類別 B 的函式並加以執行。 當此函式正在執行時，它會呼叫方法 A，這會導致重新編譯方法 A。 在此案例中，第一次重新編譯方法 A 會暫停。 不過，這兩個嘗試重新編譯方法 A 都會以 JIT 重新編譯事件來回報。  
  
 當兩個執行緒同時進行回呼時，分析工具必須支援 JIT 重新編譯回呼的順序。 例如，執行緒 A 呼叫， `ReJITCompilationStarted` 但是線上程 a 呼叫 [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)之前，執行緒 B 會使用執行緒 A 的回呼中的函式識別碼來呼叫 [ICorProfilerCallback：： ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) `ReJITCompilationStarted` 。這可能會出現，因為分析工具尚未收到 [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) 的呼叫，所以函式識別碼應該尚未有效。 不過，在此情況下，函數識別碼是有效的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
- [JITCompilationFinished 方法](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished 方法](icorprofilercallback4-rejitcompilationfinished-method.md)
