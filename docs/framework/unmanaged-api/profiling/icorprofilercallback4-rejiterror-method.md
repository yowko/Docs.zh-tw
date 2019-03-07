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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0cd68f5a15bbd8942f0dc889ecb74b7fde00d30
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502316"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError 方法
通知分析工具在 just-in-time (JIT) 編譯器發生重新編譯程序中的錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>參數  
 `moduleID`  
 [in]`ModuleID`中進行重新編譯失敗的嘗試。  
  
 `methodId`  
 [in]`MethodDef`上失敗的重新編譯嘗試的方法。  
  
 `functionId`  
 [in]正在重新編譯或標示為重新編譯函式執行個體。 這個值可以是`NULL`如果發生失敗而不是以每個具現化的方式以每個方法為基礎 （例如，如果分析工具指定重新編譯方法無效的中繼資料語彙基元）。  
  
 `hrStatus`  
 [in]HRESULT，表示失敗的本質。 請參閱值的狀態 HRESULT 區段的清單。  
  
## <a name="return-value"></a>傳回值  
 忽略此回呼傳回的值。  
  
## <a name="status-hresults"></a>狀態 HRESULT  
  
|狀態陣列 HRESULT|描述|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID`或是`methodDef`語彙基元是`NULL`。|  
|CORPROF_E_DATAINCOMPLETE|這個模組未完全載入，或正在進行卸載。|  
|CORPROF_E_MODULE_IS_DYNAMIC|動態產生指定的模組 (例如，藉由`Reflection.Emit`)，並因此不支援這個方法。|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|方法可回收組件中，具現化，因此無法重新編譯。 請注意，型別和非反映內容中定義的函式 (例如`List<MyCollectibleStruct>`) 可以具現化成可回收組件。|  
|E_OUTOFMEMORY|CLR 會嘗試將標記指定的方法進行 JIT 重新編譯時已用盡記憶體。|  
|其他|作業系統會傳回在 CLR 的控制項外發生的失敗。 例如，如果要變更之存取保護的記憶體分頁的系統呼叫失敗，作業系統會顯示錯誤。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
