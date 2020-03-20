---
title: ICorProfiler回撥9：:Dynamic方法未載入方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177029"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a>ICorProfiler回撥9：:Dynamic方法未載入方法
[在 .NET 框架 4.7.2 和更高版本中支援]  
  
每當收集動態方法並隨後卸載時，通知探測器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a>參數  
[in] `functionId`  
已垃圾回收和卸載的記憶體中函數的識別碼。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfiler回檔8.動態方法JIT編譯啟動方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfiler回檔8.動態方法JIT編譯完成方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback9 介面](icorprofilercallback9-interface.md)
- [COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS](cor-prf-high-monitor-enumeration.md)
