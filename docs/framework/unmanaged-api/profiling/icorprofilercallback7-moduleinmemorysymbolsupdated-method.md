---
title: ICorProfilerCallback7：： ModuleInMemorySymbolsUpdated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: f6dd10d196ffd3a653584e1bc8d1a5643850bc33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136600"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7：： ModuleInMemorySymbolsUpdated 方法
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 每當與記憶體中模組相關聯的符號資料流程更新時，就會通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>參數  
 [輸入] `moduleId`  
 已更新其符號資料流程之記憶體中模組的識別碼。  
  
## <a name="remarks"></a>備註  
 呼叫[ICorProfilerCallback5：： SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法時，會設定[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制此回呼。  
  
> [!NOTE]
> 目前不會針對透過 <xref:System.Reflection.Emit> Api 隱含建立或修改的符號引發此事件。  
  
 即使在呼叫 managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> 方法的其中一個多載時，會包含 `rawSymbolStore` 引數來指定元件的符號，執行時間仍可能不會實際建立符號資料與模組的關聯，直到已發生[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。 此事件可讓您更好的機會收集這類別模組的符號。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ModuleLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
