---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12414064bf0651eab443951bde2a50dcff7b2291
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992091"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7::ModuleInMemorySymbolsUpdated 方法
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 每次更新記憶體中模組相關聯的符號資料流時，請通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>參數  
 [in] `moduleId`  
 已更新其符號資料流的記憶體中模組的識別碼。  
  
## <a name="remarks"></a>備註  
 此回呼由設定控制[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標時呼叫[ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。  
  
> [!NOTE]
>  以隱含方式建立或修改透過符號目前不引發這個事件<xref:System.Reflection.Emit>Api。  
  
 即使當符號中所提供提前呼叫其中一個受管理的多載<xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType>方法，其中包含`rawSymbolStore`引數來指定組件，執行階段的符號可能未實際關聯的符號資料模組直到之後[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼發生。 這個事件會提供更新版本的機會，來收集這類模組的符號。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ModuleLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
