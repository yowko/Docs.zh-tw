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
ms.openlocfilehash: c7e53816c2f571fe6ff68b517ed827459a0f1562
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499086"
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
 [in] `moduleId`  
 已更新其符號資料流程之記憶體中模組的識別碼。  
  
## <a name="remarks"></a>備註  
 呼叫[ICorProfilerCallback5：： SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法時，會設定[COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制此回呼。  
  
> [!NOTE]
> 目前不會針對透過 api 隱含建立或修改的符號引發此事件 <xref:System.Reflection.Emit> 。  
  
 即使在呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 包含引數以指定元件符號的 managed 方法的其中一個多載時 `rawSymbolStore` ，執行時間還是不會實際將符號資料與模組建立關聯，直到發生[ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼為止。 此事件可讓您更好的機會收集這類別模組的符號。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ModuleLoadFinished 方法](icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 方法](icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 介面](icorprofilercallback7-interface.md)
