---
title: ICorProfilerCallback4::ReJITError 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 46312aaf530e69f0e6a90e35515f1373d01b4340
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730236"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError 方法

通知分析工具，及時 (JIT) 編譯器在重新編譯程式中發生錯誤。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>參數  

 `moduleID`  
 在 `ModuleID` 嘗試進行重新編譯失敗的。  
  
 `methodId`  
 在 `MethodDef` 嘗試重新編譯失敗之方法的。  
  
 `functionId`  
 在正在重新編譯或標示為重新編譯的函式實例。 此值可能是因為 `NULL` 每個方法的失敗，而不是每個具現化的基礎 (例如，如果分析工具指定了不正確元資料標記，讓方法重新編譯) 。  
  
 `hrStatus`  
 在表示失敗本質的 HRESULT。 請參閱狀態 HRESULT 一節以取得值的清單。  
  
## <a name="return-value"></a>傳回值  

 忽略此回呼傳回的值。  
  
## <a name="status-hresults"></a>狀態 HRESULT  
  
|狀態陣列 HRESULT|描述|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID`或 `methodDef` token 為 `NULL` 。|  
|CORPROF_E_DATAINCOMPLETE|這個模組未完全載入，或正在進行卸載。|  
|CORPROF_E_MODULE_IS_DYNAMIC|指定的模組是以動態方式產生的 (例如，藉由 `Reflection.Emit`) ，因此不支援此方法。|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|方法會具現化為可回收元件中，因此無法重新編譯。 請注意，在非反映內容中定義的類型和函式 (例如， `List<MyCollectibleStruct>`) 可以具現化為可回收元件。|  
|E_OUTOFMEMORY|當您嘗試將指定的方法標示為 JIT 重新編譯時，CLR 已用盡記憶體。|  
|其他|作業系統會傳回在 CLR 的控制項外發生的失敗。 例如，如果變更記憶體頁面存取保護的系統呼叫失敗，則會顯示作業系統錯誤。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
