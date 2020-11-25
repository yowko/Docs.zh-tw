---
title: ICorProfilerCallback4::GetReJITParameters 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: 2cee763674da7472ca48355e7eaba3b7dfb7adbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730301"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters 方法

允許程式碼分析工具為新重新編譯的方法主體設定替代程式碼產生旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>參數  

 `moduleID`  
 在包含 CLR 需要 JIT 重新編譯參數之方法的模組。  
  
 `methodId`  
 在 `MethodDef` CLR 需要 JIT 重新編譯參數之方法的。  
  
 `pFunctionControl`  
 在 [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) 介面的指標，分析工具可以使用它來提供重新編譯之方法的 JIT 重新編譯資訊。  
  
## <a name="remarks"></a>備註  

 CLR 會發出回呼，讓分析工具 `GetReJITParameters` 可以指定參數來重新編譯指定的方法。 `GetReJITParameters`回呼只會針對每個函式發出一次; profiler 提供的參數會套用至該函式的所有實例。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
- [JITCompilationStarted 方法](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted 方法](icorprofilercallback4-rejitcompilationstarted-method.md)
