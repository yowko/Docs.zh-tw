---
title: 'ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated 方法'
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
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916204"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated 方法
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 每當與記憶體中模組相關聯的符號資料流程更新時, 就會通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>參數  
 [in] `moduleId`  
 已更新其符號資料流程之記憶體中模組的識別碼。  
  
## <a name="remarks"></a>備註  
 呼叫[ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法時, 會設定[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制此回呼。  
  
> [!NOTE]
> 目前不會針對透過<xref:System.Reflection.Emit> api 隱含建立或修改的符號引發此事件。  
  
 即使在呼叫<xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> `rawSymbolStore`包含引數以指定元件符號的 managed 方法的其中一個多載時, 執行時間還是不會實際將符號資料與模組產生關聯直到發生[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼為止。 此事件可讓您更好的機會收集這類別模組的符號。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ModuleLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
