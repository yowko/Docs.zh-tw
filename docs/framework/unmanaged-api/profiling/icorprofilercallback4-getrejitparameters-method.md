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
ms.openlocfilehash: 858d65783515a89a434cf719ef9d5a999643094c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865307"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters 方法
可讓程式碼分析工具針對新重新編譯的方法主體，設定替代的程式碼產生旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>參數  
 `moduleID`  
 在包含 CLR 需要 JIT 重新編譯參數之方法的模組。  
  
 `methodId`  
 在CLR 需要 JIT 重新編譯參數之方法的 `MethodDef`。  
  
 `pFunctionControl`  
 在[ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md)介面的指標，分析工具可用來為重新編譯的方法提供 JIT 重新編譯資訊。  
  
## <a name="remarks"></a>備註  
 CLR 會發出 `GetReJITParameters` 回呼，讓分析工具可以指定參數來重新編譯指定的方法。 每個函式只會發出一次 `GetReJITParameters` 回呼;profiler 所提供的參數會套用至該函式的所有實例。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
- [JITCompilationStarted 方法](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted 方法](icorprofilercallback4-rejitcompilationstarted-method.md)
