---
title: ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a4c434c5d458602db8a4d582b239d6e57def6ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498995"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法
[在 .NET Framework 4.7 和更新版本中支援]  
  
每當動態方法的 JIT 編譯開始時，就會通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a>參數  
[in] `functionId`  
啟動 JIT 編譯之記憶體中函式的識別碼。

[in] `fIsSafeToBlock` 
 `true`若要指出封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回，`false`表示封鎖不會影響執行時間的作業。  

[in] `pILHeader`方法的 IL 標頭的第一個位元組指標。

[in] `cbILHeader`IL 標頭中的位元組數目。

## <a name="remarks"></a>備註  

每當動態方法是 JIT 編譯時，就會觸發此回呼。 這包括各種 IL stub 和 LCG 方法。 其目標是要為 profiler 寫入器提供足夠的資訊，以向使用者識別已編譯的方法。

> [!NOTE]
> `functionId`值無法用來解析其元資料標記，因為動態方法沒有中繼資料。

`pILHeader`只有在回呼期間，指標才有效。

## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)
