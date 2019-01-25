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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a65de26f3fc088b292ec9f8a96ca4e503a17edd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680893"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted 方法
通知分析工具在 just-in-time (JIT) 編譯器已開始重新編譯函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]JIT 編譯器開始編譯函式的識別碼。  
  
 `rejitId`  
 [in]重新編譯函式的新版本的識別碼。  
  
 `fIsSafeToBlock`  
 [in]`true`表示封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒`false`表示封鎖會不會影響執行階段的作業。 值為`true`不會損害執行階段，但可能會影響分析結果。  
  
## <a name="remarks"></a>備註  
 可接收的多個配對`ReJITCompilationStarted`並[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)方法會呼叫每個函式因為執行階段控制代碼類別建構函式。 比方說，在執行階段開始重新編譯方法，但類別 B 的類別建構函式必須執行。 因此，執行階段會重新編譯類別 B 的建構函式，並執行它。 當建構函式執行時，它會讓方法 A，這會導致重新編譯方法的呼叫。 在此案例中，就會中止方法的第一次重新編譯。 不過，兩者會嘗試重新編譯是使用 JIT 重新編譯事件所報告的方法。  
  
 在其中兩個執行緒同時進行回呼的情況下，程式碼剖析工具必須支援 JIT 重新編譯回呼的序列。 例如，呼叫執行緒 A `ReJITCompilationStarted`; 不過，在執行緒的呼叫之前[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)，執行緒 B 呼叫[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)函式識別碼從`ReJITCompilationStarted`回呼執行緒 a。它可能會顯示該函式識別碼尚未有效期不應因為呼叫[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)有尚未收到的分析工具。 不過，在此情況下，函式識別碼無效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
