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
ms.openlocfilehash: 22a133d02bb69026190428905379323362943d40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732381"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 介面

[在 .NET Framework 4.7 和更新版本中支援]  

 [ICorProfilerCallback7](icorprofilercallback7-interface.md)的子類別，提供 common language runtime 用來通知分析工具已啟動和完成 JIT 編譯動態方法的回呼方法。
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|通知分析工具已啟動動態方法的 JIT 編譯。|  
|[DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|通知分析工具已完成動態方法的 JIT 編譯。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback9 介面](icorprofilercallback9-interface.md)
