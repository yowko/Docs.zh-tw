---
title: ICorProfilerCallback8 介面
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136444"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 介面
[在 .NET Framework 4.7 和更新版本中支援]  

 [ICorProfilerCallback7](icorprofilercallback7-interface.md)的子類別，提供通用語言執行時間使用的回呼方法，以通知分析工具已開始和完成動態方法的 JIT 編譯。 
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|通知分析工具已啟動動態方法的 JIT 編譯。|  
|[DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|通知分析工具已完成動態方法的 JIT 編譯。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback9 介面](icorprofilercallback9-interface.md)
