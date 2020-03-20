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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177086"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted 方法
通知探測器及時 （JIT） 編譯器已開始重新編譯函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [在]JIT 編譯器已開始重新編譯的函數的 ID。  
  
 `rejitId`  
 [在]函數的新版本的重新編譯 ID。  
  
 `fIsSafeToBlock`  
 [在]`true`指示阻塞可能導致運行時等待調用執行緒從此回檔返回;`false`指示阻塞不會影響運行時的操作。 值`true`不會損害運行時，但可能會影響分析結果。  
  
## <a name="remarks"></a>備註  
 由於運行時處理類建構函式的方式，可以為每個`ReJITCompilationStarted`函數接收多對和[ReJIT 編譯完成](icorprofilercallback4-rejitcompilationfinished-method.md)方法調用。 例如，運行時開始重新編譯方法 A，但需要運行類 B 的類建構函式。 因此，運行時重新編譯類 B 的建構函式並運行它。 當建構函式運行時，它會調用方法 A，這將導致方法 A 再次重新編譯。 在這種情況下，方法 A 的第一次重新編譯將停止。 但是，使用 JIT 重新編譯附隨報告重新編譯方法 A 的嘗試。  
  
 在兩個執行緒同時進行回檔的情況下，探測器必須支援 JIT 重新編譯回檔的順序。 例如，執行緒 A`ReJITCompilationStarted`調用 ;但是，線上程 A 調用[ReJIT 編譯完成](icorprofilercallback4-rejitcompilationfinished-method.md)之前，執行緒 B 調用[ICorProfiler 回檔：：異常搜索功能Enter](icorprofilercallback-exceptionsearchfunctionenter-method.md)與執行緒 A 回檔中的`ReJITCompilationStarted`函數 ID。似乎函數 ID 尚未有效，因為探測器尚未收到對[ReJIT 編譯完成的](icorprofilercallback4-rejitcompilationfinished-method.md)調用。 但是，在這種情況下，函數 ID 有效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
- [JITCompilationFinished 方法](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished 方法](icorprofilercallback4-rejitcompilationfinished-method.md)
