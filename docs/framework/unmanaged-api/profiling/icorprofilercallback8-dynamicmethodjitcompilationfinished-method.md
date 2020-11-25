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
ms.openlocfilehash: 6354667e754da42692cc0de2dc5330c56f951aa1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725439"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法

[在 .NET Framework 4.7 和更新版本中支援]  
  
每當動態方法的 JIT 編譯完成時，通知 profiler。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>參數  

[in] `functionId`  
已啟動 JIT 編譯之記憶體內建函式的識別碼。

[in] `hrStatus` 指出 JIT 編譯是否成功的值。

[in] `fIsSafeToBlock` 
 `true`若要指出封鎖可能會導致執行時間等候呼叫執行緒從此回呼傳回;`false`表示封鎖不會影響執行時間的操作。  

## <a name="remarks"></a>備註  

每當動態方法的 JIT 編譯完成時，就會觸發此回呼。 這包括各種 IL 存根和 LCG 方法。 其目標是要為 profiler 寫入器提供足夠的資訊，以識別已編譯的方法給使用者。

> [!NOTE]
> `functionId` 因為動態方法沒有中繼資料，所以無法使用值解析其元資料標記。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)
