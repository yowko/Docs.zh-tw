---
title: ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136577"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法
[在 .NET Framework 4.7 和更新版本中支援]  
  
每當動態方法的 JIT 編譯完成時，就會通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>參數  
[輸入] `functionId`  
啟動 JIT 編譯之記憶體中函式的識別碼。   

[in] `hrStatus`   
值，指出 JIT 編譯是否成功。

[in] `fIsSafeToBlock`   
`true`，表示封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回;`false`，表示封鎖作業不會影響執行時間的作業。  

## <a name="remarks"></a>備註  

每當動態方法的 JIT 編譯完成時，就會觸發此回呼。 這包括各種 IL stub 和 LCG 方法。 其目標是要為 profiler 寫入器提供足夠的資訊，以向使用者識別已編譯的方法。

> [!NOTE]
> `functionId` 值無法用來解析其元資料標記，因為動態方法沒有中繼資料。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>請參閱

- [DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)
